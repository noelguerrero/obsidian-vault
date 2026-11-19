Sensitive Data Exposure occurs when a website doesn't properly protect (or remove) sensitive clear-text information to the end-user; usually found in a site's frontend source code.

Websites are made of HTML, which anyone can see by viewing the page source. Sometimes developers forget to remove sensitive information like login credentials, hidden links, or comments in the HTML or JavaScript.

![](https://assets.tryhackme.com/additional/how-websites-work/html_source.png)

Attackers can use this exposed information to gain access to restricted parts of a website. For example, a comment in the source code might contain a temporary username and password that can be used to log in.

That’s why one of the first steps in checking a website’s security is to review the page source for exposed credentials or hidden links.

