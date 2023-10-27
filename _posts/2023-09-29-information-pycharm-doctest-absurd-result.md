---
title                : "information > `Pycharm` > `doctest` > absurd result"
date_of_creation     : "#date 2023-09-29 07:18 1695957483470493710 GMT"
date_of_modification : null
permalink            : "/post/1695957483470493710"
tags :
- "#posts"
- "#pycharm"
- "#doctest"
- "#configurations"
---

Got a failed `doctest` test :

`['/ROOT//a', '/ROOT//b', '/ROOT//c', '/ROOT//d', '/ROOT//e']` instead of `['/ROOT/a', '/ROOT/b','/ROOT/c', '/ROOT/d', '/ROOT/e']`

The problem was that the script directory wasn't set in the `doctest` run configuration : 
- didn't stop the `doctest` to run okay without it (until this)
- didn't stop the configuration to be saved
- didn't prompt errors 
- didn't prompt the Python console crash

After setting the directory, the `doctest` test worked.