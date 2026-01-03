#coffee #coffee/dial-in 

```dataview
TABLE
process, variety, origin, taste-notes
FROM
"coffee"
WHERE
process = "Washed" OR contains(process, "Natural")
SORT
file.mday  desc
```

# Ferments
```dataview
TABLE
process, variety, origin, taste-notes
FROM
"coffee"
WHERE
icontains(process, "ferment")
OR icontains(process, "anaerobic")
OR icontains(process, "anoxic")
OR icontains(process, "culture")
OR icontains(process, "macerat")
OR icontains(process, "mosto")
OR icontains(process, "inoc")
SORT
file.mday  desc
```

# Espresso
```dataview
TABLE
process, variety, ratio, grind, taste-notes
FROM
#coffee/dial-in/espresso and "coffee"
SORT
process desc, file.cday  desc
```