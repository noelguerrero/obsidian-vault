
## One of the feature of browser

### Web Browsing History
- it is a feature of the browser that list the previous and current website visited by user.
- We don't want someone sees our history when they use or maliciously control our device, so for our privacy we can sanitize or clear our browsing history. 

## The other concern beyond our history...

### Logs
- It is a feature of servers that record our logins in websites.
- If user encounter a problem a the Admin or IT staff of the servers can configure or perform diagnostic to solve our problem. and also they can use that feature in other purposes like, auditing, advertising, and etc.

When you visiting a website, inside of the virtual envelop it looks like this
```
log-format combined 'remote_addr' - $remote_user [$time_local] '
'"$request" $ status $body_bytes_sent '
'"https_referer" "https_user_agnet"' 
```

When you visiting a website it remember the: 
- Address of the user ('remote_addr')
- time of the user visits the websites ($time_local)
- the request the file and folder (' $request ')
- the referrer, that is the URL from which you came ("https_referer")
- And the user agent that you used ("https_user_agent")

It looks like server stored the information that you don't want to stored like (the address of the user), But the user have not the control to delete or manage the data that stored in the servers.

## Lets consider the technical details, about some of this information and how we might get control over some of information being shared.

### Https Headers
- is a key-value pairs inside of virtual envelop that sent between client and servers that provide essential information about the request and response.

**Http Request Example:**
```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html

```

**Http Response Example:**
```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1024
Server: Apache
Set-Cookie: sessionId=abc123; Path=/; HttpOnly
```

#### When you search somethin like Cats. 

Search panel: Cats

It turns out that the browser not only goes and request to go to that webpage (that contains cats) but also includes the content in the http header and the URL. 

Referer: `Https://www.google.com/search?q=cats`

The browser telling the whole world about which webpage you came, but it is actually useful for the servers, like their analytics, they can know how people finding their websites or business and know how many users visits it. 


#### Ideally we want a less information at least or get rid of this

**Like this**
Referer: `Https://www.google.com/


## How website moderating it and how much output comes from the browser at the server's request?

##### This code is a common tag that the webpage can put in their own HTML code that indicates the browser, It send the referring address, but only send the origin.

HTML code:
`<meta name="referrer" content="origin">`

It send less information, not the whole URL, but only the origin.

##### if you don't want to sent any of that, you can do this instead. 

HTML Code:
`<meta name="referrer" content="none">`

It indicates that don't send a referrer, because the value of the content is 'none'.

And also there are other values that allow you a bit  of range when it comes to this settings.

##### There's an alternative too

If you little more technical and have a control over the web server and not just the HTML on the server.

You can configure a referrer policy in HTTP header. 

**HTTP Header:**
`Referrer-Policy: origin`

This indicates that you only want the origin to be sent.

Or you can indicates that no referrer

**HTTP Header:**
`Referrer-Policy: no-referrer`

## There's is a technique that server use to verify user

### Fingerprinting
- It is a technique that used by the server to identify or recognize clients based on the request of the user, attributes or behavior of their system. 

#### how might this implemented?
The simplest mechanism of it, it rely on the IP address, because any time we do something on the internet i sent and receive a virtual envelop, inside of those envelop have your IP address and also the destination IP address.

#### Inside of those virtual envelop it share another information as well

It is called **User-Agent** -> it is a unique string of text that identifies the browser that you're using, the version thereof, the operating system that you're using and the version thereof. 

**HTTP Header:**
`User-Agent`

The standard format might look like this:

```
Mozilla/5.0 {Linux; {Android Version}; {Build Tag etc.}}
AppleWebKit/ {WebKit Rev} (KHTML, like Gecko)
Chrome/{Chrome Rev} Mobile Safari/{WebKit Rev}
```


## There is another type of header that also includes in the virtual envelop that will back and fort on the server and the user device.

### Session Cookies
- is a piece of information that server puts on you computer to help remember who you are.

#### How session cookies works?

- When you first visit a website that wants to plant a cookie on you computer, it looks like this.

```
HTTP/3 200
Set-Cookie: session=1234abcd
```

- It respond his status code, then it will give your computer a random cookie value.

	Note: It will suppose to expire when you exit or close the browser.

- When the cookie is receive by the device and visit some other page of that website, the browser will send this.

```
GET / HTTP/3
Cookie: session=1234abcd
```

- And when the cookie is same, the server remember you and direct you to the page.


### Tracking Cookies
- is a key value pairs that sever puts into your device to remember you, but the difference is, it is designed to track the user device.
- Unlike session cookie that expire, the tracking cookie can set a maximum time (number of seconds) for being valid.

**Example Tracking Cookie:**
```
Set-Cookie: _ga=GA1.2.0123456789.0; max-age=63072000
```

It uses a cookie called `_ga` for google analytics for analytic purposes. The google analytics help the designers of the website to identify and track their user's behavior and details of their device.


## What might server uses to keep track on us?

### Tracking Parameters
- HTTP parameters or tracking parameters is a key value that usually appear in the URL. 
- Like this: `https://www.google/search?q=CATS` (cats is the example parameter) . It could be used not only for helpful purposes, but to track you.

**Example URL with tracking parameter**
```
https://example.com/ad_engagement?click_id=YmqifAWUfk44&campaign_id=23
```
- This URL take you into example.com
- have a path called as_engagement?
- have a click id that have a value of random generated characters. `click_id=Ymq....` -> is tracking to you maybe those are the address that set in your device by the servers
- and there is a second http parameters `&campaign-id=23` -> that meant to the sufficient input to the website to know what types of ads should be serve in you.

When other website or third-part software knows that the parameters like click-id has no good purposes rather than track you, maybe they remove or sanitize it for the privacy of their users. 
```
https://example.com/ad_engagement?campaign_id=23
```

#### How might this parameters can track us?
-> This parameters can end up into server logs, that the IT admin uses to know what are the user's behaviors.


## So there's another way to think about tracking cookies...

is to consider them to be **Third-party cookies.**

When you visit **example.com**, it’s the **first-party website**. If example.com uses **Google Analytics** (a tool from Google), it embeds code that connects to **google.com**.

- **First-party cookies**: Set by **example.com** to improve your experience (e.g., remembering login or preferences).
- **Third-party cookies**: Set by **google.com** (the third party) to track your behavior on example.com and other sites that also use Google tools. Maybe for analytical purposes of google.

First-party cookies directly relate to the site you chose to visit, while third-party cookies enable broader tracking across the web. **So the third party cookies can have an impact on your online privacy.**

However, the browsers do commonly is offer options which can disable third-party cookies. but this doesn't mean that the websites isn't still uses tracking parameters in some way.

### Third-party is most powerful 

**This is why?**

When a user visits three school websites: **Harvard**, **Stanford**, and **Yale**. All three websites display ads from **example.com**, which sets a **third-party cookie** on the user's browser.

When the user clicks the ad on any of the school websites, **example.com** can see:

-  The user visited Harvard, Stanford, and Yale.
-  The user clicked the ad (without knowing the other schools)

This shows how **third-party cookies** allow example.com to track the user's activity across multiple websites, making them very powerful for tracking and advertising.


## What can we do to protect our privacy?

#### Private Browsing
- is a special feature of browser that puts you into private mode or incognito mode that doesn't remember your cookies, history, logs and etc.  


## Supercookies
- These cookie are typically injected by the third-party into your HTTP request. 

Like Internet Service Providers (example of third-party) can inject cookies into the traffic between your device and the server of the website you've visit.

This is the typically the default traffic
```
GET / HTTP/3
Host: example.com
```

The third-party have the ability to inject there cookies. 
```
GET / HTTP/3
Host: example.com
Cookie: id=123345
```

So the Internet service provider can track your behavior on the browser like browsing habits and etc.  But if you using HTTPS it can reduce the opportunity for the third-party to track your behavior because of its encryption feature. 


## Let's consider another threat to your privacy

### DNS (Domain Name System)
- It is a system that translate the IP address of the websites into their english like words or their name (like facebook.com, youtube.com, Google.com and etc).

##### Why is this problematic?
It turns out that DNS is in a lots of different places like your home, school, company, and etc. And it is built into the router or the device that you're using just to connect to the internet. But the internet service provider tends to have DNS server the have deeply way known more than IP addresses in your home or office.

The problem is the traffic used for DNS is typically unencrypted (like when you search to the browser, the browser will ask the server provider what is the IP address of this website), which means that when your laptop, phone, or another device is asking what is the IP address of this website (like fb.com, youtube.com), your actually announce to the world what website you are about to visit.  

Your internet service provider knowns all of this information. Because every time you ask for IP address for this website, you asking it into your internet service provider and if they not known they ask a other servers.


## There are an alternatives to the standard DNS

### DNS over HTTPS (DoH)
- This is just instead of sending out DNS request unencrypted to the local DNS server, now they're sent it (if you enable it) over HTTPS that is securely.

There is also alternative to this **DNS over TLS (DoT)**

### DNS over TLS (DoT)
- this is similar into DoH but i doesn't bother HTTPS to sent DNS request, But still using encryption for the request. 


## Lets consider another mechanisms that can push back this invasive privacy practices

### Virtual Private Network (VPN)
- is a technology that hiding your device identity and represent you to protect your privacy.
- It allows to connect from point A to B using encrypted tunnel.

##### What is the implication of this?
VPN only guarantees that the connection between you and point B is encrypted. and change what your IP address appears to be, so indeed you appear with an IP address that is for that specific country.


There's another software that is popular for some time called **Tor, The Onion Router.**

### Tor
- is a software that you can install in your device and this uses a encryption to solve the problem a different way using additional encryption to get a higher probability of privacy.
- **How It Works:** Routes encrypted data through multiple volunteer-operated servers (nodes):
    - **Entry Node:** Knows your IP but not the destination.
    - **Middle Nodes:** Relays encrypted data.
    - **Exit Node:** Sends data to its final destination, knowing only the destination.
- **Uses:** Privacy, bypassing censorship, accessing the dark web.
- **Limitations:** Slow speed, potential exit node vulnerabilities, and misuse for illegal activities.

Note: the prof said that every node is encrypting the data that flowing around the tor network, but the chatGPT said it only relays and decrypt only a specific part of data known where to relays the data.


### Permissions
- is a feature on our device that can give an access or denied a specific software into the device application, feature or program. 


There is some feature that might need to be mindful to run all of the time which is **Location-Based Services**

### Location-Based Services
- is a service that can track our location using GPS, WiFi, or other technologies.

This applications by default it always on a track our current location. By that Google or Apples can know our location so you should be mindful about turning on of that by default. 