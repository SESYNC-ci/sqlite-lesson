---
---

## Connecting to a Database

We are going to look at the Portal mammals data organized in an SQLite database.
This is stored in a single file `portal.sqlite` that can be explored using SQL
or with tools like [SQLite Viewer](https://inloop.github.io/sqlite-viewer/) or [DB Browser](https://sqlitebrowser.org/). We will use R functions in the DBI-compliant
RSQLite package to interact with the database. 
{:.notes}


===

## Connections

The first step from RStudio is creating a connection object that
opens up a channel of communication to the database file. 



~~~r
library(RSQLite)
con <- dbConnect(RSQLite::SQLite(), 
                 "data/portal.sqlite")
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}



===

With the connection object availble, you can begin exploring the database.



~~~r
> dbListTables(con)
~~~
{:title="Console" .input}


~~~
[1] "observers" "plots"     "species"   "surveys"  
~~~
{:.output}


===



~~~r
> dbListFields(con, 'species')
~~~
{:title="Console" .input}


~~~
[1] "species_id" "genus"      "species"    "taxa"      
~~~
{:.output}


===

Read an entire database table into an R data frame with `dbReadTable`, or if you
prefer "tidyverse" functions, use the [dplyr](){:.rlib} `tbl` function.



~~~r
library(dplyr)
species <- tbl(con, 'species')
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}



~~~r
> species
~~~
{:title="Console" .input}


~~~
# Source:   table<species> [?? x 4]
# Database: sqlite 3.30.1 [/nfs/public-data/training/portal.sqlite]
   species_id genus            species         taxa   
   <chr>      <chr>            <chr>           <chr>  
 1 AB         Amphispiza       bilineata       Bird   
 2 AH         Ammospermophilus harrisi         Rodent 
 3 AS         Ammodramus       savannarum      Bird   
 4 BA         Baiomys          taylori         Rodent 
 5 CB         Campylorhynchus  brunneicapillus Bird   
 6 CM         Calamospiza      melanocorys     Bird   
 7 CQ         Callipepla       squamata        Bird   
 8 CS         Crotalus         scutalatus      Reptile
 9 CT         Cnemidophorus    tigris          Reptile
10 CU         Cnemidophorus    uniparens       Reptile
# … with more rows
~~~
{:.output}


===

The `dbWriteTable` function provides a mechanism for uploading data, as long as
the user specified in the connection object has permission to create tables.



~~~r
df <- data.frame(
  id = c(1, 2),
  name = c('Alice', 'Bob')
)

dbWriteTable(con, "observers", 
             value = df)
~~~
{:title="{{ site.data.lesson.handouts[0] }}" .text-document}


===



~~~r
> dbReadTable(con, 'observers')
~~~
{:title="Console" .no-eval .input}


