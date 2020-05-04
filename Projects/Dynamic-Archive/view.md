	<!--Past Productions-->
	@{ 
		var currentSettings = AdminSettingsReader.CurrentSettings();            // Grabs AdminSettings JSON 
		int currentSeason = currentSettings.current_season;                     // Initialize currentSeason and set using "current_season" from JSON
		int firstYear = 1997;
		int secondYear = 1998;
		Dictionary<int, string> seasonYears = new Dictionary<int, string>();    // Create Dictionary containing Seasons and their years    
		for (int i = 1; i <= currentSeason; i++)
		{
			seasonYears.Add(i, firstYear.ToString() + " - " + secondYear.ToString());
			firstYear++;
			secondYear++;
		}
	}
	<div class="container">
		<div class="h4">Past Productions</div> 
		<div class="accordian" id="pastProductions">
			<!-- Begin for loop to populate years-->
			@for (int i = currentSeason; i >= 1; i--)
			{
				string currentHeading = "heading" + i.ToString(); 
				string currentBody = "season" + i.ToString();
				<div class="card bg-black">
					<!-- header -->
					<div class="card-header text-center" id="@currentHeading"> 
						<h2 class="mb-0">
							<button class="btn btn-block text-white" type="button" data-toggle="collapse" data-target="@('#' + currentBody)" aria-expanded="false" aria-controls="@currentBody">
								@seasonYears[i]
							</button>
						</h2>
					</div>
					<!-- Collapsable body -->
					<div id="@currentBody" class="collapse" aria-labelledby="@currentHeading" data-parent="#pastProductions">
						<div class="card-body">
							<div class="card-deck bg-black">
								<!-- Iterate through Productions and populate cards-->
								@foreach (var item in Model)
								{
									if (item.Season == i)
									{
										<div class="card bg-black">
											@if (item.DefaultPhoto != null)
											{
												<div class="embed-responsive-4by3">
													<img src="@Url.Action("DisplayPhoto", "Photo", new { id = item.DefaultPhoto.PhotoId })" class="card-img-top arch-card-img bg-black">
												</div>
											}
											else
											{
												<div class="embed-responsive-4by3">
													<img src="~/Content/Images/Unavailable.png" class="card-img-top arch-card-img bg-black">
												</div>
											}
											<div class="card-body">
												<h5 class="card-title">
													@Html.DisplayFor(modelItem => item.Title)
												</h5>
												<p class="card-text">
													@Html.DisplayFor(modelItem => item.Description)
												</p>
												<a href="@Url.Action("Details", "Productions", new { id = item.ProductionId })" class="stretched-link"></a> 
											</div>
										</div>
									}
								}
							</div>
						</div>
					</div>
				</div>
			}
		</div>
	</div>