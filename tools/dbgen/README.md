# Joindin Datagenerator 

tl;dr
=====
  From the (linux) commandline:
  $ php generate.php > ji-data.sql

  It will output information on STDERR so you can see errors and some more information.


Main information
================
The generator will create a SQL file that can be used in your joind.in database. It will generate the following:
 - Users - real looking usernames, email-addresses, password, twitter accounts etc
 - Events - real long/lat, generated names, event start/endings, multiday events, cfp's etc
 - Tracks & talks
 - Comments on both events/talks (anonymous, private, from different sources etc)
 - Letting users attend events

Mind that you only need to change settings inside generate.php (the constants).


Usernames and passwords
=======================
All the usernames and passwords can be deducted from the full name of the user. For instance:

    Full name: Joseph Hale
    Username:  jhale                 (first letter firstname + lastname)
    Email:     j.hale@example.org    (first letter, a dot, last name @example.org)
    Password:  jhalepass             (username + the text "pass")


Tweaking JoDa
=============
You can tweak the data in two different ways:
  - Change the amount of data
  - Change the type of data

The amount of data is taken care of by the COUNT_* constants found in generate.php. I've created 4 different "sets"
that should be ok for most people: light, medium, heavy and massive. I strongly suggest not to use the "massive" set,
since it will make your system run out of memory. This is due to the current inefficient way of caching data. All other
sets should be fine. The current default set is "medium".

You can define most values through constant defines found in generate.php, for instance:
 - Percentage of events that have CFP
 - Percentage of anonymous comments
 - Percentage of users that have twitter account
 - Percentage of users that are admin
 - Percentage of talks that have multiple speakers


Future
======
There is still lots to do, but the most important ones:
 - Adding talks to tracks
 - Getting the correct timezone
 - making sure events that are in the future do not have comments on talks / events
 - multiple attending of events by users are possible
 - set the correct ordering of comments (earliest comments should be added to the database first).
 - Adding pending events (not implemented yet)
 - CFP must be added
 - Getting the correct timezone
 - multiple attending of events by users are possible
 - set the correct ordering of comments (earliest comments should be added to the database first).
 - The caching must be optimized. The system takes too much memory and takes too long to run on the "massive" settings.
