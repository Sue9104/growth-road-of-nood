# Object

| Category        |                                        |
| --------------- | -------------------------------------- |
| S3              | geneirc-function                       |
| S4              | define, inheritance, multiple dispatch |
| Reference Class | new, mutable in place                  |

## S3

```r
// new
seq <- list(sequence = "ATCGGGG")
class(seq) <- "StudentInfo"

seq <- structure(list(sequence = "ATCGGGG"), class = "DNA")
seq$sequence


// method
count_basepair <- function(x) UseMethod("count_basepair")
count_basepair.DNA <- function(x){
   return(nchar(x$sequence))
}
count_basepair(seq)
```

## S4

```r
// define
setClass("DNA", slots = list(sequence="character", species="character"))

// new
sample_dna <- new("DNA", sequence="AATCCCGCG", species="homo sapiens")
sample_dna@sequence
                   
// method
setGeneric("count_sequence_basepair", function(x){standardGeneric("count_sequence_basepair")})
setMethod("count_sequence_basepair", "DNA", function(x){return(nchar(x@sequence)})
```

## Reference Class

```r
// define
DNA <- setRefClass("dna", 
   fields = list(sequence="character", species="character"),
   methods=list(
      count_sequence_basepair = function(){return(nchar(sequence))}
   ),
)

// new
my_sample <- DNA$new(sequence="ATATACGCG", species="homo sapiens")
 
// method
DNA$methods(cat_sp=function(){cat(species)})
my_sample$count_sequence_basepair()

```
