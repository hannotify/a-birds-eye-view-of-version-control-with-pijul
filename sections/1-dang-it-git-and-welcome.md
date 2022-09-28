### A Birds-Eye View of Version Control with
# Pijul

<table>
    <tr>
        <td style="vertical-align: middle;">Hanno Embregts</td>
        <td style="text-align: right;"><img width="20%" data-src="img/icons/twitter-white.png" class="no-background"/></td>
        <td style="vertical-align: middle; padding: 0 0 0 0"><a href="https://www.twitter.com/hannotify">@hannotify</a></td>
    </tr>
</table>
<img data-src="img/logos/frontmania.png" width="25%" class="no-background"/>
<br/>

note:

*Voorbereidingen*:

* TODO
  
Hi, my name is Hanno. 
I work at Info Support as an IT consultant.
And this talk is about Pijul, a version control system that could perhaps be an alternative to Git.

---

<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3" data-auto-animate -->

# Yay,
# Git!

note:

Quick show of hands - who of you is currently using Git?
And who uses a different version control system?

There's a lot to like about Git:

* easy branching
* fast
* distributed nature (open-source development, work offline)

But do we like everything?
Do we like...

* amending commits? (or changing the message)
* committing to the wrong branch and having to fix it?
* running a diff when nothing happens?
* conflicts when merging or rebasing?
* getting the same conflicts multiple times when dealing with long-lived branches?
* fresh clones because the repo is too messed up to repair?
* heated team debates on rebase vs. merge?

---

<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3" data-auto-animate -->

# Dang it,
# Git!

[dangitgit.com](https://dangitgit.com) <!-- .element: class="fragment" -->

note:

Some days it's more like "Dang it, Git!" instead of "Yay, Git!"
There's a website for that, by the way. (slide)

To summarise, I don't always like:

* the documentation 
  * features we often need are buried in some obscure command-line argument
* Git's snapshot-based approach when changes travel
  * rebasing or cherry-picking changes commit identities
  * there's no way to fix a commit once and for all (`git rerere`)

But, you know, as long as there isn't something better available, it'll probably be fine, right?

---

# Teaching a Git course

<!-- .slide: data-background="img/background/version-control-timeline.png" data-background-size="contain" data-background-color="white" -->

<http://blog.plasticscm.com/2010/11/version-control-timeline.html> <!-- .element: class="attribution" -->

note:

In fact, this is what I always say when teaching people about Git.
This chart is from the Git course I regularly teach at Info Support.
Sure enough, after 2005-2006, nothing seems to have happened in version control world.

In fact, I never even gave it a second thought, until a student asked me about it at the end of a particular course day.
She said: "I like Git well enough, but what is new and cool in version control?"

And because I didn't know the answer to her question, I started researching it and found a few newer version control systems.
They were called Fossil and Pijul.
This talk is about Pijul, and how its approach is different from Git's approach.