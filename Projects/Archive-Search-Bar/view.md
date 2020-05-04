	<!--Seach Bar/ Actors,parts, and productions dropdown-->
	<div class="archive-search-container">
		@using (Html.BeginForm("Archive", "Home", FormMethod.Post))
		{
			<div class="archive-input-container">
				<select id="SearchByCategory" name="SearchByCategory">
					<option class="search-dropdown">Search by Category</option>
					<option class="search-dropdown option" value="ArchiveCastMember">Cast Member</option>
					<option class="search-dropdown option" value="ArchiveProduction">Production</option>
					<option class="search-dropdown option" value="ArchivePart">Part</option>
				</select>
				@Html.TextBox("ArchiveSearchField", "", new { placeholder = "Search" })
				<button class="search-btn btn btn-lg btn-circle fa fa-search" type="submit" value="search"></button>
			</div>
		}
	</div>

	@Scripts.Render("~/bundles/jquery")
	<script>
		$(document).ready(function () {
			@* Swap search button for mobile view, if > 900px use fontawesome magnifying glass, if < 900 use standard "Search" button" *@
			function changeSearchBtn() {
				if (window.matchMedia('(max-width: 899px)').matches) { @* matchMedia syncs with CSS media query *@
					$(".search-btn").each(function (i) {
						$(this).replaceWith('<button class="search-btn btn btn-outline-primary mobile-search-btn" type="submit" value="search">' + 'Search' + '</button>');
					});
				} else {
					$(".mobile-search-btn").each(function (i) {
						$(this).replaceWith('<button class="search-btn btn btn-lg btn-circle fa fa-search color" type="submit" value="search"></button>');
					});
				}
			}

			@* Call changeSearchBtn() when page is loaded *@
			changeSearchBtn(); 

			@* If window is resized, call changeSearchBtn()*@
			window.onresize = function (event) {
				changeSearchBtn();
			};

		});
	</script>