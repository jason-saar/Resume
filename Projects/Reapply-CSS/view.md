	<div class="card-deck bg-black">
		<div class="card bg-black">
			<img src="~/Content/Images/Stupid-ghost.png" class="card-img-top bg-black" alt="Ghost">
			<div class="card-body">
				<h5 class="card-title">Stupid Ghost</h5>
				<p class="card-text">A clumsy ghost that stubs his toe everynight, spooking the new tenants.</p>
			</div>
			<div class="card-footer">
				<button type="button" class="btn btn-block btn-primary" disabled>Get Tickets</button>
			</div>
		</div>
		<div class="card bg-black">
			<img src="~/Content/Images/Midas-gold.jpg" class="card-img-top bg-black" alt="Midas">
			<div class="card-body">
				<h5 class="card-title">Everything You Touch</h5>
				<p class="card-text">A cursed man that ruins everything he touches.</p>
			</div>
			<div class="card-footer">
				<button type="button" class="btn btn-block btn-primary" disabled>Get Tickets</button>
			</div>
		</div>
		<div class="card bg-black">
			<img src="~/Content/Images/venice.jpg" class="card-img-top bg-black" alt="Merchant">
			<div class="card-body">
				<h5 class="card-title">Merchant of Venice</h5>
				<p class="card-text">A Merchant in Venice struggles to pay off his student loans.</p>
			</div>
			<div class="card-footer">
				<button type="button" class="btn btn-block btn-primary" disabled>Get Tickets</button>
			</div>
		</div>
	</div>
	
	
	
	<div class="row productionphotos-cardborder">
		<div class="col-sm-6">
			<div class="card bg-black">
				<div class="card-body">
					<h5>
						Photo @Html.DisplayNameFor(model => model.Title)
					</h5>
					<p class="card-text">
						@Html.DisplayFor(model => model.Title)
					</p>
					<h5>
						@Html.DisplayNameFor(model => model.Description)
					</h5>
					<p class="card-text">
						@Html.DisplayFor(model => model.Description)
					</p>
				</div>
			</div>
		</div>
		<div class="col-sm-6">
			<div class="card bg-black">
				<div class="card-body">
					<h5>
						Production @Html.DisplayNameFor(model => model.Production.Title)
					</h5>
					<p class="card-text">
						@Html.DisplayFor(model => model.Production.Title)
					</p>
					<h5>
						@Html.DisplayNameFor(model => model.Production.Season)
					</h5>
					<p class="card-text">
						@Html.DisplayFor(model => model.Production.Season)
					</p>
				</div>
			</div>
		</div>
	</div
	
	
  <div class="card col-md-6 col-xl-4 bg-black" id="production-info-parent">
  @Html.DisplayFor(modelItem => item.DefaultPhoto)   @*Displays the default photo or Unavailable.jpg*@
  @{
	if (item.DefaultPhoto != null)
	{
	
		<a href="@Url.Action("Details", "Productions", new { id = item.ProductionId })">
		  <img class="card-img-top production-index-img mt-5 bg-black" src="@Url.Action("DisplayPhoto", "Photo", new { id = item.DefaultPhoto.PhotoId })" alt="Card image cap">  
		</a>
	}
	else
	{
		<a href="@Url.Action("Details", "Productions", new { id = item.ProductionId })">
		  <img class="card-img-top production-index-img mt-5 bg-black" src="~/Content/Images/Unavailable.png" alt="Card image cap">
		</a>
	}
	}