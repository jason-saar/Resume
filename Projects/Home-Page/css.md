	@font-face {
		font-family: 'BebasNeue';
		src: url('../webfonts/BebasNeue-Regular.woff2') format('woff2');
		font-weight: normal;
		font-style: normal;
	}

	/* Start Homepage */

	.home-body {
		position: relative;
		-webkit-box-flex: 1;
		-ms-flex: 1 0 auto;
		flex: 1 0 auto;
	}


	#home-main {
		display: block;
		font-size: 100%;
		font-family: BebasNeue;
		font-weight: 400;
		line-height: 1.5;
		overflow-x: hidden;
	}


	.home-block, .home-inner {
		margin: 0;
		padding: 0;
		border: none;
		outline: 0;
		vertical-align: baseline;
	}

	.home-inner {
		position: relative;
		overflow: hidden;
	}

	.home-img, .home-mobile-img {
		padding-bottom: 56.25%;
	}

	@media only screen and (max-width: 48em) {
		.home-img, .home-mobile-img {
			position: relative;
			display: none;
		}
	}

	.home-img>div, .home-mobile-img>div {
		position: absolute;
		background-size: cover;
		background-position: 50%;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}

	@media only screen and (min-width: 48.0625em) {
		.home-img {
			padding-bottom: 100vh;
		}
	}

	.home-mobile-img {
		padding-bottom: 61.25%;
		display: none;
	}

	@media only screen and (max-width: 48em){
		.home-mobile-img {
			display: block;
		}
	}

	.home-tint-overlay {
		position: absolute;
		top: 0px;
		left: 0px;
		right: 0px;
		bottom: 0px;
		z-index: 10;
		background: -webkit-gradient(linear,left top,left bottom,color-stop(53.92%,rgba(35,31,32,0)),color-stop(72.5%,rgba(35,31,32,.6)));
		background: linear-gradient(rgba(35,31,32,0) 53.92%,rgba(35,31,32,.6) 72.5%);
		-webkit-transition: inherit;
		transition: opacity ease-in-out 3s;
	}

	@media only screen and (max-width: 48em){
		.home-tint-overlay {
			display: none;
		}
	}

	.home-content {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		display: -webkit-box;
		display: -ms-flexbox;
		display: flex;
		-webkit-box-pack: center;
		-ms-flex-pack: center;
		justify-content: center;
		text-align: center;
		color: #fff;
		margin-bottom: 2.5rem;
		z-index: 100;
		width: 100%;
		max-width: 92rem;
		margin-left: auto;
		margin-right: auto;
		padding-left: 1rem;
		padding-right: 1rem;
	}

	@media only screen and (min-width: 48.0625em) {
		.home-content {
			max-width: 94rem;
			padding-left: 2rem;
			padding-right: 2rem;
		}
	}

	@media only screen and (min-width: 64.125em) {
		.home-content {
			max-width: 99.75rem;
			padding-left: 4.875rem;
			padding-right: 4.875rem;
		}
	}

	@media (max-width: 48em) {
		.home-content {
			position: relative;
			text-align: left;
			-webkit-box-pack: start;
			-ms-flex-pack: start;
			justify-content: flex-start;
			margin: .5rem 0 1rem;
			z-index: 0;
			opacity: 1;
		}
	}

	.home-content-inner {
		width: 100%;
	}


	.home-tag-line {
		margin-bottom: -2.5rem;
		font-size: 1.25rem;
	}

	@media only screen and (max-width: 80em) {
		.home-tag-line {
			margin-bottom: -1.75rem;
		}
	}

	@media only screen and (max-width: 64.0625em) {
		.home-tag-line {
			margin-bottom: -1.25rem;
		}
	}

	@media only screen and (max-width: 48em) {
		.home-tag-line {
			display: none;
		}
	}

	.home-content-inner h2 {
		display: block;
		line-height: 1;
		font-weight: 400;
		background:transparent;
		margin: 0;
	}

	.home-title {
		font-size: 13rem;
		font-weight: 400;
		color: var(--light-color);
		text-shadow: var(--dark-color) 0px 0px 10px;
	}

	@media only screen and (max-width: 80em) {
		.home-title {
			font-size: 10rem;
		}
	}

	@media only screen and (max-width: 64.0625em) {
		.home-title {
			font-size: 7.5rem;
		}
	}

	@media only screen and (max-width: 48em) {
		.home-title {
			font-size: 2.5rem;
			color: var(--light-color);
			margin-bottom: 0 !important;
		}
	}


	@media only screen and (max-width: 48em) {
		.home-title+.home-btn {
			margin-top: .625rem;
		}
	}

	.home-content-inner .home-date {
		font-family: Arial, sans-serif;
	}

	.home-date {
		font-size: 1.5rem;
		margin: -.25rem 0 1.25rem;
	}

	@media only screen and (max-width: 48em) {
		.home-date {
			color: var(--light-color);
			font-size: .875rem;
			margin: 0 0 .25rem;
		}
	}

	.home-content-inner .btn-primary {
		display: inline-block;
		font-weight: 700;
		margin-bottom: 1rem;
		padding: .75rem 1rem;
		font-family: Arial;
		text-decoration: none;
		text-transform: uppercase;
		text-align: center;
		min-width: 7.5rem;
		border-radius: 0;
		font-size: 1rem;
		line-height:1.5;
		background-color: var(--main-bg-color);
		color: var(--light-color);
		border: 1px solid var(--main-bg-color);

	}

	.home-content-inner .btn-primary:focus {
		background-color: rgba(0, 0, 0, .6);
		color: var(--main-bg-color);
		border: 1px solid var(--main-bg-color);
		box-shadow: none;
	}


	.home-content-inner .btn-primary:active:hover {
		background-color: rgba(0, 0, 0, .6);
		color: var(--main-bg-color);
		border: 1px solid var(--main-bg-color);
		box-shadow: none !important;
	}

	.home-content-inner .btn-primary:hover {
		background-color: rgba(219, 26, 17, .7);
	}


	@media only screen and (max-width: 48em) {
		.home-content-inner .btn-primary {
			font-size: .875rem;
			line-height: 1.7143;
			color: var(--dark-color);
		}
	}

	#home-nav{
		position: fixed;
		top: 50%;
		right: 2.5rem;
		color: #fff;
		z-index: 100;
		list-style-type: none;
		padding: 0;
		margin: 0;
	}

	@media only screen and (max-width:48em){
		#home-nav{
			display:none;
		}
	}

	#home-nav a{
		display: block;
		border-bottom: none;
		margin-bottom: .5rem;
		background-color: #fff;
		width: .75rem;
		height: .75rem;
		border: 1px solid var(--dark-color);
		border-radius: 50%;
		cursor: pointer;
	}

	#home-nav a:hover{
		background-color: var(--secondary-color);
	}

	#home-nav li.active a{
		background-color: var(--main-bg-color);
	}

	#home-nav a:focus {
		box-shadow: 0px 2px 0 0 var(--dark-color) !important;
		outline: 0;
	}






	/* End Homepage */

