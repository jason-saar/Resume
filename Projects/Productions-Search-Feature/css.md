    /* Start Produtions Index Search */

    /* Gradient coloring for active search button*/
    .active-search-button {
        background: -moz-radial-gradient(center, ellipse cover, rgba(219,26,17,0.55) 0%, rgba(219,26,17,0.55) 1%, rgba(0,0,0,1) 100%);
        background: -webkit-radial-gradient(center, ellipse cover, rgba(219,26,17,0.55) 0%,rgba(219,26,17,0.55) 1%,rgba(0,0,0,1) 100%);
        background: radial-gradient(ellipse at center, rgba(219,26,17,0.55) 0%,rgba(219,26,17,0.55) 1%,rgba(0,0,0,1) 100%);
        filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#8cdb1a11', endColorstr='#000000',GradientType=1 );
    }

    .search-container {
        float: right;
        padding: 25px 40px 0px 0px;
        width: 300px;
    }

    .search-select {
        font-size: 15px !important;
        height: 30px !important;
        padding: 0 0 0 4px !important;
        margin: 5px 0 5px 0 !important;
    }

    .search-text {
        font-size: 15px !important;
        height: 30px !important;
        padding: 0 0 0 8px !important;
        margin: 5px 0 5px 0 !important;
    }

    .search-button {
        float: right;
        background-color: var(--dark-color);
    }

    .search-icon {
        color: var(--light-color);
        border: none;
    }

    /* Styling for wide screen */
    @media screen and (min-width: 769px) {
        .search-container {
            position: fixed;
            z-index: 9;
            top: 160px;
            right: 40px;
            padding: 0px;
        }

        .search-button {
            position: relative;
            background-color: var(--dark-color);
        }

        .search-form {
            background-color: rgba(0, 0, 0, 0.7);
            position: relative;
            display: inline-block;
            padding: 10px 10px 0px 10px;
            margin-top: 5px;
            border-radius: 5px;
            height: 340px;
        }
    }

    /* Styling for lower resolutions*/
    @media screen and (max-width: 768px) {
        .search-container {
            display: block;
            float: none;
            width: 100% !important;
            position: relative;
            bottom: 82px;

        }

        .search-form {
            display: inline-block;
            padding: 40px 0px 0px 40px;
        }

        .search-text, .search-select {
            display: inline-block !important;
            width: 49% !important;
        }
    } 

    @media screen and (max-width: 450px) {
        .prod-index-create { 
            display: block;
            position: relative;
            bottom: 20px;
        }

        .search-container {
            bottom: 138px;
            left: 1px;
        }

        .search-form {
            position: relative;
            top: 35px;
        }
    }
    /* End Productions Index Search*/
