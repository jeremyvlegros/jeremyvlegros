---
title                : "Information : `Pycharm` created a `doctest` absurd result"
date_of_creation     : "#date 2023-09-29 07:18 1695957483470493710 GMT"
date_of_modification : "#date 2023-11-15 12:20 1700036405502184887 GMT"
permalink            : "/post/1695957483470493710"
tags :
- "#posts"
- "#pycharm"
- "#python"
- "#doctest"
- "#configurations"
- "#ide"
- "#informations"
- "#computer"
- "#languages"
---

Got a failed __`doctest`__ test, this :

__`['/ROOT//a', '/ROOT//b', '/ROOT//c', '/ROOT//d', '/ROOT//e']`__

instead of :

__`['/ROOT/a', '/ROOT/b','/ROOT/c', '/ROOT/d', '/ROOT/e']`__

The problem was that the script directory wasn't set in the __`doctest`__ run configuration : 
- didn't stop the __`doctest`__ to run okay without it (until this)
- didn't stop the configuration to be saved
- didn't prompt errors 
- didn't prompt the Python console crash

After setting the directory, the __`doctest`__ test worked.