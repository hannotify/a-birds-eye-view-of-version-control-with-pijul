<!-- .slide: data-background="img/background/usb-sticks.jpg" data-background-color="black" data-background-opacity="0.3"-->

# Demo

---

## Demo

* Up and running
* Recording patches
* Reordering patches

note:

### Up and running

    pijul init demo

### Recording patches

    vi README.md
    > This repo contains beers and movies that are important to me.
    pijul add Readme.md
    pijul record -m "Initial patch"

    #Identities
    pijul key generate hanno

    mkdir directory
    pijul add directory
    pijul record

### Reordering patches

    pijul init beers-and-movies
    cd beers-and-movies
    touch README.md
    pijul add README.md
    pijul record -m "Initial patch"
    pijul fork next-week
    pijul channel
    pijul channel switch next-week
    pijul channel switch main
    vi movies.txt
    pijul add movies.txt
    pijul record -m "Watched a movie"
    vi beers.txt
    pijul add beers.txt
    pijul record -m "Drank a beer"
    vi movies.txt
    pijul add * 
    pijul record -m "Watched another movie"
    pijul log
    // copy the hashes somewhere, or duplicate the terminal tab
    pijul channel switch next-week
    pijul apply <hash> (beer)
    ls
    pijul log
    pijul apply <hash> (another movie)
    // notice the dependent patch!
    ls
    pijul log

    pijul unrecord --reset <hash> (movie)
    pijul unrecord --reset <hash> (another movie)

---

## Pijul's current status

<ul>
    <li>v1.0-beta</li>
    <small><a href="https://pijul.org/posts/2022-01-08-beta">https://pijul.org/posts/2022-01-08-beta</a></small>
</ul>

note:

Pijul is now feature-complete and it will be backwards-compatible from now on.
However, it is still in beta.

Overall, I think Pijul is quite promising, but it needs some work in its current beta phase.
So some of its popularity will be depending on how they will get stable versions later this year.
