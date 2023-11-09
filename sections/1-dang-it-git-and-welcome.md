### A Birds-Eye View of Version Control with
# Pijul

<table>
    <tr>
        <td style="text-align: right; vertical-align: middle;" width="45.3%">Hanno Embregts</td>
        <td style="text-align: left; padding: 0 0 0 0; vertical-align: middle;"><img width="16%" data-src="img/logos/ace-associate-spade.png" class="no-background" style="margin-top: 30px; vertical-align: middle;"/><img width="22%" data-src="img/logos/java-champion.png" class="no-background" style="margin-top: 30px; vertical-align: middle;"/></td>
        <td style="text-align: right;"><img width="45%" data-src="img/icons/twitter-white.png" class="no-background" style="margin-top: 35px"/></td>
        <td style="vertical-align: middle; padding: 0 0 0 0"><a href="https://www.twitter.com/hannotify">@hannotify</a></td>
    </tr>
</table>
<img data-src="img/logos/jfall.png" width="20%" class="no-background"/>
<br/>

note:

*Voorbereidingen*:

* Verbind Spotlight met de Logitech-software.
* Eerste scherm:
  * Speaker notes
  * Terminal:
    * Tab met `mirror`
    * Tab met de slides draaiend
    * Tab voor pijul - verbonden met Docker-container via `/bin/bash`
* Tweede scherm:
  * Slides
* Telefoon met de demostappen erop
* Reset de timer in de speaker notes
  
Hi, my name is Hanno. 
I work at Info Support as an IT consultant.
I am both an Oracle ACE and a Java Champion.
I am @hannotify on most social networks - give me a follow.

This talk is about Pijul, a version control system that could perhaps become an alternative to Git.

---

<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3" data-auto-animate -->

# Yay,
# Git!

<https://pxhere.com/en/photo/652221> <!-- .element: class="attribution" -->

note:
Quick show of hands - who of you is currently using Git?
And who uses a different version control system?

Well, that's understandable!
Because there's a lot to like about Git:

* easy branching
* distributed nature (open-source development, work offline)
* fast

But do we like everything?
Do we like... for example...

* amending commits? (or changing the message)
* committing to the wrong branch and having to fix it?
* running a diff when nothing happens? (`--staged`)
* conflicts when merging or rebasing?
* getting the same conflicts over and over again when we need long-lived branches?
* having to do a fresh clone because the repo is too messed up to repair?
* heated team debates on rebase vs. merge?

Well... not particularly!

---

<!-- .slide: data-background="img/background/git-clunky-interface-tweet.png" data-background-color="black" data-background-size="80%" -->

---

<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3" data-auto-animate -->

# Yay,
# Git!

<https://pxhere.com/en/photo/652221> <!-- .element: class="attribution" -->

---

<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3" data-auto-animate -->

# Dang it,
# Git!

<div class="fragment">
<a href="https://dangitgit.com">dangitgit.com</a><br/><small>(by Katie Sylor-Miller)</small>
</div>

<div class="fragment">
<a href="https://git-man-page-generator.lokaltog.net/">git-man-page-generator.lokaltog.net</a><br/><small>(by Kim Silkebækken)</small>
</div>

<https://pxhere.com/en/photo/652221> <!-- .element: class="attribution" -->

note:
Some days it's more like "Dang it, Git!" instead of "Yay, Git!"
There's a website for that, by the way. (slide)

To summarise, I don't always like:

* the documentation 
  * features we often need are buried in some obscure command-line argument
* Git's snapshot-based approach when changes travel
  * rebasing or cherry-picking changes commit identities
  * there's no way to fix a conflict once and for all (`git rerere`)
* Git's many (many!) internal operations that are available to every user, confusing them even more 
* (slide) The Git Manpage Generator illustates this point nicely :-)

But, you know, as long as there isn't something better available, it'll probably be fine, right?

---

<!-- .slide: data-background="img/background/version-control-timeline.png" data-background-size="contain" data-background-color="white" -->

<http://blog.plasticscm.com/2010/11/version-control-timeline.html> <!-- .element: class="attribution" -->

note:

In fact, this is what I always say when teaching people about Git.
This chart is from the Git course I regularly teach at Info Support.
Sure enough, after 2005, nothing seems to have happened in version control world.

In fact, I never even gave it a second thought, until a student asked me about it at the end of a particular course day.
She said: "I like Git well enough, but what is new and cool in version control?"

And because I didn't know the answer to her question, I started researching it and found a newer version control systems.
It was called Pijul.
This talk is about Pijul, and how it's different from Git.