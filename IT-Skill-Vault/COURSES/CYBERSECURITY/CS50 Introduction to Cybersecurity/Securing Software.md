## How you implement this attacks and how you notice it?

### Phishing
- is a cyberattack that designed to get the user information or keystrokes through phishing websites or keyloggers

This is the website looks like when we download it (visiting) in browsers 

```
<DOCTYPE HTML> 
<head> 
...
</head>

<body>
 ....
</body>

</HTML>
```

So their is a tag like this that has some kind of content that maybe a technology who can get our keystrokes or behavior on navigating a websites. 
```
<script> content </script>
```

And their is a tag called anchor tag < a >
```
<a href="harvard.com">harvard.edu</a>
```
![[Pasted image 20250103173447.png]]

So by hovering (itutok) your mouse through the hyperlink you can see what website you're going and you can confirm it if you are going on the specific website that you want. 


Anyone can modify that specific tag like this.
```
<a href="https://yale.edu">https://harvard.edu</a>
```

So if you want click something and you see their is something suspicious website below like this, you can just avoid clicking it.
![[Pasted image 20250103174240.png]]
In this case the website show by clicking it you can go into harvard website, but if you hover you mouse into the hyperlink you can see, that the website seems correct or suspicious.

it looks like you are going to harvard website . but in reality you are going to a different website.

But maybe the attacker is more cleaver that he/she link a URL that change a only one key (like harvard.ed==o==) to be looks like it going to the real one, and then to be more exact he/she copy the html code of that website to be more looks like the real one. But in reality it is a phishing website that can get your information.


### Code Injection
- is a cyberattack that exploit the vulnerability of the security of a program or system and inject malicious code to gain unauthorized access, steal a data, or causing system disruption.
- Target: Website or applications code or its logic, by using malicious scripts it leads to malicious functionality

#### Examples of Code Injection

##### Cross-site Scripting (XSS)
- is a security vulnerability in web application where attackers inject malicious scripts (usually JavaScript) into web pages viewed by others.
- These scripts run in the browser by anyone who visit the affected pages, leading to stolen data, session hijacking, or unauthorized actions on behalf of the victim.
###### How XSS Works
1. An attacker finds a way to inject malicious code like by typing it into input fields, like a normal user typing a username or password into a website (e.g., via a comment box or URL).
2. The website doesn’t properly filter or sanitize the input, so the script gets saved or displayed.
3. When another user visits the page, their browser runs the malicious script as if it were safe.

###### Deep understanding how attackers inject the code
 1. **Find an Input Field**: Attackers look for places where they can enter data, such as:
    
    - A comment box
    - A registration form
    - A search bar

2. **Type Malicious Code**: Instead of entering regular text (like a username or a comment), they type **malicious code**. For example:
    
    `<script>alert('Hacked!');</script>`
    
    This is JavaScript code that creates a pop-up box. It’s a simple example, but attackers can use much more harmful code.
    
3. **Submit the Form**:
    
    - They hit "Submit" like any other user.
    - The website processes the input and saves it to a database or displays it on a webpage.

4. **Malicious Code Executes**:
    
    - If the website doesn’t properly sanitize or validate the input, the code gets executed when:
        - The attacker or another user views the page.
        - The website dynamically displays the attacker’s input (e.g., a comment or a username).

**It looks like this**
![[Pasted image 20250103183044.png]]

![[Pasted image 20250103183212.png]]

###### How do we avoid this kind of attack

**Preventing XSS**
Web developers can stop this by:

1. **Sanitizing Inputs**: Remove or escape special characters like `<`, `>`, and `"` from user input.
2. **Encoding Outputs**: Ensure user input is treated as text, not code, when displayed.
3. **Using a Content Security Policy (CSP)**: Restrict which scripts the browser is allowed to run.

**This is the proper behavior of website that might do**
![[Pasted image 20250103183849.png]]
So they command a website (example google) to treat only the inputs as a text not scripts.

### Types of Cross-Site Scripting Attack (XSS)

#### Reflected Attack
- ( also known as a reflected XSS attack ) is a type of Cross-Site Scripting (XSS) vulnerability. 
- In a reflected attack, malicious input is set (request) to a web application, and the application immediately includes that input in its response to the user without proper validation or sanitization.


###### How it works?

- **Crafted Malicious Link**: The attacker creates a specially crafted URL containing malicious code (e.g., JavaScript).
- **Delivery**: The attacker delivers the URL to a victim, often through phishing emails, social media messages, or forums.
- **Execution**: When the victim clicks the link, the malicious input is sent to the vulnerable web application.
- **Immediate Reflection**: The web application reflects the malicious code back to the victim's browser in its response.
- **Execution in Browser**: The victim's browser executes the malicious code, thinking it is legitimate content from the trusted application.

###### Step by step how it works

**1. Identifying the Vulnerable Application**

The attacker looks for a web application that reflects user input in its response without properly validating or escaping it. Examples of input points include:

- Search bars
- Query parameters in URLs
- Form submissions
- HTTP headers (like the `Referer` or `User-Agent`)

**Example:** A search functionality on a website that takes a query parameter and displays it on the page:

`https://example.com/search?q=hello`

If the response shows:

html

`<h1>Search Results for: hello</h1>`

without sanitizing the `q` parameter, the application might be vulnerable to reflected XSS.

---

**2. Crafting the Malicious Payload**

Once the attacker identifies the vulnerability, they craft a malicious payload. The payload is often a piece of JavaScript code designed to execute when rendered in the victim’s browser.

**Example Payload:**

javascript


`<script>alert('You have been hacked!');</script>`

The attacker embeds this payload into the vulnerable input parameter:

php


`https://example.com/search?q=<script>alert('Hacked!')</script>`

---

**3. Delivering the Payload**

The attacker must trick the victim into clicking the malicious link or submitting the crafted input. Common methods include:

- **Phishing Emails**: Sending emails with clickable links to the malicious URL.
- **Social Engineering**: Posting the malicious link on social media, forums, or comment sections.
- **Malvertising**: Embedding the link in advertisements.
- **URL Shorteners**: Hiding the malicious URL behind shortened links.

---

**4. Processing by the Vulnerable Application**

When the victim clicks the link, the following occurs:

1. The crafted URL is sent as a request to the web server.
2. The server processes the request and reflects the input (with the malicious code) back in the HTTP response.

**Example Response:**

```
<!DOCTYPE html>
<html>
<head>
    <title>Search Results</title>
</head>
<body>
    <h1>Search Results for: <script>alert('Hacked!')</script></h1>
</body>
</html>

```

Notice that the payload (`<script>alert('Hacked!')</script>`) is directly embedded in the response without being sanitized.

---

**5. Execution in the Victim’s Browser**

- The victim’s browser interprets the HTML, including the malicious `<script>` tag.
- The JavaScript executes within the context of the website.
- This execution can result in various malicious outcomes, such as displaying a popup, stealing sensitive data, or manipulating the page.

###### How to Prevent Reflected Attacks

**1. Input Validation**

- Ensure that user input does not contain dangerous characters.
- Use a whitelist approach (allow only safe characters).

**2. Output Encoding**

- Encode user input before including it in HTML responses to neutralize scripts. For example, escape `<script>` as `&lt;script&gt;`.

**3. Use HTTPOnly Cookies**

- Prevent JavaScript from accessing cookies by marking them as `HttpOnly`.

**4. Content Security Policy (CSP)**

- Implement a CSP header to restrict the execution of untrusted scripts. Example:
    
    css
    
    Copy code
    
    `Content-Security-Policy: default-src 'self';`
    

**5. Avoid Reflection**

- Redesign functionality to avoid reflecting input directly in responses.



#### Stored Attacks
- (also known as a stored XSS attack) is a type of XSS vulnerability where attacker's malicious code is permanently stored on the web server, 
- Unlike reflected attack, The stored attack deliver the malicious script to victims when they visit a page containing the stored payload.

##### How It Works:

In a stored attack, the attacker exploits an input field or functionality on the website to inject malicious code into the server. This code is stored in the application's database or files and later executed in the browsers of anyone who views the affected page.


##### Step by step how it works

**1. Identifying the Vulnerable Application**

The attacker looks for a web application that reflects user input in its response without properly validating or escaping it. Examples of input points include:

- Search bars
- Query parameters in URLs
- Form submissions
- HTTP headers (like the `Referer` or `User-Agent`)

**Example:** A search functionality on a website that takes a query parameter and displays it on the page:

arduino

Copy code

`https://example.com/search?q=hello`

If the response shows:

html

Copy code

`<h1>Search Results for: hello</h1>`

without sanitizing the `q` parameter, the application might be vulnerable to reflected XSS.

---

**2. Crafting the Malicious Payload**

Once the attacker identifies the vulnerability, they craft a malicious payload. The payload is often a piece of JavaScript code designed to execute when rendered in the victim’s browser.

**Example Payload:**

javascript

Copy code

`<script>alert('You have been hacked!');</script>`

The attacker embeds this payload into the vulnerable input parameter:

php

Copy code

`https://example.com/search?q=<script>alert('Hacked!')</script>`

---

**3. Delivering the Payload**

The attacker must trick the victim into clicking the malicious link or submitting the crafted input. Common methods include:

- **Phishing Emails**: Sending emails with clickable links to the malicious URL.
- **Social Engineering**: Posting the malicious link on social media, forums, or comment sections.
- **Malvertising**: Embedding the link in advertisements.
- **URL Shorteners**: Hiding the malicious URL behind shortened links.

---

**4. Processing by the Vulnerable Application**

When the victim clicks the link, the following occurs:

1. The crafted URL is sent as a request to the web server.
2. The server processes the request and reflects the input (with the malicious code) back in the HTTP response.

**Example Response:**

html

Copy code

`<!DOCTYPE html> <html> <head>     <title>Search Results</title> </head> <body>     <h1>Search Results for: <script>alert('Hacked!')</script></h1> </body> </html>`

Notice that the payload (`<script>alert('Hacked!')</script>`) is directly embedded in the response without being sanitized.

---

**5. Execution in the Victim’s Browser**

- The victim’s browser interprets the HTML, including the malicious `<script>` tag.
- The JavaScript executes within the context of the website.
- This execution can result in various malicious outcomes, such as displaying a popup, stealing sensitive data, or manipulating the page.

##### How to Prevent Stored Attacks

**1. Input Validation**

- Validate user inputs on the server-side and reject any input containing potentially harmful characters (e.g., `<`, `>`, `&`).

**2. Output Encoding**

- Encode stored data when rendering it in HTML to prevent malicious scripts from executing. For example:
    
    `<p>&lt;script&gt;alert('Hacked!')&lt;/script&gt;</p>`
    

**3. Use Content Security Policy (CSP)**

- Restrict what scripts can execute in the browser:
    
    `Content-Security-Policy: script-src 'self';`
    

**4. Sanitize User Inputs**

- Use libraries like DOMPurify to sanitize input fields and remove malicious scripts.

**5. Escape Special Characters in SQL**

- Use parameterized queries or prepared statements to prevent malicious input from being stored in the database.

**6. Implement Security Headers**

- Add headers like `X-XSS-Protection` to enable browser-based XSS defenses.


### Stored vs Reflected Attacks

| Aspects          | Stored XSS                               | Reflected XSS                                   |
| ---------------- | ---------------------------------------- | ----------------------------------------------- |
| Payload Location | Stored on the server and served to users | Reflected back immediately in the HTTP response |
| Persistence      | Permanent until removed                  | Temporary: requires user interaction            |
| Impact Scope     | Affects multiple users                   | target individual users                         |
| User interaction | Not required                             | Requires users to click or interact             |

### How do we prevent this kinds of attacks?

#### Character Escapes
- are sequences used in programming, markup, or data languages to represent characters that are difficult or unsafe to include directly in a string.
- They allow developers to use special characters, non-printable characters, or reserved characters to change a difficult or unsafe characters without causing syntax errors, or unexpected behavior.

###### Example:

Inputted malicious code
```
<p><script>alert("Attack")</script></p>
```

Escape the potentially unsafe characters
```
<p>&lt;script&gt;alert(&quot;Attack&quot;)&lt;/script&gt;</p>
```

###### Common Escape Sequences in JavaScript:

|**Escape**|**Meaning**|
|---|---|
|`\\`|Backslash (`\`)|
|`\'`|Single quote (`'`)|
|`\"`|Double quote (`"`)|
|`\n`|Newline|
|`\t`|Tab|
|`\r`|Carriage return|
|`\uXXXX`|Unicode character|
|`\xXX`|Hexadecimal character|

###### Common Escape Sequences in HTML:

|**Character**|**Escape Code**|
|---|---|
|`<`|`&lt;`|
|`>`|`&gt;`|
|`&`|`&amp;`|
|`"`|`&quot;`|
|`'`|`&#39;`|

**Common URL Encodings:**

|**Character**|**Encoded Form**|
|---|---|
|(space)|`%20`|
|`/`|`%2F`|
|`:`|`%3A`|
|`?`|`%3F`|

#### Use Content-Security-Policy
- is a web security policy that designed to help protect the websites and users from various attacks (like Cross-Site Scripting and Data injection attack).
- It allows developers to control the sources and content that can be loaded and executed in the webpage

##### How Does CSP Work?

1. **Set Rules:** The website defines a list of "safe sources" for content (e.g., scripts, images, styles).
2. **Browser Enforces:** The browser blocks anything not from these safe sources.
3. **Result:** Even if an attacker tries to inject malicious scripts, they won't run because they're not from an allowed source.

##### Example Scenario

1. You own a blog called **MyCoolBlog.com**.
2. Your blog has:
    - JavaScript for features like a search bar.
    - Images and styles to make it look nice.
3. You don’t want hackers to inject bad scripts or steal data.

---

**Without CSP:**

- A hacker tricks your blog into running a malicious script from their website (**EvilHacker.com**).
- That script might:
    - Show fake pop-ups.
    - Steal users’ passwords or cookies.

---

**With CSP:**

You set up a **CSP rule** like this:

http

`Content-Security-Policy: script-src 'self';`

Note: Self represents the same origin as the webpage where the policy is applied, it tells the browser to allow content (like javascript, styles, etc) only from the website's domain.

What this rule means:

- Only allow JavaScript files from **your website** (MyCoolBlog.com).
- Block all scripts from outside sources, like **EvilHacker.com**.

---

**What Happens in Action?**

1. A user visits your blog.
2. The browser checks your CSP rule.
3. The browser:
    - Allows JavaScript from **MyCoolBlog.com**.
    - Blocks any script trying to load from **EvilHacker.com**.

Result? Your blog stays safe, and the hacker’s script won’t run. 🎉


## Aside from code injection there is a type of attacks called..

### SQL Injection (SQLi)
- is a code injection attack that targets application or websites using a database.
- It manipulates SQL queries by injecting malicious input into them through input fields to execute unauthorized database commands.
- Target: Application or websites database, and using it to perform malicious activities.

##### How Does SQL Injection Work?

1. **Normal Scenario or What is inside of the search box or login form**:
    
    - A website has a search box or login form.
    - The user inputs data (like a username) that the application uses in an SQL query.
    - Example SQL query:
        
        `SELECT * FROM users WHERE username = 'John';`
        
2. **SQL Injection Scenario**:
    
    - An attacker inputs malicious SQL code instead of valid data.
    - Example input on a search bar: 
		    ` OR 1=1; --`
    - The query becomes inside:
        
        `SELECT * FROM users WHERE username = '' OR 1=1; --`

	- The purpose of 1=1 to become true or the input bar will said, the input bar has filled, because the sql inside of input bar will not run, if there is no inputted characters. Then the (--) is a comment syntax, it will comment the all code line below the query.
    - This query always returns **true** (`1=1` is always true), giving the attacker unauthorized access to the database.
    - This example injection will comment all the code below the query line, leading to  temporary disruption of a session in a application or website.


## So what is the solution for SQL Injection Attack?

### Prepared Statements
- (also called parameterized queries) are a SQL feature provided by most of database system to prevent SQL Injection attacks.
- It work by separating SQL code from data input.

#### How it works?

##### Step 1: Understanding the Problem

When user input is directly included in an SQL query, it can lead to **SQL Injection**. For example:

1. Query without prepared statements:
    
	**SQL Code:**
    `SELECT * FROM users WHERE username = '$username' AND password = '$password';`
    
2. If a user inputs:
    
    - `username`: `' OR 1=1 --`
    - `password`: (blank)
    
    The query becomes:
    
    **SQL Code:**
    `SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = '';`
    
    - The `1=1` condition is **always true**.
    - The `--` comments out the rest of the query.
    - This lets the attacker bypass login.

This happens because **user input is treated as part of the SQL code**.

---

##### Step 2: How Prepared Statements Fix This

What are Prepared Statements?

A **prepared statement** tells the database:

1. **"Here is the structure of my query."**
    - The query is written with placeholders where data will go, like:
        
        **SQL Code:**
        `SELECT * FROM users WHERE username = ? AND password = ?;`
        
2. **"Now, fill in the placeholders with this data."**
    - When you bind data (like `username` and `password`) to the placeholders, the database treats it **strictly as data**.
    - Even if the user inputs something malicious, it cannot alter the SQL structure.

---

##### Step 3: How It Works Step-by-Step

**1. The Query is Prepared**

The application sends the **query structure** to the database, but without actual user input:

**SQL Code:**
`SELECT * FROM users WHERE username = ? AND password = ?;`

- The `?` placeholders act as "empty boxes" for data.

The database:

- Analyzes the query.
- Ensures the SQL syntax is correct.
- Saves this **safe query structure** for later use.

**2. Data is Bound to Placeholders**

The application sends the user input separately, binding it to the placeholders:

- **Placeholder 1 (`?`)** gets the `username`.
- **Placeholder 2 (`?`)** gets the `password`.

For example the input of the attacker:

- **username**: `' OR 1=1 --`
- **password**: (blank)

Note: This input will comment the all the code line below the query line, This leading to bypass the login or authentication feature of the website.

The database **does not merge this input into the query structure**. Instead:

- It treats the input as **pure data**.

**3. Query is Executed**

Now the database executes the query, treating the user input as literal values:

**SQL Code:**
`SELECT * FROM users WHERE username = '\' OR 1=1 --' AND password = '';`

What happens here:

1. The input `' OR 1=1 --` is treated as **text** (a string).
2. It will not comment the rest of the code line below the query line.
3. It **cannot affect the SQL logic** because the query structure is already fixed.

So the username will be `' OR 1=1 --` only and the password is blank.


#### Example in Action

#### Without Prepared Statements:

**PHP Code:**

```
// Vulnerable Code
$username = $_GET['username'];
$password = $_GET['password'];

$query = "SELECT * FROM users WHERE username = '$username' AND password = '$password';";
$result = mysqli_query($connection, $query);
```


If an attacker inputs:

- Username: `' OR 1=1 --`
- Password: (blank)

The query becomes:

**SQL Code:**

`SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = '';`

This bypasses authentication.

---

#### With Prepared Statements:

**PHP Code:**

```
// Secure Code Using Prepared Statements
$stmt = $connection->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
$stmt->bind_param("ss", $username, $password); // "ss" means two strings
$stmt->execute();
$result = $stmt->get_result();

```

Here’s what happens:

1. The query sent to the database:
    
    **SQL Code:**
    
    `SELECT * FROM users WHERE username = ? AND password = ?;`
    
2. The user input:
    - Username: `' OR 1=1 --`
    - Password: (blank)
    
3. The database **binds the input** and treats it as literal text:
    
    **SQL Code:**
    
    `SELECT * FROM users WHERE username = '\' OR 1=1 --' AND password = '';`
    
4. No SQL Injection happens because the input cannot alter the SQL query.
	- It treats the `' OR 1=1 --` as a text on username.


## There is another type of injection called..

### Command Injection
- is a security vulnerability that occurs by executing a malicious commands on a hots operating system through a vulnerable application.
- This happens when the application passes the attacker's input (malicious commands) directly to system commands without proper validation or sanitization.
- Target: System files or operating system,  by inputting malicious commands through vulnerable application.

#### How It Works

Command injection exploits occur when:

1. An application takes user input and incorporates it into a command-line execution string.
2. The input is not properly validated or sanitized.
3. The attacker manipulates the input to include additional commands, which are executed by the operating system.

##### Common Scenarios

- **Web Applications**: A web application might use system commands to interact with the file system, e.g., for file uploads or server diagnostics.
- **Scripts**: Shell scripts that process user input are particularly vulnerable.
- **Dynamic Command Execution**: Applications that use functions like `exec()`, `system()`, `popen()`, or their equivalents in different programming languages without sanitizing inputs.

##### Example:

**Vulnerable Code (PHP)**

```
<?php
$user_input = $_GET['filename'];
// Vulnerable code
$output = shell_exec("cat " . $user_input);
echo $output;
?>

```

**Exploit**

By supplying a malicious input like `filename=file.txt; rm -rf /`, the attacker could execute unintended commands:

**bash code:**
`cat file.txt; rm -rf /`

**Consequences**

- **Data Breach**: Access to sensitive data.
- **System Compromise**: Full control over the server.
- **Data Loss**: Destruction of files and databases.
- **Service Disruption**: Denial of Service (DoS) attacks.

#### Prevention
- **Input Validation**:
    - Whitelist acceptable input formats.
    - Reject or sanitize suspicious input.
- **Avoid Direct Command Execution**:
    - Use APIs or libraries for system-level tasks rather than invoking shell commands.
- **Parameterize Commands**:
    - Use mechanisms that separate data from commands, e.g., Python's `subprocess.run()` with argument arrays.
- **Least Privilege Principle**:
    - Run applications with minimal permissions.
- **Escaping Input**:
    - Escape special characters in user input to neutralize malicious payloads.



##  In the context of the browser there is a feature called Developer Tools, that attackers might take advantage of the feature of that.

### Developer Tools (DevTools)
- It is a built in tools in modern browser nowadays (chrome, safari, and etc) these tools are essential for web development and troubleshooting. 
- It allows developers to inspect, debug, analyze websites or web applications.

The problem of this when the user are aware of this kind of tool, they can edit the website source code to **altered there session temporary** ( they can use developer tools for **temporary local modifications** and to aid in exploiting vulnerabilities ), so if you are not paranoid enough to be aware of possibilities they can to something malicious.   

#### How Attackers Might Exploit Developer Tools

Although changes made via Developer Tools are temporary and local, attackers can use them to:

1. **Understand the Website's Functionality**:
    
    - Inspect source code, APIs, and JavaScript logic to identify vulnerabilities.
    - For example, finding exposed API keys, endpoints, or sensitive information in the JavaScript files.

2. **Manipulate HTML and JavaScript**:
    
    - Change form behavior to bypass client-side validation (e.g., removing required fields or changing input constraints).
    - Modify JavaScript logic to skip certain checks.
    
    Example:
    
    - If a form uses client-side validation to ensure only positive numbers are entered, an attacker can disable this in Developer Tools and submit negative or extreme values.

3. **Replay or Manipulate Network Requests**:
    
    - Use the **Network Panel** to observe and analyze requests sent to the server.
    - Modify parameters in API calls or submit custom payloads using tools like Postman or cURL.
    
    Example:
    
    - A web application may include a hidden parameter like `price=100`. An attacker could manipulate this to `price=1` and attempt to make a purchase at an unfair price.

4. **Steal Sensitive Information**:
    
    - Inspect cookies, local storage, or session storage for sensitive data (e.g., session tokens, user credentials, or API keys).
    - If the website improperly stores sensitive information in these areas, an attacker could use it to impersonate users or access restricted areas.

5. **Exploit Weaknesses in Security**:
    
    - Bypass Content Security Policies (CSP) by injecting malicious scripts.
    - Test Cross-Site Scripting (XSS) payloads or other injection techniques.

6. **Gather Information for Phishing**:
    
    - Use Developer Tools to copy the structure and content of a website, which can then be used to create a phishing site that mimics the original.

The take away this is to **never rely on the client-side validation** because it runs in the user's browser, which is an environment controlled by user an can be easily manipulated.

##### Client-side validation 
- is a process of verifying user input in the browser before it is sent to the server. 
- It ensures that the data entered by the user meets certain criteria (like require fields, proper format or valid range) and provides a immediate feedback without requiring a round-trip to the server.

##### When you trust Client-Side Validation

**When the website require a password input**
`<input required type="text"> //a password check box`

By using DevTools the attacker can disable this check box and so they can  have no input.

The client-side send the attack inputs (that page session), and then if the server trusting the client-side validation, the attacker will proceed to the next pages of the website.

So you must use **Server-Side Validation.**

##### Server-Side Validation
- is a process of validating user input on the server before processing it.
- This ensure that the data receive from the client-side (browser or app) meets the expected criteria.
- Server-side validation is a critical security measure because it cannot bypassed by disabling JavaScript, modifying HTML, or using tools like Postman or cURL.

Client-Side is good for enhance user experience by immediate feedback, but **it must always accompanied by a Server-Side Validation.** 

## Lets consider another class of attack which your code might be vulnerable if it's on a server using a same language, HTML namely Cross-Site Request Forgeries, or CSRF's.

### Cross-Site Request Forgery (CSRF)
- is a type of web security vulnerability that allows an attacker to trick user and performing unwanted action behalf of the user on that websites where it is authenticated.

#### How CSRF Works

CSRF exploits the trust that a website has in a user's browser. When a user is logged into a website, their browser includes their session cookies (or other authentication tokens) with any request sent to the site. An attacker can use this behavior to make unauthorized requests.

#### Steps in a CSRF Attack

1. **Victim Authenticates on a Website**:
    
    - The user logs into a trusted website (e.g., `bank.com`) and a session cookie is stored in their browser.

2. **Victim Visits a Malicious Site**:
    
    - The attacker tricks the user into visiting a malicious website or clicking a crafted link (e.g., via email or ads).

3. **Malicious Request is Sent**:
    
    - The malicious site contains code (e.g., an image, script, or hidden form) that sends a request to `bank.com` using the victim’s browser.
    - The browser includes the session cookie with the request, making it appear legitimate.

4. **Action is Executed**:
    
    - The server processes the request, thinking it was made by the authenticated user.

#### Example of a CSRF Attack

#### Scenario: Bank Transfer

1. The user logs into their online banking site (`bank.com`) and stays authenticated.
2. The attacker sends the victim an email/image that contains malicious link:
    HTML Code:
    `<img src="https://bank.com/transfer?to=attacker&amount=1000">`
    
3. If the victim is logged into `bank.com` and clicks the link, the browser sends a GET request to `https://bank.com/transfer?to=attacker&amount=1000` with the user's session cookie.

4. The bank's server processes the request and transfers money to the attacker.


#### Difference Between CSRF and XSS

| Aspect         | CSRF                                         | XSS                                                              |
| -------------- | -------------------------------------------- | ---------------------------------------------------------------- |
| Full Form      | Cross-Site Request Forgery                   | Cross-Site Scripting                                             |
| Focus          | Exploits the trust of website into the user. | Exploits the trust of the user into websites.                    |
| Execution      | Requires user interaction (clicking link).   | Injects and executes malicious scripts directly on the websites. |
| Authentication | Requires the victim to be authenticated.     | Does not necessarily require authentication.                     |
| Attack Goal    | Perform unauthorized actions.                | Steal sensitive information or hijack sessions.                  |

### So it turns out that " GET " (a function of specific programming language like PHP) is not a good thing when it comes to changing state on the server. 

#### GET method
- is a HTTP request method used to retrieve data from a server
- one of the most common methods used in web development.

**When to Use `GET`:**

- When you want to **retrieve** information without making any changes.
- Example scenarios:
    - Viewing a product list or a webpage.
    - Performing a search operation where the result is displayed in the same or another page.

**Example of a `GET` Request:**

**html code:**
```
<form method="GET" action="/search">
    <input type="text" name="query" placeholder="Search">
    <button type="submit">Search</button>
</form>

```

This form sends a `GET` request to the server, and the URL might look like this:

**URL will be:**
`https://example.com/search?query=laptop`


if the website implement get method in crucial state-changing (like delete, create, purchase in you websites) it is vulnerable to attacks like CSRF, because that attack works with parameters like get method do.
`https://example.com/deleteAccount?userId=123`

**GET has lacks protections**, so using it for modifying data exposes you to accidental or malicious triggers, **POST is better for actions that change server data because it's designed for deliberate, secure request.**

#### POST method
- is an HTTP request used to send data from the server to create or update. 
- Unlike GET method append data to the URL, POST method sent data through request body, making it hidden.

**When to Use `POST`:**

- **When creating or modifying data** on the server (e.g., submitting forms, adding items to a cart).
- **When sending large amounts of data** or sensitive information that should not be exposed in the URL.

**Example of a `POST` Request:**

A form to submit a new user account:
```
<form method="POST" action="/register">
    <input type="text" name="username" placeholder="Username">
    <input type="password" name="password" placeholder="Password">
    <button type="submit">Register</button>
</form>

```
When the form is submitted, the data (`username` and `password`) is sent in the request body, not in the URL.

#### Difference Between GET and POST:

| Aspects              | GET                                   | POST                                         |
| -------------------- | ------------------------------------- | -------------------------------------------- |
| Purpose              | Retrieve data (read-only).            | Send data to the server (write or update).   |
| URL Visibility       | Data appended to the URL (`?query`)   | Data is sent in the request body (hidden).   |
| Caching              | Can be cached by browsers or proxies. | Not cached (designed for sensitive actions). |
| Security for changes | Not secure for changing data.         | Secure (used for state-changing actions).    |
So POST method is more secure because when the website implements GET method on crucial state-changing, and the user is victim from malicious link that contains parameters, the website can trigger those malicious link and perform its purpose. But when the website implements POST method on the crucial state-changing it can easily ignore it, or it shows a kind of authentication form, leading to user to be suspicious of the link behavior. 

## But that form can attacker uses in another malicious intent, So it doesn't matter if you are using POST or GET method if the website didn't follow the secured rules.

This is a phishing button that if you put your credit value and if you click the button it will automatically your account will buy a certain product.

Assuming that you accidentally type your sensitive credentials (bank number, bank password).

```
<form action="https://www.amazon.com/" method="post">
<input name="dp" type="hidden" value="B07kLqzWSk">
<button type ="submit">Buy Now</button>
</form>
```

although you accidentally type your credentials, it won't work because it need a user intervention (click the button) before your credentials is submit, so you can think if this is a legitimate or not.

it turns out that the attacker can enhance this code to do their malicious intent

```
<form action="https://www.amazon.com/" method="post">
<input name="dp" type="hidden" value="B07kLqzWSk">
<button type ="submit">Buy Now</button>
</form>
<script>
	document.form[0].submit();
</script>
```

By applying this script, the form submit automatically the inputs when you accidentally type your credentials.

### So how can we defend this kind of threat in you website or system

By applying a CSRF Token (randomly generated token like hidden value, token, code) that based on the user accounts, it will be more secured because the attacker might be difficult to identify what is the hidden value of the user.
```
<form action="https://www.amazon.com/" method="post">
	<input name="csrf_token" type="hidden" value="1234abcd">
	<input name="dp" type="hidden" value="B07kLqzWSk">
	<button type="submit">Buy Now</button>
</form>
```
If the attacker malicious form have not or didn't match the hidden value it won't work. 

### It is possible to input this token as HTTP headers as well

```
POST / HTTP/3
Host: amazon.com
X-CSRFToken: 1234abcd
```

## If you interested this kind of web-centric attacks, you might consider explore the Open Worldwide Application Security Project (OWASP)

### Open Worldwide Application Security Project (OWASP)
- is a non-profit organization focused on improving the security of software and applications.
- It provides a variety of tools, resources, and guidelines to help organizations, developers, and security professionals build and maintain secure system.

## Class of attacks that particularly common when it comes to software that's running on your Mac, PC or Phone

### Arbitrary Code Execution (ACE)
- it is a type of security vulnerability that allows an attacker to execute malicious instruction or code on a system or within software application, potentially leading to full system compromise.
- This is a example of **Remote Code Execution (RCE)**
	- it is a attack where if the adversary is somewhere else in the world perhaps connected via internet.

#### General Information how it works

**1. Identifying a Vulnerability**

The attacker identifies a flaw in the target software, application, or system. Common types of vulnerabilities that lead to ACE include:

- **Buffer Overflows**: A program writes data beyond the allocated memory buffer, allowing the attacker to inject and execute code.
- **Improper Input Validation**: The application fails to sanitize user input, enabling malicious payloads to be processed as executable code.
- **Insecure Deserialization**: Deserializing untrusted data allows attackers to craft payloads that execute commands during the deserialization process.
- **Command Injection**: The application allows unsanitized inputs to be interpreted as system commands.

---

**2. Crafting the Payload**

Once the vulnerability is identified, the attacker creates a **payload**, which is the malicious code or commands they want the system to execute. Examples of payloads include:

- Executing system commands (e.g., creating backdoors, reading sensitive files).
- Deploying malware (e.g., ransomware, keyloggers).
- Manipulating application behavior (e.g., disabling security mechanisms).

---

**3. Delivering the Payload**

The attacker delivers the malicious payload through one of several methods:

- **User Input Fields**: Injecting the payload into input fields (e.g., forms, URLs) that the application processes improperly.
- **File Uploads**: Uploading files containing malicious code that the application executes.
- **Network Requests**: Exploiting vulnerable APIs or services by sending specially crafted network packets.
- **Phishing or Social Engineering**: Tricking a user into executing the malicious code on their system.

---

**4. Exploiting the Vulnerability**

The system or application processes the malicious payload due to the vulnerability:

- If the input isn't properly validated, the application might execute the attacker's code.
- If there's a buffer overflow, the injected payload might overwrite critical memory areas (e.g., return addresses) to redirect execution to the attacker's code.
- If deserialization flaws exist, malicious objects can trigger the execution of arbitrary methods.

---

**5. Executing Malicious Code**

Once the payload is successfully delivered and processed, the system executes the attacker's code. This can lead to:

- **Privilege Escalation**: Gaining higher-level access to the system.
- **Data Theft**: Accessing and exfiltrating sensitive information.
- **System Takeover**: Gaining full control of the compromised system.
- **Persistence**: Installing backdoors or malware for future access.


#### Key Differences between Command Injection and Arbitrary Code Execution

| Aspect               | Command Injection                                      | Arbitrary Code Execution                                                                  |
| -------------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------- |
| Mechanism            | Injects malicious input into system command execution. | Injects malicious input into the program's execution flow (eg.. memory, deserialization)  |
| Scope of Impact      | Limited to executing system commands.                  | Broader: includes system commands, scripts, or low-level code.                            |
| Exploitation Context | Usually through inputs passed to OS commands.          | Often exploits program-level vulnerabilities (e,g., buffer overflows, memory corruption). |
| Examples             | Injecting shell commands via unsanitized input.        | Exploiting a buffer overflow to execute custom shellcode.                                 |

#### One of the common mechanism of Arbitrary Code Execution is Buffer Overflow

##### Buffer Overflow
- is a type of programming error or vulnerability that occurs when a program writes more data to a buffer (a fixed-size block of memory) that it is designed to hold. This can result overwritting other memory, leading to erratic program behavior, crashes, or exploitable security vulnerabilities.

###### How It Happens

1. **Buffer Definition**: A buffer is a contiguous block of memory allocated to store data, such as an array or a character string.
2. **Input Exceeds Size**: When input data exceeds the buffer's capacity and no boundary checks are in place, the extra data spills over into adjacent memory locations.
3. **Unintended Effects**: This overflow can overwrite critical program data, such as:
    - Return addresses in the call stack.
    - Adjacent variables in memory.



## Cracking
- it is refers to a practice of bypassing or breaking the security of a system, software, or digital content to gain unauthorized access, functionality, or benefits.
- Example: cracking a specific app like spotify to access the VIP functionality without payment..

**Reverse engineering** is on of the example of cracking.

### Reverse Engineering
- is a process of analyzing how system, software, or device work and disassembling and deconstruct it, to uncover (means reveal or discover) its design, functionality and operation.

There is a good side in reverse engineering, you can **analysis the malwares**. Malware Analysis has a same idea how reverse engineering works.

### Malware analysis
- is a process of examining and understanding malicious software (malware) to determine its behavior, purpose and potential impact on a system, network, and software.

## How might you hedge (protect or reduce the effect ) of this kind of threats of remote code like Arbitrary code with software of you own?

Start using **open source software**, so you can have an idea how other works in their software and what other people ways to defend this kind of attack. 

### Open Source Software
- is a software that is distributed with its source code, allowing anyone to view,  modify, and distribute the code.

**Examples of Open Source Software**:

- **Operating Systems**: Linux, FreeBSD
- **Web Browsers**: Mozilla Firefox
- **Office Suites**: LibreOffice, Apache OpenOffice
- **Programming Languages**: Python, PHP, Ruby
- **Databases**: MySQL, PostgreSQL
- **Development Tools**: Git, Eclipse, Visual Studio Code

**Benefits**:

- Cost-effective (often free to use).
- High transparency and security (code is publicly reviewed).
- Flexibility and adaptability for specific needs.
- Fosters innovation and learning.

**Why it's a hedge**:**
-  Unlike closed-source software, where vulnerabilities might remain hidden, open source software reduces the risk of hidden exploits being unnoticed.

So the alternative one is **closed-source software**

### Closed source software 
- also known as proprietary software a software that its source code is not available into public.
- Because of that the the developers and organization who owns the software, can only view, modify or distribute the code.

**Examples of Closed-Source Software**:

- **Operating Systems**: Microsoft Windows, macOS
- **Productivity Tools**: Microsoft Office, Adobe Photoshop
- **Media Players**: Netflix app, iTunes
- **Games**: Most commercially sold video games (e.g., Call of Duty, FIFA)

Since, its not public the possibilities of exploiting the closed-source software low.

## What is the other way to prevent some infected software that you installing in?

 **Just download into legal App stores**
 
## So how can the app store enforce the user to install the software in their store

### First this is how the author of the app digitally sign the app when its upload to app stores.

] When the app is uploading to app store it uses a digital signature formula the we previously discuss.

**When the software created it will be convert into hash value:**

Software -> Hash

**So with that hash the author can give his/her digital signature into the app stores.

Hash with private key -> signature

**So the app store can verified that you the author the one who wrote that app. Then the author can register his/her public key when you updates it, so store can assume that you the author who update that app not a random person.

#### This method is also uses the app store to digitally signature the app, so our phones  or the users can identify its from google or apple.  


Another mechanism or terminology that is used in the world of linux computers called **Package Managers**

### Package Managers
- its a tool that interacts with the operating system's (like linux) repositories to install, update, or remove packages. It also handles the dependency resolution to ensure that all required components are present.
- So when we install application the package managers verified it before it installed.


Also the **Operating system** involves on verifying the application before its installed

### Operating System
- it is a primary software that handles the software and hardware of the device (like phones, computers, and etc).

- Operating building a support for verifying applications, but its difficult to some install third-party software, specially when the OS didn't support or allow a that specific application.

**But also don't securely trust your application because maybe there have a malicious intent in the end or their computers are hacked.**

## There are models that the world has been experimenting with overtime to reduce that malicious probabilities.


### Bug Bounty
- is a program where the company or organization encourage the ethical hackers, security researchers, and developers to identify and report the security vulnerabilities, bug, and weaknesses in their software, websites, or system, and in return they reward them.

## So where can you learn about the threats how the worlds handles it?

So all the threats we discuss is on **Common Vulnerabilities and Exposures (CVE)**

### Common Vulnerabilities and Exposures (CVE)
- is a system used to publicly identify and catalog security vulnerabilities and exposures in software, hardware, and systems.
- It provide a standardized way to reference those vulnerabilities, making for the developers to track and discuss them.

There is a **Common Vulnerability Scoring Systems (CVSS)** to standardized way of assigning numeric score for this kind of threat or vulnerabilities and helps organizations on what will prioritize based on **the severity and potential impact.**

Also there is **Exploit Prediction Scoring System (EPSS)** it provides numeric value that helps the organizations on measuring the **likelihood** of a vulnerability being actively exploited, helping organizations assess which vulnerabilities are most likely to be targeted.

Note: **likelihood - a chance of vulnerabilities being target.

**EPSS vs. CVSS**

- **CVSS** measures the **severity** of a vulnerability based on its potential impact on the system.
- **EPSS** measures the **likelihood** of a vulnerability being actively exploited, helping organizations assess which vulnerabilities are most likely to be targeted.

For example:

- A vulnerability with a **high CVSS score** (indicating severity) but a **low EPSS score** (indicating low likelihood of exploitation) might be considered less urgent to patch than a vulnerability with a **medium CVSS score** but a **high EPSS score** (indicating a high likelihood of exploitation).

And their is **Known Exploited Vulnerabilities Catalog (KEV)** it provides a list of vulnerabilities that are actively being exploited in cyberattacks.

