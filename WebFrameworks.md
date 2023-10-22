## Web frameworks quiz

⭐️ Question 1 (1 point)
Saved
Question 1 options:
If an express application contains the following call to getg:

app.get('/foo', (req, res) => res.send('bar'));

Assuming that the application is running on port 3000 and that the browser has never accessed this path previously, what http response status code would be received by the browser if the browser requests http://localhost:3000/foo ...?
answer: 200

⭐️ Question 2 (1 point)
Saved
Question 2 options:
What is the argument that would be used in a call to app.use so that the path of every request is searched for within the directory, foo, in the file system that express app is running from... and if found, returns that file as the body of an http response?

The answer contains no spaces. If quoting a string, use single quotes. It would be the argument that goes into:

app.use( **\_**)

express.static('foo')
explanation: 'every request is searched for within the directory, in the file system that express app is running from... and if found, returns that file as the body of an http response'. => express.static('directory name')

Question 3 (1 point)
Saved
Question 3 options:
If you would like the following markup to appear in all pages created by using res.render to contain:

<header>Welcome</header>

You would place that markup in the following file in the views directory (assuming you are using the hbs module):

home(.hbs)

Question 4 (1 point)
Saved
Question 4 options:
Finish the following code so that the express application responds to POST requests for /foo

app.\_\_\_\_('/foo', (req, res) => {res.send.('foo')});

post

Question 5 (1 point)
Saved
Question 5 options:
Assuming the module, hbs, is installed, if res.render is called with "foo" as the first argument, then the file (blank 1, file name) must exist in the (blank 2, directory name within expression project) folder.
foo.hbs

views

Saved
Within a handlebars template file, relational operators, such as > and <, cannot be used.

⭐️ Question 7 options:
True
False

True!!!!!!

Question 8 (1 point)
Saved
Question 8 options:
Assuming that the following context object is passed into a call to res.render:

has a key called points
the value is a list of objects
each object, in turn has two keys, x and y
Using the shorthand version of handlerbars code that does not require this when iterating over a list of objects, complete the code in the handlerbars template to display the values of the x and y properties of every object in points within an html div element:

{ {#each **\_**} }
{ {**\_**} }, { {**\_**} } { {/each} }

points, x, y

⭐️ Question 9 (1 point)
Saved
Question 9 options:
Assuming the code in views/foo.hbs contains this code (assume no space between curly braces, as Brightspace is not rendering consecutive curly braces correctly):

<h1>{ {bar} }</h1>

What would the second argument to res.render have to be so that the word hello appears between the tags? Omit quotes for property names if quoting is not necessary. Use single quotes for strings. If creating objects, no spaces except for after : or , ... for example {k1: 'v1', k2: 'v2'}.

{bar: 'hello'}

Question 10 (1 point)
Saved
Given the following template, foo.hbs (assume no space between curly braces, as Brightspace is not rendering consecutive curly braces correctly):

<h1>{ {header} }</h1>

And the following call to render:

const greeting = 'hello';
res.render('foo', {header: greeting});

Assuming that all the setup for handlebars is present, and the layout file is correctly set up, the resulting page should contain the following text (choose error if there's an error):

hello

Question 12 (1 point)
Saved
The names req and res must be given to the parameters of the function passed in as the second argument to app.get.

Question 12 options:
True
False

False!!!!

Question 1 (1 point)
Question 1 options:
What should the type be of the second argument passed in to a call to app.get?
function (callback function)

Question 2 (1 point)
Saved
Given the following template, foo.hbs (assume no space between curly braces, as Brightspace is not rendering consecutive curly braces correctly):

<h1>{ {greeting} }</h1>

And the following call to render:

const greeting = 'hello';
res.render('foo', greeting);

Assuming that all the setup for handlebars is present, and the handlebars layout file is correctly set up, the resulting page should contain the following text (choose error if there's an error):

Question 2 options:
error.
