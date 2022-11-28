# SwirlRNotes

Questions
-	`ls()` gives items in workdesk, how do we search if item is there?

# 1	R PROGRAMMING: THE BASICS OF PROGRAMMING IN R (21/11/2022)
## 1.1	BASIC BUILDING BLOCKS (13/11/2022)
Assigning variable: `x <-` 

Vector: `c(…)`, can concatenate by `c(c(…),c(…))`

Help: `?function`

Arithmetic: `+ - / ^ sqrt() abs()` [for vectors it’s all done component wise if $n_1 = n_2$, otherwise its recycled]

Up arrow instead of retype, tab to find variables

## 1.2	WORKSPACE AND FILES (13/11/2022)
Current directory: `getwd()`

Objects in workspace: `ls()`

`list.files()` or `dir()`

`args(function)`

`dir.create("testdir")`

`setwd()`

`file.create("mytest.R")`

`file.exists()`

`file.info()`

`$` to extract specific item

`file.rename(from, to)`

`file.copy(from, to)`

`file.path()`

`unlink("testdir", recursive = TRUE)`

## 1.3	SEQUENCES OF NUMBERS (13/11/2022)

`a:b` counts in increments of size 1 from first number till reaches next

`seq(a, b, by=c)` increments size c

`seq(a, b, length=c)` increments st seq size is c i.e. adds in increments $\frac{b-a}{c-1}$

length()

seq(along.with = my_seq) or seq_along(my_seq) gives sequence 1 2 … length(my_seq)

rep(a, times = b) gives a … a, b times 

rep(c(…), times = b) gives c1 … cn … , b times

rep(c(…), each = b) gives c1 … c1 … cn … cn b times each

## 1.4	VECTORS (13/11/2022)

Atomic and lists

Types of atomic vectors: numeric, logical, character, integer, complex

Character: c(“…”, “…”, …, “…”)

Use paste(vector, collapse = “ “) to turn it into one vector

Or paste(vector1, vector2, sep = “ “) to join componentwise 
## 1.5	MISSING VALUES (13/11/2022)

NA ‘not available’, operations leave it unchanged

NaN ‘not a number’

is.na(vector) tells you which positions are NA

sum(vector) sums the vector, for TRUE and FALSE vectors it sums the 

## 1.6	SUBSETTING VECTORS (14/11/2022)

x[a:b] extracts elements a to b from vector x

x[c(…)] extracts those specific elements from x

x[-c(…)] extracts all but those specific elements from x

x[logical operation] returns the elements that correspond to true

x[“…”] returns element with that name

‘one-based indexing’

names()

identical() compares if vectors (or matrices) are the same

## 1.7	MATRICES AND DATA FRAMES (14/11/2022)

dim() dimension of object, m n means m rows n columns, can assign a vector a dimension and this turns it into a matrix

length() length of vector

attributes() 

class()

matrix(data = , nrow = , ncol = )

cbind(vector, matrix) binds column vector on LHS of matrix but turns everything into characters

data.frame(vector, matrix) binds without coercion

colnames(my_data) <- cnames

## 1.8	LOGIC (15/11/2022)

`<`, `>`, `>=`, `<=`, `==`, `!=`, `|` or, `&` and, `|` or (for first entry of vector), `&&` and (for first entry of vector), `!` negation

Order of operations: and before or

isTRUE()

xor()

which() gives position in vector for which statement is true

any() logical statement for vectors equiv to or

all() logical statement for vectors equiv to and

## 1.9	FUNCTIONS (17/11/2022)
Sys.Date()

function_name <- function(arg1, arg2){

# Manipulate arguments in some way

# Return a value

}

increment <- function(number, by = 1){

number + by

}

evaluate <- function(func, dat){

func(dat)

}

Can evaluate anonymous functions

"%mult_add_one%" <- function(left, right){ # Notice the quotation marks!

left * right + 1

}

If there’s a … need everything after … to have specified default value

## 1.10	LAPPLY AND SAPPLY (18/11/2022)

head() shows first 6 lines of dataset

lapply(dataset, function) – list apply – function on columns

sapply(dataset, function) – simplify list apply – simplifies lapply to a matrix (if poss)

## 1.11	VAPPLY AND TAPPLY (18/11/2022)

vapply(dataset, function, type of data) – sapply but with specificity

tapply(dataset$column, dataset$column, function) – splits it up by both columns

## 1.12	LOOKING AT DATA (18/11/2022)

Format, dimensions, variable names, variables stored, missing data, flawed data

ls() list variables in workspace

class()

dim()

nrow()

ncol()

object.size() – gives number of bytes

names() – column names

head( , n) – first n rows, 6 by default

tail( , n) – last n rows, 6 by default

summary()

str() - structure

## 1.13	SIMULATION (19/11/2022)

sample(set, number of samples, replace = FALSE, prob = vec of resp probs of each item in set)

r – random, d – density, p – probability, q - quantile

rbinom(n, size, prob) ¬¬

replicate(number of replications, distribution)

hist() – histogram

## 1.14	DATES AND TIMES (21/11/2022)

Dates represented by ‘Date’ class, times represented by 'POSIXct' and 'POSIXlt' classes

dates are stored as the number of days since 1970-01-01 

times are stored as number of seconds since 1970-01-01 (for 'POSIXct') or list of seconds, minutes, hours, etc. (for 'POSIXlt').

Sys.date(), Sys.time() – gives in POSIXct

Class()

Unclass()

YEAR-MONTH-DAY

as.Date()

as.POSIXlt()

weekdays()

months()

quarters()

strptime() turns something onto YYYY-MM-DD, example input: (t3, "%B %d, %Y %H:%M")

can compare times

difftime(time1, time2, units = ‘…’)

lubridate package

1.15	BASE GRAPHICS (21/11/2022)

plot(dataset) – gives scatterplot

plot(x = dataset$col1, y = dataset$col2, …)

xlab = “”, ylab = “”, main = “”, sub = “”, col = #, xlim = c(a, b), pch = #

key things to explore: dim(), names(), head(), tail() and summary()

boxplot(formula = col1 ~ col2, data = dataset)

hist(mtcars$mpg)

http://varianceexplained.org/r/teach_ggplot2_to_beginners/

http://www.ling.upenn.edu/~joseff/rstudy/week4.html

# 2	REGRESSION MODELS: THE BASICS OF REGRESSION MODELING IN R

https://github.com/DataScienceSpecialization/courses

## 2.1	INTRODUCTION (21/11/2022)

lm(depvar ~ indepvar, dataset)

summary(regrline)

## 2.2	RESIDUALS 

Residuals is difference between line of best fit and points

mean(fit$residuals)

cov(fit$residuals, dataset$indepvar)

## 2.3	LEAST SQUARES ESTIMATION

## 2.4	VARIATION

## 2.5	INTRODUCTION TO MULTIVARIABLE REGRESSION

## 2.6	MULTIVAR EXAMPLES

## 2.7	MULTIVAR EXAMPLES2 

## 2.8	MULTIVAR EXAMPLES3

## 2.9	RESIDUALS DIAGNOSTICS AND VARIATION 

## 2.10	VARIANCE INFLATION FACTORS 

## 2.11	OVERFITTING AND UNDERFITTING

## 2.12	BINARY OUTCOMES

## 2.13	COUNT OUTCOMES

# 3	STATISTICAL INFERENCE: THE BASICS OF STATISTICAL INFERENCE IN R



# 4	EXPLORATORY DATA ANALYSIS: THE BASICS OF EXPLORING DATA IN R



