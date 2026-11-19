## PASSWORD

**Authentication** - proving who you are.

**Authorization** - Whether or not you should access on something once you had prove him.

#### When incomes to accounts:

**Username**: 
- it can be public
- Uniquely identify you 

**Password:**
- It must be private
- It allows you authenticate yourself, demonstrate who you are.
- Not re-use in other website.

### Dictionary attack 
- It is a type of cyberattack that crack your password by guessing it using  a physical book of words or a file that contains a English words or other some human language (predefine password like: password123, qwerty, and etc) to know your password and unlock your account. 

**To avoid that use**
- Good Password: Strong, unique passwords that prevent dictionary attacks and brute force attacks.

### Brute force attacks 
- is a cyberattack that cracks the password, encrypted information and etc, by using scripts that generating letter, digits, and symbols (example aaaa, 0000, 123abcd and etc) that tries every possible combination of characters . 

#### Example of brute force scenarios and codes:

**A.** If we your are using 4 digits of decimal number password, it has 10,000 Possible passwords.
10 x 10 x 10 x 10 = 10^4 <-- estimate of 10,000 possible password

Example code that brute force the 4 digits decimal password:
```
File name: crack.py 

from string import digits

for i in digits:
	for j in digits:
		for k in digits:
			for l in digits:
				print (i,j,k,l)
```
**Comment:** It has a miliseconds speed to print all password 0000 to 9999
**Take away:** if you are using a 4 digits password, it is not secure at all.


**B.** If you are using 4 english letters, we have 26 uppercase (A - Z), and 26 lowercase (a - z) is total of 52. 
52 x 52 x 52 x 52 = 52^4 <- estimate of  7,311,616 possible passwords <- this is not the total of 52^4 but it is a total of possible passwords.

Example code that brute force the 4 English letter password:
```
File name: crack.py <-- .py is python

from string import ascii_letters <-- a letters a to z uppercase and lowercase

for i in ascii_letters:
	for j in ascii_letters:
		for k in ascii_letters:
			for l in ascii_letters:
				print (i,j,k,l)
```
**Comment:** It has a few seconds to print aaaa to zzzz uppercase and lowercase
**Takeaways:** So meaning a 4 digits alphabet is not secure at all


**C.** If you are using 4 characters, compose of letters, digits, and punctuation. so it has 94 keys (52 letters uppercase and lowercase, 0-9 digits, 32 symbols)
94 x 94 x 94 x 94 = 94^4 <-- estimate of 78,074,896 possible passwords.

Example code that brute force the 4 character password:
```
File name: crack.py <-- .py is python

from string import ascii_letters, digits, punctuation

for i in ascii_letters + digits + punctuation:
	for j in ascii_letters + digits + punctuation:
		for k in ascii_letters + digits + punctuation:
			for l in ascii_letters + digits + punctuation:
				print (i,j,k,l)
```
**Comment:** It takes a few minutes to print all characters.
**Takeaways:** So meaning 4 characters is not a secure also.

Most of website and apps require atleast 8 characters
94^8 <-- estimated of 6,095,689,385,410,816 possible passwords.

It could take very long time that can run out many time and money to crack it.

So meaning if we could make longer and longer password that compose many letters, digits, and symbols. We raising the time for the hackers to crack our password and maybe they will surrender. And that means our password is secured.

But it has a downside also if the password is more longer and complex is, it can be hard to remember. So we need to balance it depends of the purpose of the account.

#### How to defend this attack?

#### National Institute of Standards and Technology (NIST)
is a organization from US that issues recommendation for consumers and company to secure their accounts effectively. 

#### Recommendations from NIST:
1. Memorized secrets SHALL be at least 8 characters in length <-- Memorized secrets they mean is password.
	**Comment**: To increase the time for the hackers to crack your password

2. Verifiers SHOULD permit subscriber-chosen memorized secrets at least 64 characters in length. All printing ASCII characters (refers to US English keyboard that includes character) as well as the space character SHOULD be acceptable in memorized secrets. Unicode characters SHOULD be accepted as well.
	Note: 
	- ASCII characters - refers to US English keyboard that includes letters, digits, and symbols
	- Unicode - Includes thing like emoji and other accented characters or symbols that might have in language that beyond in English.
		**Comment**: ACII code for password is good too avoid brute force attack, but by adding unicode can be hard to remember (Not recommended for password for simple accounts)

3. Verifiers SHALL compare the prospective secrets against a list that contains values known to be commonly-used, expected, or compromised
	- Password obtained from previous breach corpuses. <-- hacked database of companies
	- Dictionary words.
	- Repetitive or sequential characters (e.g 'aaaaaa', '1234abcd')
	- Context-specific words, such as the name of the service, the username, and derivatives thereof.
		**Comment**: to avoid brute force also

4. Memorized secrets verifiers SHALL NOT permit the subscriber to store a "hint" that is accessible to an unauthenticated claimant. Verifiers SHALL NOT prompt subscribers to use specific types of Information (e.g.. "What was the name of your first pet?") when choosing memorized secrets.
	**Comment**: by typing some secret answer for question, could lead to giving a hint for the hackers to known your password.

5. Verifiers SHOULD NOT require memorized secrets to be changed arbitraty (e.g periodically).
	**Comment**: By changing the password every day, week or month could forgotten easily.

6. Verifiers SHOULD implement a rate-limiting mechanism that effectively limits the number of failed authentication attemps that can be made on the subscriber's account.
	**Comment**: It is good for preventing brute force attack, when they can lock your devices or accounts in a few minutes or hours. So they can loose their interest. But it sometimes we are forget many things, so think first the usability of a device or account before creating a password on it.  


### Two-Factor Authentication (2FA)
- Generally known as Multi-Factor Authentication is a security method that requires two different forms of identification to access something.
- It a technology whereby in addition to having one factor that you use to login, usually your password, as is tradition, also have second or maybe more factors to additionaly has to use in order to login.

##### Three factors of Multi-Factor Authentication:
- **Knowledge** - is something that you known like your password
- **Possession** - something that physically you have, it might be a your own phone that has SMS support on it, that displays a short code that you may type in.
- **Inheritance** - something unique in you, generally describe as biometrics (fingerprints or face recognition)

Some companies, websites, or apps describe Two-step verification, where just typing two passwords, but two factor more technically refers to two or more types of fundamental different factors, that additionaly has to use in order to login.

### One-Time Password (OTP)
- It is one of the possesion factors that you might receive.
- It is one time use only, it is texted in you or sent via an app push notification, or sent in your key fob (a keychain that display a one-time password that companies used).

### Threat or Types of Attack that you must avoid
##### SIM Swapping
Also known as an authorized SIM change or SIM hijacking, is when a phone number is transferred without the owner's knowledge. The goal of a SIM swap is usually to gain financial control of the phone number and to take over the social media accounts. 

A Sim card, either a physical card or little chips that has unique identifier (phone number). It was associate that unique identifier into your device, But i so easy to trick a phone company that you been change your sim and i might convince them, that i swap my SIM card and get what file is already on that device. 

##### KEYLOGGING
also known as a malware on your device that logs all your keystrokes, And it sent it all on the software of the attacker. 

When the attacker is sees you typing that OTP that you receive, if they are fast and smart enough to log what you're typing, they type it before you, so they can pretend that they are you. But the OTP is one time used and always changing, so it is difficult to become first than the target.

**How to defend it?**
Just be conscious and paranoid on the device you've been used. Just put an extra time to improve and secure your device.

##### Credential Stuffing
 is a type of cyberattack where attackers use stolen username and password combinations (often obtained from previous data breaches) to try to gain unauthorized access to other online accounts. Since many people reuse the same credentials across multiple sites, this tactic can be effective.

if you want to avoid this attack, you have to use different credentials for different accounts. Username of email is yes, but the password is no.

##### Social Engineering
is a manipulation technique that exploits human psychology to deceive individuals to reveal their sensitive information, granting access, or performing actions that compromise security. Instead of hacking systems directly, attackers manipulate people to bypass security measures.

##### Phishing
is a type of cybersecurity attack that getting senstive information or credentials of an indivudual, by sending via email that contains a link. And also pretending a trusted website or application.

#### Machine-in-the-Middle Attacks
is a type of cyberattack when the attacker secretly intercepts and possibly alters communication between two parties, making it seem the two users are communicating directly. The attacker can steal sensitive data, manipulate messages, or impersonate one of the parties. By storing or recording the data that flow in that communication.


### Defenses that you can use:

#### Single Sign-On (SSO)
it refers to an ability to sign up for, or to login to one's website using an account that you already have in the options of that website or application. (log in with your facebook account or login with your email).

#### Password Managers 
is a software application or tool designed to securely store, manage, and generate passwords for your online accounts. It helps users maintain strong, unique passwords without having to remember all of them, enhancing both convenience and security.

When you creating an account on a certain website. Password manager can store your keystrokes or password and it can automatically type that password. And also password manager remember the URL of that website you have been created an account, so that if you encounter a phising attack, the password manager will ignore the auto type of your password and it may warn you  since their URL aren't match.

###### Third parties password managers:
- Apple iCloud Keychain
- Google Password Manager
- Microsoft Credential Manager
- .....

#### Passkeys
is a modern and secure way to authenticate users without relying on traditional passwords. They are part of an emerging standard aimed at making online authentication easier and safer by using **biometric data** or device-based cryptographic keys (your biometrics that stored in your device) instead of passwords.