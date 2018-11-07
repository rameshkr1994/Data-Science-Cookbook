## R Questions

`1.`	 Comment the following code?

```R
Sum <- rbind(data_frame1,data_frame2)
```
`2.`	Vector `v` is `c(1,2,3,4)` and list `x` is `list(5:8)`, what is the output of `v*x[1]`?

`3.`	What does `unlist()` do?

`4.`	What is the difference between "`%%`" and "`%/%`"?

`5.`	What’s the output of the following code?
```R
15 %in% x
```

`6.`	Comment the following code?
```R
pairs(formula, data)
```
`7.`	Comment of the following code?
```R
is.matrix(m)
```
`8.`	What’s the output of the following code?
```R
x <- c("a", "b", "c")
> as.numeric(x)
```
`9.`	What’s the output of the following code?
```R
> y <- data.frame(a = 1, b = "a")
> dput(y)
```

`10.`	What’s the output of the following code?
```R
> x <- 1:4
> y <- 6:9
> z <- x + y
> z
```
`11.`	What’s the output of the following code?
```R
> x <- matrix(1:4, 2, 2)
> y <- matrix(rep(10, 4), 2, 2)
> x * y
```
`12.`	What’s the output of the following code?
```python
for(i in 1:100) {
             if(i <= 20) {
                next
      }
}
```
`13.`	Comment the following code?
```R
if( any(x < 0) ) y <- log(1+x) else y <- log(x)
```
`14.`	What’s the output of the following code?
```R
> f <- function() {
+             ## This is an empty function
+ }
> f()
```
`15.`	What’s the output of the following code?
```R
> f <- function() {
+              cat("Hello, world!\n")
+ }
> f()
```
`16.`	What’s the output of the following code?
```R
> f <- function(a, b) {
+       a^2
+ }
> f(2)
```
`17.`	Which of the variable in the following code is variable ?
```R
> f <- function(x, y) {
+            x^2 + y / z
+ }
```
`18.`	Comment the following code:
```R
> x <- list(a = 1:5, b = rnorm(10))
> lapply(x, mean)
```
`19.`	Comment the following code:
```R
install.packages("caret")
# load caret package
library(caret)
# load the dataset
data(iris)
# calculate the pre-process parameters from the dataset
preprocessParams <- preProcess(iris[,1:4], method=c("range"))
# transform the dataset using the pre-processing parameters
transformed <- predict(preprocessParams, iris[,1:4])
# summarize the transformed dataset
summary(transformed)
```
`20.`	Comment the following code?:
```R
# load the library
library(caret)
# load the iris dataset
data(iris)
# define training control
trainControl <- trainControl(method="cv", number=10)
# estimate the accuracy of Naive Bayes on the dataset
fit <- train(Species~., data=iris, trControl=trainControl, method="nb")
# summarize the estimated accuracy
print(fit)
```
`21.`	Comment the following code?:
```R
# load caret library
library(caret)
# load the iris dataset
data(iris)
# prepare 5-fold cross validation and keep the class probabilities
control <- trainControl(method="cv", number=5, classProbs=TRUE, summaryFunction=mnLogLoss)
# estimate accuracy using LogLoss of the CART algorithm
fit <- train(Species~., data=iris, method="rpart", metric="logLoss", trControl=control)
# display results
print(fit)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgwMDczMTMyOF19
-->