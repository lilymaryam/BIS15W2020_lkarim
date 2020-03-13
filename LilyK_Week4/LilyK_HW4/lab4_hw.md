---
title: "Lab 4 Homework"
author: "Lily Karim"
date: "2/7/2020"
output:
  html_document: 
    keep_md: yes
    theme: spacelab
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove any `#` for included code chunks to run.  

## Load the tidyverse

```r
library(tidyverse)
```

For this assignment we are going to work with a large dataset from the [United Nations Food and Agriculture Organization](http://www.fao.org/about/en/) on world fisheries. First, load the data.  

1. Load the data `FAO_1950to2012_111914.csv` as a new object titled `fisheries`.\


```r
getwd()
```

```
## [1] "/Users/lilykarim/Desktop/BIS15W2020_lkarim/LilyK_Week4/LilyK_HW4"
```


```r
fisheries <- readr::read_csv("data/FAO_1950to2012_111914.csv")
```

```
## Parsed with column specification:
## cols(
##   .default = col_character(),
##   `ISSCAAP group#` = col_double(),
##   `FAO major fishing area` = col_double()
## )
```

```
## See spec(...) for full column specifications.
```



2. What are the names of the columns? Do you see any potential problems with the column names?

```r
colnames(fisheries)
```

```
##  [1] "Country"                 "Common name"            
##  [3] "ISSCAAP group#"          "ISSCAAP taxonomic group"
##  [5] "ASFIS species#"          "ASFIS species name"     
##  [7] "FAO major fishing area"  "Measure"                
##  [9] "1950"                    "1951"                   
## [11] "1952"                    "1953"                   
## [13] "1954"                    "1955"                   
## [15] "1956"                    "1957"                   
## [17] "1958"                    "1959"                   
## [19] "1960"                    "1961"                   
## [21] "1962"                    "1963"                   
## [23] "1964"                    "1965"                   
## [25] "1966"                    "1967"                   
## [27] "1968"                    "1969"                   
## [29] "1970"                    "1971"                   
## [31] "1972"                    "1973"                   
## [33] "1974"                    "1975"                   
## [35] "1976"                    "1977"                   
## [37] "1978"                    "1979"                   
## [39] "1980"                    "1981"                   
## [41] "1982"                    "1983"                   
## [43] "1984"                    "1985"                   
## [45] "1986"                    "1987"                   
## [47] "1988"                    "1989"                   
## [49] "1990"                    "1991"                   
## [51] "1992"                    "1993"                   
## [53] "1994"                    "1995"                   
## [55] "1996"                    "1997"                   
## [57] "1998"                    "1999"                   
## [59] "2000"                    "2001"                   
## [61] "2002"                    "2003"                   
## [63] "2004"                    "2005"                   
## [65] "2006"                    "2007"                   
## [67] "2008"                    "2009"                   
## [69] "2010"                    "2011"                   
## [71] "2012"
```



3. What is the structure of the data? Show the classes of each variable.

```r
str(fisheries)
```

```
## Classes 'spec_tbl_df', 'tbl_df', 'tbl' and 'data.frame':	17692 obs. of  71 variables:
##  $ Country                : chr  "Albania" "Albania" "Albania" "Albania" ...
##  $ Common name            : chr  "Angelsharks, sand devils nei" "Atlantic bonito" "Barracudas nei" "Blue and red shrimp" ...
##  $ ISSCAAP group#         : num  38 36 37 45 32 37 33 45 38 57 ...
##  $ ISSCAAP taxonomic group: chr  "Sharks, rays, chimaeras" "Tunas, bonitos, billfishes" "Miscellaneous pelagic fishes" "Shrimps, prawns" ...
##  $ ASFIS species#         : chr  "10903XXXXX" "1750100101" "17710001XX" "2280203101" ...
##  $ ASFIS species name     : chr  "Squatinidae" "Sarda sarda" "Sphyraena spp" "Aristeus antennatus" ...
##  $ FAO major fishing area : num  37 37 37 37 37 37 37 37 37 37 ...
##  $ Measure                : chr  "Quantity (tonnes)" "Quantity (tonnes)" "Quantity (tonnes)" "Quantity (tonnes)" ...
##  $ 1950                   : chr  NA NA NA NA ...
##  $ 1951                   : chr  NA NA NA NA ...
##  $ 1952                   : chr  NA NA NA NA ...
##  $ 1953                   : chr  NA NA NA NA ...
##  $ 1954                   : chr  NA NA NA NA ...
##  $ 1955                   : chr  NA NA NA NA ...
##  $ 1956                   : chr  NA NA NA NA ...
##  $ 1957                   : chr  NA NA NA NA ...
##  $ 1958                   : chr  NA NA NA NA ...
##  $ 1959                   : chr  NA NA NA NA ...
##  $ 1960                   : chr  NA NA NA NA ...
##  $ 1961                   : chr  NA NA NA NA ...
##  $ 1962                   : chr  NA NA NA NA ...
##  $ 1963                   : chr  NA NA NA NA ...
##  $ 1964                   : chr  NA NA NA NA ...
##  $ 1965                   : chr  NA NA NA NA ...
##  $ 1966                   : chr  NA NA NA NA ...
##  $ 1967                   : chr  NA NA NA NA ...
##  $ 1968                   : chr  NA NA NA NA ...
##  $ 1969                   : chr  NA NA NA NA ...
##  $ 1970                   : chr  NA NA NA NA ...
##  $ 1971                   : chr  NA NA NA NA ...
##  $ 1972                   : chr  NA NA NA NA ...
##  $ 1973                   : chr  NA NA NA NA ...
##  $ 1974                   : chr  NA NA NA NA ...
##  $ 1975                   : chr  NA NA NA NA ...
##  $ 1976                   : chr  NA NA NA NA ...
##  $ 1977                   : chr  NA NA NA NA ...
##  $ 1978                   : chr  NA NA NA NA ...
##  $ 1979                   : chr  NA NA NA NA ...
##  $ 1980                   : chr  NA NA NA NA ...
##  $ 1981                   : chr  NA NA NA NA ...
##  $ 1982                   : chr  NA NA NA NA ...
##  $ 1983                   : chr  NA NA NA NA ...
##  $ 1984                   : chr  NA NA NA NA ...
##  $ 1985                   : chr  NA NA NA NA ...
##  $ 1986                   : chr  NA NA NA NA ...
##  $ 1987                   : chr  NA NA NA NA ...
##  $ 1988                   : chr  NA NA NA NA ...
##  $ 1989                   : chr  NA NA NA NA ...
##  $ 1990                   : chr  NA NA NA NA ...
##  $ 1991                   : chr  NA NA NA NA ...
##  $ 1992                   : chr  NA NA NA NA ...
##  $ 1993                   : chr  NA NA NA NA ...
##  $ 1994                   : chr  NA NA NA NA ...
##  $ 1995                   : chr  "0 0" "1" NA "0 0" ...
##  $ 1996                   : chr  "53" "2" NA "3" ...
##  $ 1997                   : chr  "20" "0 0" NA "0 0" ...
##  $ 1998                   : chr  "31" "12" NA NA ...
##  $ 1999                   : chr  "30" "30" NA NA ...
##  $ 2000                   : chr  "30" "25" "2" NA ...
##  $ 2001                   : chr  "16" "30" NA NA ...
##  $ 2002                   : chr  "79" "24" NA "34" ...
##  $ 2003                   : chr  "1" "4" NA "22" ...
##  $ 2004                   : chr  "4" "2" "2" "15" ...
##  $ 2005                   : chr  "68" "23" "4" "12" ...
##  $ 2006                   : chr  "55" "30" "7" "18" ...
##  $ 2007                   : chr  "12" "19" NA NA ...
##  $ 2008                   : chr  "23" "27" NA NA ...
##  $ 2009                   : chr  "14" "21" NA NA ...
##  $ 2010                   : chr  "78" "23" "7" NA ...
##  $ 2011                   : chr  "12" "12" NA NA ...
##  $ 2012                   : chr  "5" "5" NA NA ...
##  - attr(*, "spec")=
##   .. cols(
##   ..   Country = col_character(),
##   ..   `Common name` = col_character(),
##   ..   `ISSCAAP group#` = col_double(),
##   ..   `ISSCAAP taxonomic group` = col_character(),
##   ..   `ASFIS species#` = col_character(),
##   ..   `ASFIS species name` = col_character(),
##   ..   `FAO major fishing area` = col_double(),
##   ..   Measure = col_character(),
##   ..   `1950` = col_character(),
##   ..   `1951` = col_character(),
##   ..   `1952` = col_character(),
##   ..   `1953` = col_character(),
##   ..   `1954` = col_character(),
##   ..   `1955` = col_character(),
##   ..   `1956` = col_character(),
##   ..   `1957` = col_character(),
##   ..   `1958` = col_character(),
##   ..   `1959` = col_character(),
##   ..   `1960` = col_character(),
##   ..   `1961` = col_character(),
##   ..   `1962` = col_character(),
##   ..   `1963` = col_character(),
##   ..   `1964` = col_character(),
##   ..   `1965` = col_character(),
##   ..   `1966` = col_character(),
##   ..   `1967` = col_character(),
##   ..   `1968` = col_character(),
##   ..   `1969` = col_character(),
##   ..   `1970` = col_character(),
##   ..   `1971` = col_character(),
##   ..   `1972` = col_character(),
##   ..   `1973` = col_character(),
##   ..   `1974` = col_character(),
##   ..   `1975` = col_character(),
##   ..   `1976` = col_character(),
##   ..   `1977` = col_character(),
##   ..   `1978` = col_character(),
##   ..   `1979` = col_character(),
##   ..   `1980` = col_character(),
##   ..   `1981` = col_character(),
##   ..   `1982` = col_character(),
##   ..   `1983` = col_character(),
##   ..   `1984` = col_character(),
##   ..   `1985` = col_character(),
##   ..   `1986` = col_character(),
##   ..   `1987` = col_character(),
##   ..   `1988` = col_character(),
##   ..   `1989` = col_character(),
##   ..   `1990` = col_character(),
##   ..   `1991` = col_character(),
##   ..   `1992` = col_character(),
##   ..   `1993` = col_character(),
##   ..   `1994` = col_character(),
##   ..   `1995` = col_character(),
##   ..   `1996` = col_character(),
##   ..   `1997` = col_character(),
##   ..   `1998` = col_character(),
##   ..   `1999` = col_character(),
##   ..   `2000` = col_character(),
##   ..   `2001` = col_character(),
##   ..   `2002` = col_character(),
##   ..   `2003` = col_character(),
##   ..   `2004` = col_character(),
##   ..   `2005` = col_character(),
##   ..   `2006` = col_character(),
##   ..   `2007` = col_character(),
##   ..   `2008` = col_character(),
##   ..   `2009` = col_character(),
##   ..   `2010` = col_character(),
##   ..   `2011` = col_character(),
##   ..   `2012` = col_character()
##   .. )
```



4. Think about the classes. Will any present problems? Make any changes you think are necessary below.

```r
fisheries <- fisheries %>% 
  mutate_at(vars(9:71), as.numeric, na.rm = TRUE) %>% 
  mutate_if(is.character, as.factor)
```

```
## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion

## Warning: NAs introduced by coercion
```

```r
sapply(fisheries, class)
```

```
##                 Country             Common name          ISSCAAP group# 
##                "factor"                "factor"               "numeric" 
## ISSCAAP taxonomic group          ASFIS species#      ASFIS species name 
##                "factor"                "factor"                "factor" 
##  FAO major fishing area                 Measure                    1950 
##               "numeric"                "factor"               "numeric" 
##                    1951                    1952                    1953 
##               "numeric"               "numeric"               "numeric" 
##                    1954                    1955                    1956 
##               "numeric"               "numeric"               "numeric" 
##                    1957                    1958                    1959 
##               "numeric"               "numeric"               "numeric" 
##                    1960                    1961                    1962 
##               "numeric"               "numeric"               "numeric" 
##                    1963                    1964                    1965 
##               "numeric"               "numeric"               "numeric" 
##                    1966                    1967                    1968 
##               "numeric"               "numeric"               "numeric" 
##                    1969                    1970                    1971 
##               "numeric"               "numeric"               "numeric" 
##                    1972                    1973                    1974 
##               "numeric"               "numeric"               "numeric" 
##                    1975                    1976                    1977 
##               "numeric"               "numeric"               "numeric" 
##                    1978                    1979                    1980 
##               "numeric"               "numeric"               "numeric" 
##                    1981                    1982                    1983 
##               "numeric"               "numeric"               "numeric" 
##                    1984                    1985                    1986 
##               "numeric"               "numeric"               "numeric" 
##                    1987                    1988                    1989 
##               "numeric"               "numeric"               "numeric" 
##                    1990                    1991                    1992 
##               "numeric"               "numeric"               "numeric" 
##                    1993                    1994                    1995 
##               "numeric"               "numeric"               "numeric" 
##                    1996                    1997                    1998 
##               "numeric"               "numeric"               "numeric" 
##                    1999                    2000                    2001 
##               "numeric"               "numeric"               "numeric" 
##                    2002                    2003                    2004 
##               "numeric"               "numeric"               "numeric" 
##                    2005                    2006                    2007 
##               "numeric"               "numeric"               "numeric" 
##                    2008                    2009                    2010 
##               "numeric"               "numeric"               "numeric" 
##                    2011                    2012 
##               "numeric"               "numeric"
```



5. How many countries are represented in the data? Provide a count.

```r
nlevels(fisheries$Country)
```

```
## [1] 204
```



6. What are the names of the countries?

```r
levels(fisheries$Country)
```

```
##   [1] "Albania"                   "Algeria"                  
##   [3] "American Samoa"            "Angola"                   
##   [5] "Anguilla"                  "Antigua and Barbuda"      
##   [7] "Argentina"                 "Aruba"                    
##   [9] "Australia"                 "Bahamas"                  
##  [11] "Bahrain"                   "Bangladesh"               
##  [13] "Barbados"                  "Belgium"                  
##  [15] "Belize"                    "Benin"                    
##  [17] "Bermuda"                   "Bonaire/S.Eustatius/Saba" 
##  [19] "Bosnia and Herzegovina"    "Brazil"                   
##  [21] "British Indian Ocean Ter"  "British Virgin Islands"   
##  [23] "Brunei Darussalam"         "Bulgaria"                 
##  [25] "Cabo Verde"                "Cambodia"                 
##  [27] "Cameroon"                  "Canada"                   
##  [29] "Cayman Islands"            "Channel Islands"          
##  [31] "Chile"                     "China"                    
##  [33] "China, Hong Kong SAR"      "China, Macao SAR"         
##  [35] "Colombia"                  "Comoros"                  
##  [37] "Congo, Dem. Rep. of the"   "Congo, Republic of"       
##  [39] "Cook Islands"              "Costa Rica"               
##  [41] "Croatia"                   "Cuba"                     
##  [43] "Cura\xe7ao"                "Cyprus"                   
##  [45] "C\xf4te d'Ivoire"          "Denmark"                  
##  [47] "Djibouti"                  "Dominica"                 
##  [49] "Dominican Republic"        "Ecuador"                  
##  [51] "Egypt"                     "El Salvador"              
##  [53] "Equatorial Guinea"         "Eritrea"                  
##  [55] "Estonia"                   "Ethiopia"                 
##  [57] "Falkland Is.(Malvinas)"    "Faroe Islands"            
##  [59] "Fiji, Republic of"         "Finland"                  
##  [61] "France"                    "French Guiana"            
##  [63] "French Polynesia"          "French Southern Terr"     
##  [65] "Gabon"                     "Gambia"                   
##  [67] "Georgia"                   "Germany"                  
##  [69] "Ghana"                     "Gibraltar"                
##  [71] "Greece"                    "Greenland"                
##  [73] "Grenada"                   "Guadeloupe"               
##  [75] "Guam"                      "Guatemala"                
##  [77] "Guinea"                    "GuineaBissau"             
##  [79] "Guyana"                    "Haiti"                    
##  [81] "Honduras"                  "Iceland"                  
##  [83] "India"                     "Indonesia"                
##  [85] "Iran (Islamic Rep. of)"    "Iraq"                     
##  [87] "Ireland"                   "Isle of Man"              
##  [89] "Israel"                    "Italy"                    
##  [91] "Jamaica"                   "Japan"                    
##  [93] "Jordan"                    "Kenya"                    
##  [95] "Kiribati"                  "Korea, Dem. People's Rep" 
##  [97] "Korea, Republic of"        "Kuwait"                   
##  [99] "Latvia"                    "Lebanon"                  
## [101] "Liberia"                   "Libya"                    
## [103] "Lithuania"                 "Madagascar"               
## [105] "Malaysia"                  "Maldives"                 
## [107] "Malta"                     "Marshall Islands"         
## [109] "Martinique"                "Mauritania"               
## [111] "Mauritius"                 "Mayotte"                  
## [113] "Mexico"                    "Micronesia, Fed.States of"
## [115] "Monaco"                    "Montenegro"               
## [117] "Montserrat"                "Morocco"                  
## [119] "Mozambique"                "Myanmar"                  
## [121] "Namibia"                   "Nauru"                    
## [123] "Netherlands"               "Netherlands Antilles"     
## [125] "New Caledonia"             "New Zealand"              
## [127] "Nicaragua"                 "Nigeria"                  
## [129] "Niue"                      "Norfolk Island"           
## [131] "Northern Mariana Is."      "Norway"                   
## [133] "Oman"                      "Other nei"                
## [135] "Pakistan"                  "Palau"                    
## [137] "Palestine, Occupied Tr."   "Panama"                   
## [139] "Papua New Guinea"          "Peru"                     
## [141] "Philippines"               "Pitcairn Islands"         
## [143] "Poland"                    "Portugal"                 
## [145] "Puerto Rico"               "Qatar"                    
## [147] "Romania"                   "Russian Federation"       
## [149] "R\xe9union"                "Saint Barth\xe9lemy"      
## [151] "Saint Helena"              "Saint Kitts and Nevis"    
## [153] "Saint Lucia"               "Saint Vincent/Grenadines" 
## [155] "SaintMartin"               "Samoa"                    
## [157] "Sao Tome and Principe"     "Saudi Arabia"             
## [159] "Senegal"                   "Serbia and Montenegro"    
## [161] "Seychelles"                "Sierra Leone"             
## [163] "Singapore"                 "Sint Maarten"             
## [165] "Slovenia"                  "Solomon Islands"          
## [167] "Somalia"                   "South Africa"             
## [169] "Spain"                     "Sri Lanka"                
## [171] "St. Pierre and Miquelon"   "Sudan"                    
## [173] "Sudan (former)"            "Suriname"                 
## [175] "Svalbard and Jan Mayen"    "Sweden"                   
## [177] "Syrian Arab Republic"      "Taiwan Province of China" 
## [179] "Tanzania, United Rep. of"  "Thailand"                 
## [181] "TimorLeste"                "Togo"                     
## [183] "Tokelau"                   "Tonga"                    
## [185] "Trinidad and Tobago"       "Tunisia"                  
## [187] "Turkey"                    "Turks and Caicos Is."     
## [189] "Tuvalu"                    "Ukraine"                  
## [191] "Un. Sov. Soc. Rep."        "United Arab Emirates"     
## [193] "United Kingdom"            "United States of America" 
## [195] "Uruguay"                   "US Virgin Islands"        
## [197] "Vanuatu"                   "Venezuela, Boliv Rep of"  
## [199] "Viet Nam"                  "Wallis and Futuna Is."    
## [201] "Western Sahara"            "Yemen"                    
## [203] "Yugoslavia SFR"            "Zanzibar"
```


7. Use `rename()` to rename the columns and make them easier to use. The new column names should be:  
+ country
+ commname
+ ASFIS_sciname
+ ASFIS_spcode
+ ISSCAAP_spgroup
+ ISSCAAP_spgroupname
+ FAO_area
+ unit

```r
fisheries <- 
  fisheries %>% 
  dplyr::rename(country = Country,
                commname = `Common name`,
                ISSCAAP_spgroup = `ISSCAAP group#`,
                ASFIS_spcode =`ASFIS species#`,
                ASFIS_sciname = `ASFIS species name`,
               ISSCAAP_spgroupname = `ISSCAAP taxonomic group`,
               FAO_area = `FAO major fishing area`,
               unit = Measure)
```


8. Are these data tidy? Why or why not, and, how do you know? Use the appropriate pivot function to tidy the data. Remove the NA's. Put the tidy data frame into a new object `fisheries_tidy`. 
The data is not tidy because all of the year columns are data and should be pivotted longer.

```r
fisheries_tidy <- 
  fisheries %>% 
  pivot_longer(`1950`:`2012`,
               names_to = "year",
               values_to = "catch")
```



9. Refocus the data only to include country, ISSCAAP_spgroupname, ASFIS_spcode, ASFIS_sciname, year, and catch.

```r
fisheries_tidy2 <- 
  fisheries_tidy %>% 
  select(country, ISSCAAP_spgroupname, ASFIS_spcode, ASFIS_sciname, year, catch)
```



10. Re-check the classes of `fisheries_tidy2`. Notice that "catch" is shown as a character! This is a problem because we will want to treat it as a numeric. How will you deal with this?
I already dealt with this when the classes needed to be fixed

```r
str(fisheries_tidy2)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	1114596 obs. of  6 variables:
##  $ country            : Factor w/ 204 levels "Albania","Algeria",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ ISSCAAP_spgroupname: Factor w/ 30 levels "Abalones, winkles, conchs",..: 25 25 25 25 25 25 25 25 25 25 ...
##  $ ASFIS_spcode       : Factor w/ 1553 levels "1020100101","1020100201",..: 92 92 92 92 92 92 92 92 92 92 ...
##  $ ASFIS_sciname      : Factor w/ 1548 levels "Ablennes hians",..: 1412 1412 1412 1412 1412 1412 1412 1412 1412 1412 ...
##  $ year               : chr  "1950" "1951" "1952" "1953" ...
##  $ catch              : num  NA NA NA NA NA NA NA NA NA NA ...
```

```r
catch1 <- fisheries_tidy2$catch
class(catch1)
```

```
## [1] "numeric"
```



11. Based on the ASFIS_spcode, how many distinct taxa were caught as part of these data?

```r
nlevels(fisheries_tidy2$ASFIS_spcode)
```

```
## [1] 1553
```



12. Which country had the largest overall catch in the year 2000? #ask about this one
Peru had the largest catch.

```r
fisheries_tidy2 %>% 
  group_by(country) %>% 
  filter(year == 2000) %>% 
  summarise(catch = sum(catch, na.rm = TRUE)) %>% 
  arrange(desc(catch))
```

```
## # A tibble: 204 x 2
##    country                     catch
##    <fct>                       <dbl>
##  1 Peru                     10625010
##  2 Japan                     4921013
##  3 United States of America  4692229
##  4 Chile                     4297928
##  5 Indonesia                 3761769
##  6 Russian Federation        3678828
##  7 Thailand                  2795719
##  8 India                     2760632
##  9 Norway                    2698506
## 10 Iceland                   1982369
## # … with 194 more rows
```






13. Which country caught the most sardines (_Sardina_) between the years 1990-2000?
Morocco has the largest sardine catch


```r
fisheries_tidy2 %>% 
  filter(str_detect(ASFIS_sciname, "Sardina")) %>% 
  filter(year >= 1990 & year <= 2000) %>%
  group_by(country) %>% 
  summarize(catch = sum(catch, na.rm = T)) %>% 
  arrange(desc(catch))
```

```
## # A tibble: 46 x 2
##    country              catch
##    <fct>                <dbl>
##  1 Morocco            4785190
##  2 Spain              1425317
##  3 Russian Federation 1035139
##  4 Portugal            926318
##  5 Ukraine             784730
##  6 Italy               377907
##  7 Algeria             311733
##  8 Turkey              273565
##  9 France              263871
## 10 Denmark             242017
## # … with 36 more rows
```



14. Which five countries caught the most cephalopods between 2008-2012?
The top 5 countries are China, Peru, Korea, Japan, and Chile.

```r
fisheries_tidy2 %>% 
  filter(str_detect(ISSCAAP_spgroupname, "Squids")) %>% 
  filter(year <=2012 &year >=2008) %>% 
  group_by(country) %>% 
  
  summarise(catch = sum(catch, na.rm = T)) %>% 
  arrange(desc(catch))
```

```
## # A tibble: 139 x 2
##    country                    catch
##    <fct>                      <dbl>
##  1 China                    4785139
##  2 Peru                     2274232
##  3 Korea, Republic of       1535454
##  4 Japan                    1394041
##  5 Chile                     723186
##  6 Indonesia                 684567
##  7 United States of America  613400
##  8 Thailand                  603529
##  9 Taiwan Province of China  593638
## 10 Argentina                 587238
## # … with 129 more rows
```



15. Given the top five countries from question 12 above, which species was the highest catch total? The lowest?
The species with the highest catch total of the five countries was Dosiducus gigas with 784022 and the species witht the lowest catch total was Moroteuthis ingens with 2. 

```r
cephalopod_stats <- 
  fisheries_tidy2 %>% 
  filter(country == "China" | country ==  "Peru" | country == "Korea" | country == "Japan" | country == "Chile") %>% 
  filter(str_detect(ISSCAAP_spgroupname, "Squids")) %>% 
  filter(year <=2012 &year >=2008) %>% 
  group_by(ASFIS_sciname) %>% 
  summarise(catch = sum(catch, na.rm = T)) %>% 
  arrange(desc(catch))
```



16. In some cases, the taxonomy of the fish being caught is unclear. Make a new data frame called `coastal_fish` that shows the taxonomic composition of "Miscellaneous coastal fishes" within the ISSCAAP_spgroupname column.


```r
coastal_fish <- 
  fisheries_tidy2 %>% 
  filter(ISSCAAP_spgroupname == "Miscellaneous coastal fishes")
```


17. Use the data to do at least one exploratory analysis of your choice. What can you learn?
I want to know which country caught the most octopus in 1963.
The answer is Italy




```r
fisheries_tidy %>% 
  filter(str_detect(commname, "octopus")) %>% 
  filter(year == 1963) %>% 
  group_by(country) %>% 
  summarise(catch = sum(catch, na.rm = T)) %>% 
  arrange(desc(catch))
```

```
## # A tibble: 22 x 2
##    country            catch
##    <fct>              <dbl>
##  1 Italy               6100
##  2 Spain               1900
##  3 Tunisia             1000
##  4 Mexico               700
##  5 Yugoslavia SFR       100
##  6 Albania                0
##  7 Congo, Republic of     0
##  8 Croatia                0
##  9 Dominican Republic     0
## 10 France                 0
## # … with 12 more rows
```


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
