## Cookies, Forms quiz

⭐️ Question 1 (1 point)
Saved
Question 1 options:
(true/false) If you have the value of a user's login cookie, you can use that to simulate their authenticated session elsewhere, consequently "stealing" their logged in session.

True!!!!

explanation: The answer is True because if you have the value of a user's login cookie, it can potentially be used to simulate their authenticated session elsewhere, effectively "stealing" their logged-in session.

⭐️ Question 2 (1 point)
Saved
Which Set-Cookie option produces a cookie that only be sent to the server over HTTPS using SSL?
Question 2 options:

HttpOnly

Secure >>> this

SameSite

expires

no such option exists

Question 3 (1 point)
Saved
Question 3 options:
If a form at the url, http://foo.bar/my-form, has the following markup:

<form method="POST">
<!-- other markup follows-->

Fill in the blanks for the resulting http request after the form's submit button is pressed (method in all caps, path is case sensitive):

POST /my-form HTTP/1.1

⭐️ Question 4 (1 point)
Saved
Question 4 options:
(true/false) The Cookie header can only contain a single name value pair.

False.

⭐️ Question 5 (1 point)
Saved
What is the most appropriate status code for for an http response given back as the result of a POST form submission where refreshing the page does not cause the form to be resubmitted
:303 See Other

⭐️ Question 6 (1 point)
Question 6 options:
(true/false) When the path and domain options (also called directives) for the Set-Cookie response header are set, the browser only sends those cookies back through the Cookie request header when the browser is making a request to the specified domain and path.
: False!!!

explanation:
Set-Cookie: myCookie=myValue; path=/example; domain=mydomain.com

Question 8 (1 point)
Saved
Which Set-Cookie option (also called directive) prevents client-side JavaScript (that is, JavaScript run in the browser) from accessing cookies?
: HttpOnly

⭐️ Question 9 (1 point)
Question 9 options:
The form element's [ action ]
(all lowercase) attribute determines the path of the http request generated by pressing the form's submit button.

Question 10 (1 point)
Saved
Question 10 options:
Given the following http request:

POST /foo HTTP/1.1
Content-Type: application/x-www-form-urlencoded

bar=baz&qux=corge

Fill in the blanks for the form markup that generated this request on form submission (not all tags are shown)

<form method="POST" action="/foo">
  <input type="text" name="bar" value="baz">
  <input type="text" name="qux" value="corge">
  <input type="submit">
</form>

⭐️ Question 11 (1 point)
Saved
Question 11 options:
Given the following form:

<form method="GET" action="/foo">
<input type="text" name="bar">
<input type="text" name="qux">
<input type="submit">
</form>

If the form is submitted with baz typed into the first field and corge typed into the second field, the resulting query string is:

bar=baz&qux=corge

⭐️ Question 12 (1 point)
Saved
If a form's method is GET, then the data in the form is transmitted to the server:

Question 12 options:

In the body of the HTTP request as JSON

In the body of the HTTP request as name and value pairs

Appended to the path of an HTTP request >>> this

Through a cookie

Within the HTTP request headers

⭐️ Question 1 (1 point)
Question 1 options:
(true/false) When a browser has valid cookies for a domain, it will send the information in those cookies as the value of the Cookie header when making all future requests to that domain until that cookie is deleted (deleted manually by the user, deleted because of expiration, etc.)
]
True!!!

⭐️ Question 2 (1 point)
Loading JavaScript from another domain that reads cookies from the domain that the current page is being viewed on is called:
Question 2 options:

XSS >> Cross-site scripting. this

Session Fixation

CSRF

Third Party Tracking Cookies >> wrong

Replay Attack

Question 7 (1 point)
Saved
An http GET request with a query string can only be generated when pressing the submit button on a form with method="GET" and named input fields.
Question 7 options:

False!
