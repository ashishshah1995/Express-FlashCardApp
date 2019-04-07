Flashcard application with cookie to store user name

To launch app
In terminal window: node app.js (or, to use nodemon to autorestart app when files are edited: nodemon app.js)
in browser goto localhost:3000
Typical flow
In a browser open localhost:3000
If a user name cookie does not exist, a form is displayed to enter it.
After the user name is submitted a "welcome" message is displayed with button to start flashcards.
A random question is displayed. The page has buttons to display the answer, show a hint and display another random card.
The card also has a button to clear the user name and return to name input form.
Packages used
Express framework
Pug to render templates
body-parser middleware
cookie-parser middleware
Routes (i.e. localhost:3000/...)
All routes use response.render and Pug template to generate pages.

Templates utilize a shared template (e.g extends layout) which in turn includes template pieces (e.g. include includes/header.pug).

/ (root)
Displays user name in a welcome box if the username cookie is set, otherwise it redirects to /hello. Page has a Begin button to display a flashcard.

Next to the Welcome box is a button to clear the user name that submits a post to /goodbye.

/hello, get request
Displays a form to submit a user name if there is no username cookie, otherwise redirects to root route. The welcome box displays the message "hello, student". The name entered is submitted with a post request.

/hello, post request
The user name is extracted from the request and is saved as a cookie. The client is then redirected to root route.

/goodbye
Defined for only post requests. Clears the user name cookie and redirects to /hello.

/cards/#?side=type
Display the card at index # from the cards array. Type is either the value question or answer. The question/answer and hint are passed to the Pug template using response.locals properties. If the side displayed is the question the HTML includes a JS script which adds a Show Hint button to display the hint when clicked.

Both sides have buttons to flip to the other side and display another random card.

The welcome box described above for the root and /hello routes is displayed. Displaying a card is not dependent on a saved user name.

If the side query parameter is neither question or answer the question side is displayed.

/cards
Redirects to the question side of random card.

/about
Text about the app.

error handling
All errors should be captured and redirected to an error page which displays the error status, a "desktop" graphic and the stack dump in a scrolling window.

If the card index in the URL is invalid a 404 error is displayed.

Project file structure
/data
the flat file containing the questions in json format.

/js-express-basics-flashcard-assets
the designer html files and images.

/node_modules
packages install by npm.

/public
static assets: images, client-side JS file, CSS files.

/routes
JS files that explicitly define routes (e.g. /cards, /hello).

cards.js and index.js define multiple routes
about.js defines one route (using different syntax than cards.js, index.js)
/views
Pug templates called by route functions, extended shared templates and included partial templates.

app.js
the main application JS file, which is launched by Node.

requires body-parser package
requires cookie-parser package
declares pug as the template renderer.
declares files containing routes for explicitly defined routes.
declares error handling middleware



Flashcard study app, as taught by Treehouse in the "Express Basics" course (https://teamtreehouse.com/library/express-basics-2)

Using Express, Mongoose, Pug and DB on MongoDB Atlas.

To run the app locally:

Download all files

Use "npm install" to install dependencies

Use "node app.js" to start the app on http://localhost:3000/

Notes:

Most of the code was done during the course "Express Basics" course on Treehouse.

Here are some of the features that I added, that were not covered in the course:

All the flashcards are saved to a MongoDB on MongoDB Atlas

Multiple Flashcards topic and the ability to switch between them

Ability to add or delete flashcards topics (the entire /edit-cards page)

Keeping track of which cards have been "already seen" using cookies

Randomizing the order in which cards appear


A flashcard app containing videogame trivia with a user authentication signup & login.

This project creates a user authentication system with Express, MongoDB/Mongoose and Pug. A user can sign up with a username and password, log in, and log out of the app. Once logged in, a flashcard game containing videogame trivia is accessible to the user.

I combined and expanded upon what I learned from two tutorial series on Team Treehouse (Express Basics & User Authentication with Express and Mongo) to code this. It is heavily commented so that other Treehouse students can easily understand the code and use it along with these tutorials as additional practice.




Flashcard App
A practice app built during Unit 6 of the Team Treehouse Full Stack JavaScript Techdegree. A user can input their name, then start a flashcard game with JavaScript-related questions and answers.

Technologies used
Express
Node
Pug
JavaScript
CSS

Future improvements
Full UX redesign
Flashcard database with categories
Add users/authentication
