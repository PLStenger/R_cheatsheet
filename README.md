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
     
     
### Subset data.frame

     newdat <- dat[ which(dat$XX=='X' & dat$YY > Y), ]
