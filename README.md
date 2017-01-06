# obistools

Tools for data enhancement and quality control.

## Check required fields

```R
data <- data.frame(
  occurrenceID = c("1", "2", "3"),
  scientificName = c("Abra alba", NA, ""),
  locality = c("North Sea", "English Channel", "Flemish Banks"),
  minimumDepthInMeters = c("10", "", "5")
)

check_fields(data)
```

```
             field level                                       message row
1        eventDate error           Required field eventDate is missing  NA
2 decimalLongitude error    Required field decimalLongitude is missing  NA
3  decimalLatitude error     Required field decimalLatitude is missing  NA
4 scientificNameID error    Required field scientificNameID is missing  NA
5 occurrenceStatus error    Required field occurrenceStatus is missing  NA
6    basisOfRecord error       Required field basisOfRecord is missing  NA
7   scientificName error Empty value for required field scientificName   2
8   scientificName error Empty value for required field scientificName   3
```

## Taxon matching

```R
names <- c("Abra alva", "Buccinum fusiforme", "Buccinum fusiforme", "Buccinum fusiforme", "ljkf hlqsdkf")
match_taxa(names)
```
```
Proceed to resolve names (y/n/p)? y
  AphiaID     scientificname      authority     status match_type
1  531014 Buccinum fusiforme   Kiener, 1834 unaccepted      exact
2  510389 Buccinum fusiforme Broderip, 1830 unaccepted      exact
Multiple matches, pick a number or leave empty to skip: 2
        scientificName                          scientificNameID match_type
1            Abra alba urn:lsid:marinespecies.org:taxname:141433     near_1
2   Buccinum fusiforme urn:lsid:marinespecies.org:taxname:510389      exact
2.1 Buccinum fusiforme urn:lsid:marinespecies.org:taxname:510389      exact
2.2 Buccinum fusiforme urn:lsid:marinespecies.org:taxname:510389      exact
3                 <NA>                                      <NA>       <NA>```