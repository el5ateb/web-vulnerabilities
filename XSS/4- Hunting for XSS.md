

## Step 1: Look for Input Opportunities 
> look for opportunities to submit user input to the target site. If you’re attempting stored XSS, search for places where input gets stored by the server and later displayed to the user, including comment fields, user profiles, and blog posts. The types of user input that are most often reflected back to the user are forms, search boxes, and name and username fields in sign-ups.

> Don’t limit yourself to text input fields, either. Sometimes drop-down menus or numeric fields can allow you to perform XSS, because even if you can’t enter your payload on your browser, your proxy might let you insert it directly into the request.

> for reflected and DOM XSS, 
> look for user input in URL parameters, fragments, or pathnames that get displayed to the user.
	A good way to do this is to insert a custom string into each URL parameter and check whether it shows up in the returned page. Make this string specific enough that you’ll be sure your input caused it if you see it rendered.

> Insert your custom string into every user-input opportunity you can find. Then, when you view the page in the browser, search the page’s source code for it. This should give you an idea of which user input fields appear in the resulting web page.

## Step 2: Insert Payloads :
> **More Than a script Tag**
> Inserting script tags into victim web pages isn’t the only way to get your scripts executed in victim browsers. There are a few other tricks. First, you can change the values of attributes in HTML tags. Some HTML attributes allow you to specify script to run if certain conditions are met
-  **example**, onload event 

