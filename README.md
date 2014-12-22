# [Quickjack](http://samy.pl/quickjack)

**Quickjack** is an intuitive, point-and-click tool for performing advanced and covert clickjacking and frame slicing attacks.

Use the Quickjack tool directly at [http://samy.pl/quickjack/quickjack.html](http://samy.pl/quickjack/quickjack.html)

by [@SamyKamkar](https://twitter.com/samykamkar) // <code@samy.pl> // <http://samy.pl> // Dec 22, 2014

Code available on [github](https://github.com/samyk/quickjack)

<a href="http://www.youtube.com/watch?feature=player_embedded&v=LpEvTSaSHwk
" target="_blank"><img src="http://img.youtube.com/vi/LpEvTSaSHwk/0.jpg" alt="Quickjack" width="640" height="480" border="10" /></a>


------

# Overview

Quickjack allows you to easily perform [clickjacking](http://www.sectheory.com/clickjacking.htm), or steal "clicks" from users on many websites, forcing the user to unknowingly click buttons or links (e.g., the Facebook Like button) using their own cookies. By placing the auto-generated code on any site, you can obtain thousands of clicks quickly from different users, or perform targeted attacks by luring a victim to a specific URL. It also allows you to deceive a user into believing you have information on them that you don't, as well as coerce a user into providing information to you without even knowing it.

In this demonstration, we'll both steal Facebook likes without a user knowing, as well as show a user's [imgur](http://imgur.com) name on our own site.

Quickjack supports not only easy point-and-click generation of code, but also the underlying iframe follows the user's mouse movement around the page wherever they go, hides the clickjacking frame, and even performs a method of determining when you've obtained the user's click in order to then remove clickjacking from the page so the user can actually perform the click they meant to execute.

Quickjack also includes a frame slicing tool which allows you to capture a small section of a page to display to them, coercing them to believe you have such information on them. An example would be to slice a section of a website which normally contains the user's name, then place that frame slice on your own site, making it appear that you know their name.

You can even use frame slicing to obtain information from the user, such as slicing differnet characters of the user's name on a site, rearranging them and adding other letters and numbers, turning it into a captcha, and when the user enters the captcha, they're just entering an anagram of their name (and other characters which you remove) and can determine their name!

In this project, we'll learn how Quickjack performs these methods and how clickjacking and frame slicing work, as well as some of the more advanced techniques presented in the Quickjack tool which allow more potent clickjacking to occur, as well as see real demonstrations on sites such as Facebook.

Quickjack is originally based off of a "cake slicing" app which is no longer online.

Clickjacking was initially discovered by the amazing [Robert Hansen](https://twitter.com/rsnake/) and [Jeremiah Grossman](https://twitter.com/jeremiahg/)

![http://samy.pl/quickjack/qj1.png](http://samy.pl/quickjack/qj1.png)

---

![http://samy.pl/quickjack/qj2.png](http://samy.pl/quickjack/qj2.png)



------

# [Use Quickjack](http://samy.pl/quickjack/quickjack.html)

Use the Quickjack tool at [http://samy.pl/quickjack/quickjack.html](http://samy.pl/quickjack/quickjack.html)

### Source
You can simply use Quickjack [online here](http://samy.pl/quickjack/quickjack.html), or acquire the source code for yourself from my github: <https://github.com/samyk/quickjack>

-----

# Stealing Facebook Likes
You can see how we **create** the clickjacking attack for Facebook **in seconds** in [the video](https://www.youtube.com/watch?v=LpEvTSaSHwk).

See the HTML demo (which likely won't last) here: [http://samy.pl/quickjack/pwned.html](http://samy.pl/quickjack/pwned.html)
which clickjacks this page:
[http://samy.pl/quickjack/fb.html](http://samy.pl/quickjack/fb.html)
which contains an iframe to Facebook!

-----

# Clickjacking

[Clickjacking](http://www.sectheory.com/clickjacking.htm) was initially discovered by the amazing [Robert Hansen](https://twitter.com/rsnake/) and [Jeremiah Grossman](https://twitter.com/jeremiahg/).

[Quickjack](http://samy.pl/quickjack/quickjack.html) makes clickjacking fun and easy! It also adds a few advanced features that make clickjacking potent and covert.

### Persistence / Mouse Tracking

By tracking the mouse, Quickjack consistently keeps the hidden clickjacking iframe directly underneath the user's mouse pointer. This ensures the moment they make a click on the page, their click has been jacked.

### Click Detection

Traditionally, the person performing the clickjacking attack cannot detect when the clickjack occurred due to cross-domain policy, however we get around this by ensuring focus is in the parent window, the window we control. Although we can't detect a click or focus in the clickjacking frame, we **can** detect the loss of focus, or blur, within our parent window, the window we control!

This means as soon as the user clicks inside the iframe (without knowing), our window will blur, causing us to trigger a special call. Our call hides the clickjacking iframe further, ensuring the **next** click the user performs actually happens on the page they're on! Awesome!

### Referral Scrubbing

Referral scrubbing is the method of removing your HTTP referrer so the target domain cannot discover where a clickjacking attack originated from. It is optionally allowed by using multiple redirects, or optionally by switching in and out of HTTPS.

### Preventing Frame Breakout/Frame Busting

We use some older methods of frame busting **evasion** to prevent sites from using frame busting/breakouts in some browsers.

-----

# Frame Slicing

We use fun and intuitive frame slicing to allow you to slice a frame out of any page. Here's an actual frame slice, not an image, from [imgur](http://imgur.com).


-----

# Preventing Quickjacking

You can prevent quickjacking, clickjacking or frame slicing by using the X-Frame-Options HTTP header, or following these other great instructions from [OWASP](https://www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet).

-----

# Questions?

Feel free to contact me with any questions!

Follow [@SamyKamkar](https://twitter.com/samykamkar) on Twitter!

You can see more of my projects at <http://samy.pl> or contact me at <code@samy.pl>.


------
