## Prosper I.T. Code Summary

#### User Stories
Full Stack 
  * [Search Productions](#search-productions) 
  * [Home Page](#home-page)
  * [Dynamic Archive](#dynamic-archive)

Front-end
  * [Responsive Rental Requests](#responsive-rental-requests)
  * [Archive Search Bar](#archive-search-bar)
  * [Subscriber Area](#subscriber-area)
  * [Reapply CSS](#reapply-css)

Back-end
  * [Update Photo Class](#update-photo-class)
  * [Photo Return Icon](#photo-return-icon)


## Introduction

During the last two weeks I spent at The Tech Academy, I worked with a team developing an interactive website for managing the content and productions for a theater/acting company. This content management service was designed in mind for users who aren't technically saavy, so ease-of-use was a priority. The site has just been started, so there were many improvements that could be made. Our team was comprised of people of varying skill-levels and the user-stories available reflected that. I saw this as an opportunity to challenge myself and continue building upon what I've already learned. I tackled several stories, with three of them being "difficult." I found that the more challenging stories were much more enjoyable and rewarding. I've listed the different stories I worked on below, they are categorized and in order of most difficult to least difficult.


## Full Stack Stories

#### Search Productions
I was tasked with creating a search and filter feature that would allow the user to filter Productions on the Productions Index page. 
This involved querying the database to create, filter, and sort a list that I would be able to use on the front-end. The search field
simultaneously searches different fields, and the user can select any combination of fields to further filter the data. I was challenged to improvise, adapt, and overcome obstacles that this story presented to me. I relied heavily on constant debugging to ensure that the feature was working as intended and to recognize problems as they came up.

[User Story](Projects/Productions-Search-Feature/User-Story.png?raw=true)

[UI-One](Projects/Productions-Search-Feature/Search-Feature-1.png?raw=true) [UI-Two](Projects/Productions-Search-Feature/Search-Feature-2.png?raw=true) [UI-Three](Projects/Productions-Search-Feature/Search-Feature-3.png?raw=true)

[Controller](Projects/Productions-Search-Feature/controller.md)

[View](Projects/Productions-Search-Feature/View.md)

[Styling](Projects/Productions-Search-Feature/css.md)

#### Home Page
After completing two "difficult" stories, my Instructor gave me the opportunity to redesign the home page of the website. This involved mostly front-end design, but also included a little bit of back-end work. It was the end of my second sprint, but I was up to the challenge and I looked forward to providing the project with a clean and aesthetic home page. While there was no user story posted as it was already the end of my final sprint, my instructor recognized my abilities and we discussed what the homepage should look like.

[UI-One](Projects/Home-Page/Home-Page-1.png?raw=true) [UI-Two](Projects/Home-Page/Home-Page-2.png?raw=true) [UI-Three](Projects/Home-Page/Home-Page-3.png?raw=true)

[View](Projects/Home-Page/view.md)

[Controller](Projects/Home-Page/controller.md)

[Styling](Projects/Home-Page/css.md)

#### Dynamic Archive
When I started the project, the Archive of past productions contained static content. I took on the task of making that page dyanmically generate content. We needed to query the database and display past productions by season (year range). The content needed to be displayed concisely.

[User Story](Projects/Dynamic-Archive/User-Story.png?raw=true)

[UI-One](Projects/Dynamic-Archive/Dynamic-Archive-1.png?raw=true) [UI-Two](Projects/Dynamic-Archive/Dynamic-Archive-2.png?raw=true) [UI-Three](Projects/Dynamic-Archive/Dynamic-Archive-3.png?raw=true)

[View](Projects/Dynamic-Archive/view.md)

[Controller](Projects/Dynamic-Archive/controller.md)

[Styling](Projects/Dynamic-Archive/css.md)


## Front-end Stories

#### Responsive Rental Requests
This was a challenging user interface story to transform the Rental Request Index page of the website. We needed a responsive design, that was both professional and stylish. This was my first "difficult" story during the live project, and I wanted to create something that not only look good for the end user, but was easy to use and understand as well.

[User Story](Projects/Responsive-Rental-Request/User-Story.png?raw=true)

[UI-One](Projects/Responsive-Rental-Request/Responsive-Rental-Request-1.png?raw=true) [UI-Two](Projects/Responsive-Rental-Request/Responsive-Rental-Request-2.png?raw=true) [UI-Three](Projects/Responsive-Rental-Request/Responsive-Rental-Request-3.png?raw=true)

[View](Projects/Responsive-Rental-Request/view.md)

[Styling](Projects/Responsive-Rental-Request/css.md)

#### Archive Search Bar
The original search form used on the Archive page was multi-line, and wasn't suitable for wide-screen view. I redesigned the search form so that it was more aesthetic, but retained it's original format for mobile-view. I also took the time to add in a little bit of css to display all images at the same size without distorting the quality.

[User Story](Projects/Archive-Search-Bar/User-Story.png?raw=true)

[UI-One](Projects/Archive-Search-Bar/Archive-Search-Bar-1.png?raw=true) [UI-Two](Projects/Archive-Search-Bar/Archive-Search-Bar-2.png?raw=true)

[View](Projects/Archive-Search-Bar/view.md)

[Styling](Projects/Archive-Search-Bar/css.md)

#### Subscriber Area
Details on the subscriber dashboard were misaligned, and the page would not react responsively. I realigned the subscriber details, and adjusted the styling so that the details would stack when not being viewed on a wide-screen.

[User Story](Projects/Subscriber-Area/User-Story.png?raw=true)

[UI-One](Projects/Subscriber-Area/Subscriber-Area-1.png?raw=true) [UI-Two](Projects/Subscriber-Area/Subscriber-Area-2.png?raw=true) [UI-Two](Projects/Subscriber-Area/Subscriber-Area-3.png?raw=true)

[View](Projects/Subscriber-Area/view.md)

[Styling](Projects/Subscriber-Area/css.md)

#### Reapply CSS
One of the previous members of our team had added a class to our site.css file that modified the behavior of bootstrap classes. This shouldn't have been done, and I was tasked with correcting the mistake and reapplying the new css class to the views that had been affected.

[User Story](Projects/Reapply-CSS/User-Story.png?raw=true)

[View](Projects/Reapply-CSS/view.md)

[Styling](Projects/Reapply-CSS/css.md)



## Back-end Stories

#### Update Photo Class
Our original class did not automatically calculate an images height and width, and this needed to be inputted by the user when a new instance was created. I change the create method of the contoller to automatically calculate the height and width of an image. This story also required some light front-end work updating CSS classes, and apply them to the the different Photo views.

[User Story](Projects/Update-Photo-Class/User-Story.png?raw=true)

[Controller](Projects/Update-Photo-Class/controller.md)

[Styling](Projects/Update-Photo-Class/css.md)

#### Photo Return Icon
Initially our DisplayPhoto() method did not check to see if the photo id existed or was valid. I updated that method to check if the photo id existed, and if it did not an image was returned to the user to display that an image is unavaible. This involved finding an image, modifying it with Gimp to suit our needs, converting it into a byte array, and then returning it to the view.

[User Story](Projects/Photo-Return-Icon/User-Story.png?raw=true)

[Controller](Projects/Photo-Return-Icon/controller.md)


