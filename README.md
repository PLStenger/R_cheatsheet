# R_cheatsheet
 Useful tricks I always needs, I'm always searching and finding them hours after...

### Make all comparisons possible

    combn(c( "0",
         "3",
         "6",
         "12",
         "18",
         "24",
         "60"), 2)

    
         [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12] [,13] [,14] [,15] [,16] [,17] [,18] [,19] [,20] [,21]
     [1,] "0"  "0"  "0"  "0"  "0"  "0"  "3"  "3"  "3"  "3"   "3"   "6"   "6"   "6"   "6"   "12"  "12"  "12"  "18"  "18"  "24" 
     [2,] "3"  "6"  "12" "18" "24" "60" "6"  "12" "18" "24"  "60"  "12"  "18"  "24"  "60"  "18"  "24"  "60"  "24"  "60"  "60" 
     
Add `t()` for upside-down      
     
     
### ggplot without legend

     + theme(legend.position="none")

### ggplot no X axis labels, title and ticks

     + theme(axis.title.x=element_blank(),
        axis.text.x=element_blank(),
        axis.ticks.x=element_blank())

### ggplot split legend in two column

     + guides(fill=guide_legend(ncol=2))
     

### Subset data.frame

     newdat <- dat[ which(dat$XX=='X' & dat$YY > Y), ]


### Delete row in data.frame according condition

     dat <- dat[ which(dat$Phylum!='Rhabditophora'), ]
  
### Change pattern in data.frame

     dat$Phylum <- gsub(' Dinoflagellata', 'Dinoflagellata', dat$Phylum)

### Turn all integer in a data.frame into numeric

     dat[] <- lapply(dat, function(x) {
       if(is.integer(x)) as.numeric(as.character(x)) else x
     })
     
### Order discrete x scale by frequency/value 

     dat$Condition <- factor(dat$Condition, levels=c("SF", "LF", "F"))
     
     
     
     
### summarise dat
     dat_summarise <- dat %>% 
       group_by(phylum, index) %>% 
       summarise(value = sum(value))
 

     head(dat_summarise)

### spread dat

     dat_summarise %>% spread(species, value)


### A small suggestion for increasing citations to your R package(s)
### from a Gaurav Sood mail:      

'Recently, I have been thinking about how to increase citations to R packages. I believe one of the reasons users don't cite software is that citations to software aren't the norm in academia. Another is that users forget. Taking inspiration from Marek Hlavac, whose stargazer package has more than 1,000 citations, I believe a short .onAttach message cuing the citation can help increase citations.  

Here's the code in stargazer that produces the StartupMessage:

https://github.com/cran/stargazer/blob/master/R/stargazer-internal.R

We can also rewrite the code using the citation function in R as follows:'

```
packageStartupMessage("\nPlease cite as:\n")
citationInfo <- citation("stargazer")
  
packageStartupMessage(paste(citationInfo$title))
```

A note thanking users may make the message even more effective: 

```
.onAttach <- function(libname, pkgname) {
  package_citation <- "Author, X. (Year). MyPackage: A powerful R package for XYZ. R Foundation for Statistical Computing. Version X.X. URL: https://example.com/mypackage"
  message("Thank you for using MyPackage!")
  message("To acknowledge our work, please cite the package:")
  message(package_citation)
}

```
