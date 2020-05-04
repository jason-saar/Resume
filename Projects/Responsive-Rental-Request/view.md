	@model IEnumerable<TheatreCMS.Models.RentalRequest>

	@{
		ViewBag.Title = "Rental Request";
	}
	<div class="container-fluid">
		<div class="h2 m-4">Rental Requests</div>
		<table class=" table-responsive-stack" id="rentalRequests">
			<thead class="bg-light">
				<tr class="text-black">
					<th>
						@Html.DisplayNameFor(model => model.ContactPerson)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.Company)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.StartTime)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.EndTime)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.ProjectInfo)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.Requests)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.RentalCode)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.Accepted)
					</th>
					<th>
						@Html.DisplayNameFor(model => model.ContractSigned)
					</th>
					<th class="bg-black border-0" id="rental-request-nav-th">
						<div class="hidden-placeholder"></div>
					</th>
				</tr>
			</thead>

			<tbody>
				@{
					string rentalStartDate;
					string rentalStartTime;
					string rentalEndDate;
					string rentalEndTime;

					foreach (var item in Model)
					{
						rentalStartDate = item.StartTime.ToString("dd-MM-yy");
						rentalStartTime = item.StartTime.ToString("HH:mm tt");
						rentalEndDate = item.EndTime.ToString("dd-MM-yy");
						rentalEndTime = item.EndTime.ToString("HH:mm tt");

						<tr class="text-light rental-request-rows">
							<td>
								@Html.DisplayFor(modelItem => item.ContactPerson)
							</td>
							<td>
								@Html.DisplayFor(modelItem => item.Company)
							</td>
							<td>
								<div class="rental-request-date">@rentalStartDate</div>
								<div class="rental-request-date">@rentalStartTime</div>
							</td>
							<td>
								<div class="rental-request-date">@rentalEndDate</div>
								<div class="rental-request-date">@rentalEndTime</div>
							</td>
							<td id="rental-request-project-info">
								<button type="button" class="project-info-popover fa fa-search" title="Project Info" data-trigger="hover" data-toggle="project-info" data-content="@Html.DisplayFor(modelItem => item.ProjectInfo)"></button>
							</td>
							<td>
								@Html.DisplayFor(modelItem => item.Requests)
							</td>
							<td>
								@Html.DisplayFor(modelItem => item.RentalCode)
							</td>
							<td>
								@if (item.Accepted)
								{
									<span class="text-success">Yes</span>
								}
								else
								{
									<span class="text-danger">No</span>
								}
								@*Html.DisplayFor(modelItem => item.Accepted)*@
							</td>
							<td>
								@if (item.ContractSigned)
								{
									<span class="text-success">Yes</span>
								}
								else
								{
									<span class="text-danger">No</span>
								}
								@*Html.DisplayFor(modelItem => item.ContractSigned)*@
							</td>
							<td id="rental-request-nav-container">
								<div class="rental-request-nav">@Html.ActionLink("Edit", "Edit", new { id = item.RentalRequestId }, new { @class = "badge badge-pill badge-danger text-black" }) </div>
								<div class="rental-request-nav">@Html.ActionLink("Details", "Details", new { id = item.RentalRequestId }, new { @class = "badge badge-pill badge-danger text-black" }) </div>
								<div class="rental-request-nav">@Html.ActionLink("Delete", "Delete", new { id = item.RentalRequestId }, new { @class = "badge badge-pill badge-danger text-black" }) </div>
							</td>
						</tr>
					}
				}

			</tbody>
		</table>
	</div>

	<!-- Handles stacking when resolution < 992-->
	@Scripts.Render("~/bundles/jquery")
	<script src="@Url.Content("~/Scripts/umd/popper.min.js")"></script>
	<script>
		$(document).ready(function () {

			 $('[data-toggle="project-info"]').popover();

			$('.table-responsive-stack').find("th").each(function (i) {
				if (!$(this).is('#rental-request-nav-th') ) {
					$('.table-responsive-stack td:nth-child(' + (i + 1) + ')').prepend('<div class="table-responsive-stack-thead">' + $(this).text() + '</div><br>');
				}
				$('.table-responsive-stack-thead').hide();
			});


			$('.table-responsive-stack').each(function () {
				var thCount = $(this).find("th").length;
				var rowGrow = 100 / thCount + '%';
				$(this).find("th, td").css('flex-basis', rowGrow);
			});

			function flexTable() {
				if (window.matchMedia('(max-width: 992px)').matches) {

					$(".table-responsive-stack").each(function (i) {
						$(this).find(".table-responsive-stack-thead").show();
						$(this).find('thead').hide();
					});

					$(".project-info-popover").each(function (i) {
						$(this).replaceWith('<span class="mobile-project-info">' + $(this).attr("data-content") + '</span>');
					});



				} else {

					$(".table-responsive-stack").each(function (i) {
						$(this).find(".table-responsive-stack-thead").hide();
						$(this).find('thead').show();
					});

					$(".mobile-project-info").each(function (i) {
						$(this).replaceWith('<button type="button" class="project-info-popover fa fa-search" title="Project Info" data-trigger="hover" data-toggle="project-info" data-content="' + $(this).text() + '"></button>');
					});
					$('[data-toggle="project-info"]').popover();
				}
			}

			flexTable();

			window.onresize = function (event) {
				
				flexTable();
			};

		});
	</script>