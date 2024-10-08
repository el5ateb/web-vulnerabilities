- #### prevent XSS 
	 - Applications should implement two controls: 
		 robust input validation and contextual output escaping and encoding. 
	 - Applications should never insert user-submitted data directly into an HTML,
	   Instead, the server should validate that user-submitted input doesn’t contain dangerous characters that might influence the way browsers interpret the information on the page. 
	**example**, user input containing the string script is a good indicator that the input contains an XSS payload. In this case, the server could block the request, or sanitize it by removing or escaping special characters before further processing.
---
- #### Encoding special characters 
	- they are interpreted literally instead of as a special character by the programs or machines that process the characters. 
	- Applications will need to encode the user input based on where it will be embedded. 
		- if the user input is inserted into script tags, it needs to be encoded in JavaScript format. The same goes for input inserted into HTML, XML, JSON, and CSS files.
		- In the context of our example, the application needs to encode special characters into a format used by HTML documents. 
		- For example, the left and right angle brackets can be encoded into HTML characters &lt and &gt. To prevent XSS, the application should escape characters that have special
		- meaning in HTML, such as the & character, the angle brackets < and >, single and double quotes, and the forward-slash character. Escaping ensures that browsers won’t misinterpret these characters as code to execute. This is what most modern applications do to prevent XSS.
----
- #### prevention DOM-based XSS
	1. avoid code that rewrites the HTML document based on user input
	2. implement client-side input validation before it is inserted into the DOM.
	3. et the Http Only flag on sensitive cookies that your site uses
	4. implement the Content-Security-Policy HTTP response header
------
For more information about preventing XSS attacks, visit the OWASP XSS prevention cheat sheet, 
https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_CheatSheet.html
