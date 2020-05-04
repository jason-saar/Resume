	#rentalRequests {
		table-layout: fixed;
		border: none;
		width: 100%;
		border-color: var(--light-color);
	}

	.project-info-popover, .project-info-popover:active, .project-info-popover:visited, .project-info-popover:focus {
		text-decoration: none;
	}

	.table-responsive-stack tr {
		display: -webkit-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-orient: horizontal;
		-webkit-box-direction: normal;
		-ms-flex-direction: row;
		flex-direction: row;
		text-align: center;
		border: none;
	}


	.table-responsive-stack td,
	.table-responsive-stack th {
		width: 10%;
		display: block;
		/*      
	   flex-grow | flex-shrink | flex-basis   */
		-ms-flex: 1 1 auto;
		flex: 1 1 auto;
		border-color: var(--light-color);
		text-align: center;
		padding: .15rem;
	}



	.table-responsive-stack .table-responsive-stack-thead {
		font-weight: bold;
		font-size: 1.0625em;
		display: inline-flex;
		color: #efeee0;
		position: relative;
		top: 3px;
	}

	.rental-request-date {
		position: relative;
		bottom: 9px;
	}

	.project-info-popover {
		background-color: var(--dark-color);
		border-color: var(--light-color);
		border: none;
		vertical-align: middle !important;
		color: var(--light-color);
	}

	.project-info-popover:focus, .project-info-popover:active {
		outline: none;
	}

	.rental-request-rows td {
		border-bottom: 1px solid var(--light-color) !important;
		margin-top: 10px;
		padding-bottom: 10px;
		flex-basis:;
	}

	#rental-request-nav-th {
		flex-basis: 5% !important;
		margin-left: 5px;
	}

	.rental-request-rows #rental-request-nav-container {
		border: none !important;
		flex-basis: 5% !important;
	}

	.rental-request-nav {
		margin: 2px 0 2px 0;
	}

	.rental-request-nav a {
		display: inline-block;
		width: 55px;
	}


	@media screen and (max-width: 992px) {
		.table-responsive-stack tr {
			-webkit-box-orient: vertical;
			-webkit-box-direction: normal;
			-ms-flex-direction: column;
			flex-direction: column;
			border: none;
			border-color: var(--light-color);
			display: block;
			text-align: left;
			margin: 0px 0 50px 0;
			padding-top: 20px;
			padding-bottom: 20px;
			border: 1px solid var(--light-color);
			margin: 0 -20px 0 -20px 0;
		}

		.rental-request-rows {
			margin-top: 10px;
			padding-bottom: 10px;
		}

		.rental-request-rows td {
			border: none !important;
			margin: auto;
			padding: 0;
		}
		
		.table-responsive-stack td {
			float: left\9;
			width: 100%;
			border: none;
			padding: 0;
		}

		.table-responsive-stack br {
			display: normal;
		}

		#rental-request-nav-container {
			padding-top: 5px;
			width: 205px;
			display: flex;
			align-content: center;
			justify-content: center;
		}

		.rental-request-nav a {
			margin: 0px;
		}

		.rental-request-nav {
			display: inline-flex;
			padding: 2.5px;
		}

		.mobile-project-info {
			display: inline-block;
			width: 90%;
		}

		.rental-request-date {
			display: inline-flex;
			position: static;
		}

	}