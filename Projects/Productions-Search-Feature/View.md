    @model IEnumerable<TheatreCMS.Models.Production>
    @using TheatreCMS.Controllers
    @using TheatreCMS.Helpers
    @using System.Globalization
    @using TheatreCMS.ViewModels

    @{
        ViewBag.Title = "Productions";

        //Assign ViewBag seasonyears, showtimes, and runtimes to variables
        Dictionary<int, string> seasonYears = (ViewBag.SeasonYears as Dictionary<int, string>);
        var showTimes = (ViewBag.ShowTimes as IEnumerable<string>).ToList();
        var runTimes = (ViewBag.RunTimes as IEnumerable<int>).ToList();
    }

    <h2 class="prod-index-header">Productions</h2>

    @if (User.IsInRole("Admin"))
    {
        <p class="prod-index-create">
            @Html.ActionLink("Create New", "Create")
        </p>
    }

    <div class="search-container">
        <button class="search-button" type="button">
            <div class="fa fa-search search-icon " />
        </button>
        <div class="search-form">
            @using (Html.BeginForm("Index", "Productions", FormMethod.Get))
            {
                <p>
                    @Html.TextBox("SearchString", ViewBag.CurrentFilter as string, new { @class = "search-text", placeholder = "Search..." })
                    <select class="search-select" id="season" name="season">
                        <!-- Check if searching, if searching hide default selected placeholder option-->
                        @if (String.IsNullOrEmpty(ViewBag.CurrentSeason))
                        {
                            <option selected disabled hidden>Season</option>  @* Hide if ViewBag.CurrentSeason HasValue *@
                        }
                        <option value="any">Any Season</option>
                        @for (int i = seasonYears.Count(); i > 0; i--)
                        {

                            {
                                if (!String.IsNullOrEmpty(ViewBag.CurrentSeason))
                                {
                                    <!-- Check if string is numerical -->
                                    if (Int32.TryParse((string)ViewBag.CurrentSeason, out _))
                                    {
                                        if (i == Int32.Parse(ViewBag.CurrentSeason))
                                        {
                                            <!-- Prevents duplicate option -->
                                            <option selected value="@i">@seasonYears[i]</option>
                                        }
                                        else
                                        {
                                            <option value="@i">@seasonYears[i]</option>
                                        }
                                    }
                                    else
                                    {
                                        <option value="@i">@seasonYears[i]</option>
                                    }
                                }
                                else
                                {
                                    <option value="@i">@seasonYears[i]</option>
                                }
                            }
                        }
                    </select>
                    <select class="search-select" id="month" name="month">
                        @if (String.IsNullOrEmpty(ViewBag.CurrentMonth))
                        {
                            <option selected disabled hidden>Month</option>
                        }
                        <option value="any">Any Month</option>
                        @for (int i = 0; i < 12; i++)
                        {
                            if (!String.IsNullOrEmpty(ViewBag.CurrentMonth))
                            {
                                if (Int32.TryParse((string)ViewBag.CurrentMonth, out _))
                                {
                                    if (i == Int32.Parse(ViewBag.CurrentMonth))
                                    {
                                        <!-- DateTimeFormatInfo.InvariantInfo.MonthNames converts int to full month string -->
                                        <option selected value="@i">@DateTimeFormatInfo.InvariantInfo.MonthNames[i]</option>
                                    }
                                    else
                                    {
                                        <option value="@i">@DateTimeFormatInfo.InvariantInfo.MonthNames[i]</option>
                                    }
                                }
                                else
                                {
                                    <option value="@i">@DateTimeFormatInfo.InvariantInfo.MonthNames[i]</option>
                                }
                            }
                            else
                            {
                                <option value="@i">@DateTimeFormatInfo.InvariantInfo.MonthNames[i]</option>
                            }
                        }
                    </select>
                    <select class="search-select" id="day" name="day">
                        @if (String.IsNullOrEmpty(ViewBag.CurrentDay))
                        {
                            <option selected disabled hidden>Day</option>
                        }
                        <option value="any">Any Day</option>
                        @for (int i = 1; i <= 31; i++)
                        {
                            if (!String.IsNullOrEmpty(ViewBag.CurrentDay))
                            {
                                if (Int32.TryParse((string)ViewBag.CurrentDay, out _))
                                {
                                    if (i == Int32.Parse((string)ViewBag.CurrentDay))
                                    {
                                        <!-- Controller includes integer extension method to give numbers suffixes-->
                                        <option selected value="@i">@i.DisplayWithSuffix()</option>
                                    }
                                    else
                                    {
                                        <option value="@i">@i.DisplayWithSuffix()</option>
                                    }
                                }
                                else
                                {
                                    <option value="@i">@i.DisplayWithSuffix()</option>
                                }
                            }
                            else
                            {
                                <option value="@i">@i.DisplayWithSuffix()</option>
                            }
                        }
                    </select>
                    @if (!String.IsNullOrEmpty(ViewBag.DayEx))
                    {
                        @Html.ValidationMessage("day", ViewBag.DayEx as string, new { @class = "text-danger" }) <!-- Day validation error-->
                    }
                    <select class="search-select" id="showtime" name="showtime">
                        @if (String.IsNullOrEmpty(ViewBag.CurrentShowtime))
                        {
                            <option selected disabled hidden>Showtime</option>
                        }
                        <option value="any">Any Showtime</option>
                        @foreach (var item in showTimes)
                        {
                            if (!String.IsNullOrEmpty(ViewBag.CurrentShowtime))
                            {
                                if (DateTime.TryParse((string)ViewBag.CurrentShowtime, out _))
                                {
                                    if (item == (string)ViewBag.CurrentShowtime)
                                    {
                                        <option selected value="@item">@item</option>
                                    }
                                    else
                                    {
                                        <option value="@item">@item</option>
                                    }
                                } else
                                {
                                    <option value="@item">@item</option>
                                }
                            }
                            else
                            {
                                <option value="@item">@item</option>
                            }
                        }
                    </select>
                    <select class="search-select" id="runtime" name="runtime">
                        @if (String.IsNullOrEmpty(ViewBag.CurrentRuntime))
                        {
                            <option selected disabled hidden>Runtime</option>
                        }
                        <option value="any">Any Runtime</option>
                        @foreach (var runTime in runTimes)
                        {
                            if (!String.IsNullOrEmpty(ViewBag.CurrentRuntime))
                            {
                                if (Int32.TryParse((string)ViewBag.CurrentRuntime, out _))
                                {
                                    if (runTime == (Int32.Parse(ViewBag.CurrentRuntime)))
                                    {
                                        <option selected value="@runTime">@runTime</option>
                                    }
                                    else
                                    {
                                        <option value="@runTime">@runTime</option>
                                    }
                                }
                                else
                                {
                                    <option value="@runTime">@runTime</option>
                                }
                            }
                            else
                            {
                                <option value="@runTime">@runTime</option>
                            }
                        }
                    </select>
                    World Premiere
                    @if (ViewBag.WorldPremiere ?? false)
                    {
                        <input type="checkbox" id="worldpremiere" name="worldpremiere" value="true" checked />
                    }
                    else
                    {
                        <input type="checkbox" id="worldpremiere" name="worldpremiere" value="true" />
                    }
                    <input id="search-submit" class="btn btn-outline-primary  btn-sm" type="submit" value="Search" />
                    @if ((ViewBag.IsSearching ?? false) && String.IsNullOrEmpty(ViewBag.DayEx)) //Only display if isSearching == true and no day validation error
                    {
                        <span>@ViewBag.Results Results.&nbsp;&nbsp;@Html.ActionLink("Reset search", "Index")</span>
                    }
                </p>
            }
        </div>
    </div>


    @Scripts.Render("~/bundles/jquery")

    <!-- Toggle for search button, if currently searching show search form else hide search form  -->
    <!-- Scroll function for search form -->
    <script>
        $(document).ready(function () {
            $(document).scroll(function () {
                if ($(window).scrollTop() > 0 && window.matchMedia('(min-width: 769px)').matches) {
                    $(".search-container").css({ top: '64px' });
                }
                if ($(window).scrollTop() === 0) {
                    $('.search-container').removeAttr('style');
                }

            });

            var currentlySearching = "@((ViewBag.IsSearching).ToString())"

            if (currentlySearching != "False") {
                $('.search-form').show();
                $('.search-button').addClass('active-search-button');
            } else {
                $('.search-form').hide();
            }

            $('.search-button').click(function () {
                $('.search-form').slideToggle();
                if ($('.search-button').hasClass('active-search-button')) {
                    $('.search-button').removeClass('active-search-button');
                } else {
                    $('.search-button').addClass('active-search-button');
                }
            });

        });
    </script>
