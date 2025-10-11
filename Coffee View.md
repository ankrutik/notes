#coffee #coffee/dial-in 

```dataview
TABLE
process, variety, origin, taste-notes
FROM
"coffee"
WHERE
process = "Washed" OR process = "Natural"
SORT
process desc, file.cday  desc
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
process desc, file.cday  desc
```
