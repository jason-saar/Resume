public ActionResult Index(string searchString, string season, string month, string day, string showtime, string runtime, bool? worldPremiere, bool? isSearching)
{
	var productions = from p in db.Productions
					  select p;
	var showTimes = from p in db.Productions
					select new ShowtimeListVM
					{
						ShowTimeEve = p.ShowtimeEve,
						ShowTimeMat = p.ShowtimeMat
					};

	var runTimes = from p in db.Productions
				   select p.Runtime;

	//Pass Variables to ViewBag 
	ViewBag.SeasonYears = SeasonYears();            //Dictionary of Season Years <int, string>
	ViewBag.ShowTimes = ShowtimeSort(showTimes);    //Sort showtimes ascending
	ViewBag.RunTimes = RuntimeSort(runTimes);       //Sort runtimes ascending
	ViewBag.CurrentFilter = searchString;
	ViewBag.CurrentSeason = season;
	ViewBag.CurrentMonth = month;
	ViewBag.CurrentDay = day;
	ViewBag.CurrentShowtime = showtime;
	ViewBag.CurrentRuntime = runtime;
	ViewBag.WorldPremiere = worldPremiere;

	if (!String.IsNullOrEmpty(month) && month != "any" && !String.IsNullOrEmpty(day) && day != "any") // If day && month HasValue // If day && month HasValue
	{
		var monthInt32 = Int32.Parse(month);
		monthInt32 += 1;                        // Add one to month for db comparison, value passed from view is 0-11 with 0:Jan 1:Feb etc...
		var dayInt32 = Int32.Parse(day);
		if (!IsValidDay(dayInt32, monthInt32))  // Call day validation check
		{
			ViewBag.DayEx = "Invalid Date";
			isSearching = true;
			ViewBag.IsSearching = isSearching;
			return View(productions.ToList());
		}
		else
		{
			productions = productions.Where(p => p.OpeningDay.Month <= monthInt32 && p.ClosingDay.Month >= monthInt32);
			productions = productions.Where(p => p.OpeningDay.Day <= dayInt32 && p.ClosingDay.Day >= dayInt32);
			isSearching = true;

		}
	}
	else
	{
		if (!String.IsNullOrEmpty(month) && month != "any")
		{
			var monthInt32 = Int32.Parse(month);
			monthInt32 += 1;
			productions = productions.Where(p => p.OpeningDay.Month <= monthInt32 && p.ClosingDay.Month >= monthInt32);
			isSearching = true;
		}
		if (!String.IsNullOrEmpty(day) && day != "any")
		{
			var dayInt32 = Int32.Parse(day);
			productions = productions.Where(p => p.OpeningDay.Day <= dayInt32 && p.ClosingDay.Day >= dayInt32);
			isSearching = true;
		}
	}
	//Comapare values passed from view to values in productions
	if (!String.IsNullOrEmpty(searchString))
	{
		productions = productions.Where(p => p.Title.Contains(searchString) || p.Playwright.Contains(searchString) || p.Description.Contains(searchString));
		isSearching = true;
	}
	if (!String.IsNullOrEmpty(season) && season != "any")
	{
		var seasonInt32 = Int32.Parse(season);
		productions = productions.Where(p => p.Season == seasonInt32);
		isSearching = true;
	}
	if (!String.IsNullOrEmpty(showtime) && showtime != "any")
	{
		var dt = DateTime.Parse(showtime);
		var time = dt.TimeOfDay;
		productions = productions.Where(p => DbFunctions.CreateTime(((DateTime)p.ShowtimeEve).Hour, ((DateTime)p.ShowtimeEve).Minute, ((DateTime)p.ShowtimeEve).Second) == time || DbFunctions.CreateTime(((DateTime)p.ShowtimeMat).Hour, ((DateTime)p.ShowtimeMat).Minute, ((DateTime)p.ShowtimeMat).Second) == time);
		isSearching = true;
	}
	if (!String.IsNullOrEmpty(runtime) && runtime != "any")
	{
		var runtimeInt32 = Int32.Parse(runtime);
		productions = productions.Where(p => p.Runtime == runtimeInt32);
		isSearching = true;
	}
	if (worldPremiere == true)
	{
		productions = productions.Where(p => p.IsWorldPremiere == true);
		isSearching = true;
	}
	
	if(isSearching.HasValue && isSearching == true) //Pass isSearching boolean to ViewBag
	{
		ViewBag.IsSearching = isSearching;
	}
	else if (season == "any" || month == "any" || day == "any" || showtime == "any" || runtime == "any")
	{
		ViewBag.IsSearching = true;
	}
	else
	{
		ViewBag.IsSearching = false;
	}

	ViewBag.Results = productions.Count();  //Total search results

	return View(productions.ToList());
}


private Dictionary<int, string> SeasonYears()
{
	var currentSettings = AdminSettingsReader.CurrentSettings();
	var currentSeason = currentSettings.current_season;
	int latestYear = DateTime.Now.Year;
	int currentMonth = DateTime.Now.Month;
	if (currentMonth >= 6) //Seasons last from June - June, if True current season must display latest year as current year + 1
	{
		latestYear++;
	}

	Dictionary<int, string> seasonYears = new Dictionary<int, string>(); //Create dictionary file from current season in json file
	for (int i = currentSeason; i > 0; i--)
	{
		string year = latestYear.ToString();
		string previousYear = (latestYear - 1).ToString();
		if (i == currentSeason)
		{
			seasonYears.Add(i, "Current ('" + previousYear.Substring(year.Length - 2) + " ~ '" + year.Substring(previousYear.Length - 2) + ")");
		}
		else
		{
			seasonYears.Add(i, i + " ('" + previousYear.Substring(year.Length - 2) + " ~ '" + year.Substring(previousYear.Length - 2) + ")");
		}
		latestYear--;
	}
	return seasonYears;
}


public bool IsValidDay(int day, int month)      //Date Validator
{
	var year = DateTime.Now.Year;
	bool b = false;
	var currentSeason = SeasonYears().Count();
	
	for (int i = currentSeason; i >= 0; i--)        //Using currentseason, loop through theatre years, if dd/mm exists in any of those years, bool is valid.
	{
		if (day <= DateTime.DaysInMonth(year, month))
		{
			b = true;
		}
		year--;
	} 
	return b;
}


public List<string> ShowtimeSort(IEnumerable<ShowtimeListVM> showtimeListVMs)   //Sort Method
{
	var unorderedShowtimeList = new List<DateTime>();
	foreach (var item in showtimeListVMs.ToList())      //loop through list of ShowtimeListVM containing values of ShowTimeEve/Mat
	{
		if (item.ShowTimeEve.HasValue)
		{
			unorderedShowtimeList.Add((DateTime)item.ShowTimeEve);
		}
		if (item.ShowTimeMat.HasValue)
		{
			unorderedShowtimeList.Add((DateTime)item.ShowTimeMat);
		}
	}
	var orderedShowtimeList = unorderedShowtimeList.OrderBy(x => x.TimeOfDay).ToList();     //Sort list ascending

	var showTimes = new List<String>();
	foreach (var item in orderedShowtimeList)       //Convert each value to string in format "hh:mm am/pm"
	{
		if (!showTimes.Contains(item.ToShortTimeString()))          //Check if showTimes list contains showtime already
		{
			showTimes.Add(item.ToShortTimeString());
		}
	}
	return showTimes;
}


public List<int> RuntimeSort(IEnumerable<int> runTimesList) //Sort method
{
	var runTimes = new List<int>(); //Sort runtimes in ascending order
	foreach (var item in runTimesList.ToList())
	{
		if (!runTimes.Contains(item)){          //Check if runTimes list contains runtime already
			runTimes.Add(item);
		}
	}
	runTimes.Sort();
	return runTimes;
}
}


public static class IntegerExtensions   //Integer extensions class and method
{
	public static string DisplayWithSuffix(this int num)
	{
		string number = num.ToString();
		if (number.EndsWith("11")) return number + "th";
		if (number.EndsWith("12")) return number + "th";
		if (number.EndsWith("13")) return number + "th";
		if (number.EndsWith("1")) return number + "st";
		if (number.EndsWith("2")) return number + "nd";
		if (number.EndsWith("3")) return number + "rd";
		return number + "th";
	}
}