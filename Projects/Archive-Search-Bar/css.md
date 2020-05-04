	/* Archive Current Productions */
	#current-productions {
		padding: 0px 20px;
	}

	/* Resize Archive Current Productions Image */
	#current-productions .current-production-img {
		height: 30vw;
		object-fit: cover;
	}

	/* Archive Current Productions Image Responsive Resizing */
	@media only screen and (max-width: 575px) {
		#current-productions .current-production-img {
			height: 60vw;
			object-fit: cover;
		}
	}

	/* Start Archive Search Bar */

	@media only screen and (min-width: 900px){
	   
		/* Search container for centering Input Container*/
		.archive-search-container {
			display: flex;
			justify-content: center;
			align-items: center;
		}

		/* Input Container: Input field, Category Dropdown, Search button*/
		.archive-input-container {
			margin: 0 auto;
			width: 850px;
			position: relative;
		}

		/* Archive Search Text*/
		.archive-input-container input[type="text"]{
			width: 600px;
			height: 50px;
			padding: 12.5px 20px 12.5px 20px;
			margin: 8px 0px 8px 200px;
			background-color: var(--light-color);
			font-size: 20px;
			border: none;
			outline: none;
			border-right: 0px;
			border-radius: 0px;
		}

		/* Arhive Search Category Dropdown */
		.archive-input-container #SearchByCategory {
			width:200px;
			height: 50px;
			margin: 0px;
			padding: 12.5px 20px 12.5px 20px;
			background-color: #007bff;
			color: var(--light-color);
			text-align: center;
			position: absolute;
			float: left;
			top: 8px;
			border: none;
			border-radius: 4px 0px 0px 4px;
			outline: none;
		}

		/* Archive Search Button*/
		.archive-input-container .btn {
			height: 50px;
			width: 50px;
			border: none;
			padding: 12.5px 0px;
			background-color: var(--light-color);
			color: var(--dark-color);
			text-align: center;
			position: absolute;
			border-radius: 0px 4px 4px 0px;
			margin: 8px 0px 8px 0px;
		}
		
		.archive-input-container .btn:focus {
			box-shadow: none !important;
		}
		
		.archive-input-container .btn:hover {
			background-color: var(--light-color);
		}

		.archive-input-container option {
			background-color: var(--light-color);
			color: var(--dark-color);
		}

	}

	@media only screen and (max-width: 900px) {
		.archive-input-container {
			padding: 0px 20px;
		}
	}

	/* End Archive Search Bar*/