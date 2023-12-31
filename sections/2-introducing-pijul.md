<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3"-->

# Introducing Pijul

<https://pxhere.com/en/photo/652221> <!-- .element: class="attribution" -->

note: 
**Time Elapsed:** 3 min.

---

<!-- .slide: data-background="img/background/pijul.jpg" data-background-color="black" data-background-opacity="0.8"-->
## pi · jul <!-- .element: class="stroke" -->

<blockquote class="explanation">
    or <em>crotophaga sulcirostris</em>, a bird known to do collaborative nest building.
</blockquote>

<https://commons.wikimedia.org/wiki/File:Museo_de_la_Naturaleza_de_Cantabria_(208).jpg> <!-- .element: class="attribution" -->

note:

So let's address the name of this version control system first.
[explain the name]

---

## Features

* distributed version control <!-- .element: class="fragment fade-in-then-semi-out" -->
* simple, because of its basis on a sound theory of patches <!-- .element: class="fragment fade-in-then-semi-out" -->
* fast, because it aims to fix the Darcs performance issues <!-- .element: class="fragment fade-in-then-semi-out" -->
* interactive recording <!-- .element: class="fragment fade-in-then-semi-out" -->

<https://www.pijul.org> <!-- element: class="attribution" -->

note:
Darcs is a version control system from 2003 that is also patch-based.
However it didn't gain much popularity due to the fact that it was very slow.
It was also in the VCS popularity graph that I showed you earlier.

---

## Quick facts

<ul>
    <li>written in Rust
    <li>bootstrapped since April 2017
    <li>free code hosting at 
    <a href="https://nest.pijul.com">https://nest.pijul.com</a> 
</ul>

note:
Rust is one of the faster languages around, because it is a low-level language.
Its performance is comparable to that of C++.

Bootstrapped means that it is used for its own development.
So they 'eat their own dog food'.

Hosting is available on the Pijul Nest.

---

## Patch-oriented design

<ul>
    <li class="fragment fade-in-then-semi-out">A patch is an intuitive atomic unit of work.</li>
    <li class="fragment fade-in-then-semi-out">It focuses on <em>changes</em>, instead of <em>differences between snapshots</em> (i.e. Git commits).</li>
    <li class="fragment fade-in-then-semi-out">Applying or unapplying a patch <em>doesn't change</em> its identity.</li>
    <li class="fragment fade-in-then-semi-out">The end result of applying several patches is always the same, regardless of the order in which they were applied.</li>
    <li class="fragment fade-in-then-semi-out">Pijul keeps track of 'dependent patches'</li>
    <li class="fragment fade-in-then-semi-out">Rebase and merge don't exist, applying a patch (and its dependencies) is like <code>git cherry-pick</code>.</li>
</ul>

note:
Let's zoom in on this "patch-oriented design".

[walk through the bullet list]

[on **identity**]
By contrast, Git doesn't store any patches.
It stores snapshots of files and computes the differences when they are needed.
In Git each snapshot has its own identity. 

[on **order**]
Changes in Pijul can be applied in any order. This is great for cherry-picking: Pijul knows the changes that need to come along, and maintains the identity of the change after the cherry-pick. No need to manually find the commits to revert or pick.

[on **rebase** and **merges**]
One particular goal of Pijul is to model conflicts as normal states of collaboration, so that conflicts are resolved by normal changes, valid even for the same conflicts in any other context.

It is important to note that conflicts in Pijul always happen between changes, for example we might say that “change A conflicts with change B”. A conflict resolution is always a change. 

One of the main features of Pijul is that its internal representation of repositories fully models conflicts. Patches can even be applied to a conflicting repository, leaving the conflict resolution for later.

---

<!-- .slide: data-background="img/snapshot-vs-patch.png" data-background-color="#555" data-background-size="contain" data-visibility="hidden" -->

<https://www.katacoda.com/ysndr/scenarios/pijul/assets/comparison.png> <!-- .element class="attribution" -->

---

## If commits were bank transactions

<table>
        <tr>
            <th/>
            <th>snapshot</th>
            <th>patch</th>
        </tr>
        <tr class="fragment">
            <th align="right">initial balance</th>
            <td align="right"><code>100</code></td>
            <td align="right"><code>+100</code></td>
        </tr>  
        <tr class="fragment">
            <th align="right">salary</th>
            <td align="right"><code>400</code></td>
            <td align="right"><code>+300</code></td>
        </tr>
        <tr class="fragment">
            <th align="right">heating</th>
            <td align="right"><code>0</code></td>
            <td align="right"><code>-400</code></td>
        </tr>
</table>


note:

Snapshots store account balance, patches store deltas.
Which means patch order doesn't matter for the final result.
