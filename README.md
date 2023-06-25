
# Table of Contents

1.  [Introduction](#org967b2f2)
2.  [My story](#org0d053b1)
3.  [Results](#org17922d3)
4.  [The main challenge](#orgbaa395b)
5.  [Lessons learned](#org46112ed)
6.  [About me](#org14025f5)


<a id="org967b2f2"></a>

# Introduction

Star Wars Movie Guide helps Star Wars fans or anyone interested in the Star Wars universe
access key information about the films, characters, and other related details in an
easy-to-use and visually appealing way. I am the sole member but sought help from peers
when I ws stuck on a problem. I wanted to focus on two aspects to address the problem: creating an
awesome and user-friendly journey to the marvelous universe that is both web and mobile-friendly,
and identifying a rich and reliable API. As the sole member, I worked on all aspects of the
project including development, design, and project management. First, as a developer, I was responsible
for building the backend and frontend components and implementing all features of the app. 
Second, as a designer, I created a visually appealing and user-friendly interface for the app.
Third, as the project manager, I carefully planned and organized the project, set 
goals and timelines, as well as ensuring the project was completed on time (Trello board
was a huge help on this!).


<a id="org0d053b1"></a>

# My story

Form weird beings to droids and clones, I was immersed into a new and strange
world when I first watched Attack of the Clones. The film happened to be the first
Star Wars film I ever watched and I was hooked. Of course I made sure I watched
all of them and in the right order!. I then had an idea that probably one day
I would create an app where not only I, but anyone else could easily access all
the information related to Star Wars, and especially films. Thanks to [ALX](https://www.alxafrica.com/), I was
finally able to implement it.


<a id="org17922d3"></a>

# Results

For the front-end, I utilized jquery to generate dynamic content in combination
with HTML and CSS. I decided not use other frontend frameworks because I wanted to
cement my understanding of Javascript and JQeury. On the backend side, I used
Flask to manage my application, Redis for caching,  Gunicorn for a
production-ready app, and Nginx for serving my pages.
I managed to implement a couple of features notably: Oauth via Google, a responsive
app, and a solid backend.


<a id="orgbaa395b"></a>

# The main challenge

I first thought of using a simple logging and signup page for my app. By simple,
I mean a user will be required to enter his/her email address and password to access
the app as a member. I went along with the idea and actually implemented it. However,
I felt that it was lacking something, something to make it and my app feel a bit more alive.
And that is when I remembered how easy it felt when logging sites such as Slack and others
that offer different options for signing in. I decided at that moment to restructure my
form to incorporate Oauth via Google.

A search in my browser quickly took me to [this](https://developers.google.com/identity/gsi/web/guides/overview) Google's developer's site that has a rich documentation
and how To's for its API's and libraries. I learned how to create an OAuth consent screen and credentials to use
for my project by obtaining my client ID and configuring the consent screen. I loaded the client
library in the logging HTML's head tag, generated the integration code, and displayed the Google
button in the form. Then I ran my app and I was so sure it would fire up as expected. But Alas,
nothing, well not completely nothing since the Google button was visible. The problem
was ensring that when the button was clicked, it would load a new window with sessioned
Google emails that a user could select for signing in. Mine would load a new **empty** window.

The browser console logged this error: "Not a valid origin for the client:"
I rechecked my client ID once more to ensure I was not supplying an incorrect ID. The ID
was not the culprit. A similar [stackoverflow](https://stackoverflow.com/questions/42566296/google-api-authentication-not-valid-origin-for-the-client) issue suggested origins verification and I
carefully read [this article](https://medium.com/@thomashellstrom/use-google-as-login-in-your-web-app-with-oauth2-352f6c7f10e6) on how to enable Google Oauth. That is when I noticed my error:
since I was using authorized JavaScript origins, I had put 127.0.0.1:5003 and localhost as my origins.
See, both 127.0.0.1 and localhost refer to the *same* thing and I assumed that would be the
case. However, the solution required I use the alias(localhost) that resolves to all loopback IP addresses.
I changed the IP to the alias and ensured I added the port 5003 since my app running on a Gunicorn service
on port 5003. As soon as I refreshed the page, boom! It worked. I was so happy.


<a id="org46112ed"></a>

# Lessons learned

As a result of this project, I have taken a technical interest in how apps are developed and deployed.
From caching results in-memory using Redis to signing users via Google's Oauth, I have gained
rich skills regarding Software Engineering. One thing I might do different is
to use the Authlib library to incorporate more than one authenticator.
As an engineer, I have learned that I don't give up, I maintain focus, and I don't let
hard things pass by but confront them.
Additionally, I can confirm that ever since I started using Emacs, my life as a
Software Engineer has gotten easier because Emacs is a poweful editor and a minefield
of incredible keybindings for faster typing, file conversion, enabling links, among others. 
I actually use orgmode to generate my README's!. I was saved from the hell of exiting vim :).


<a id="org14025f5"></a>

# About me

Francis is a Software Engineer trained by the excellent team at ALX. He likes solving both simple 
and complex challenges, hiking, and having a cup of sugarles coffee.

-   [Github link for the project](https://github.com/fk2019/Star_Wars_Movie_Guide)
-   [Deployed page](http://34.232.69.25/)
-   [Landing page](https://fk2019.github.io/home/)
-   [LinkedIn](https://www.linkedin.com/in/francis-kamau-792953252/)

