# SteepestAscent
Steepest Ascent to find local max and min in multivariate function
# A way to find a global maximum is to consider several different starting points, and hope for one one their local maxima to be the global maximum. Randomization can be used to find a starting point. 
#Consider the function: {-(x[1]^2+x[2]^2-2)*(x[1]^2+x[2]^2-1)*(x[1]^2+x[2]^2)*(x[1]^2+x[2]^2+1)*(x[1]^2+x[2]^2+2))} x {(2-sin(x[1]^2-x[2]^2)*cos(x[2]-exp(x[2])))}.
It has several local maxima in the region [-1.5,1.5] X [-1.5,1.5]. Using several randomly chosen starting points, steepest ascent is used to find all of the local maxima of f, and thus the global maximum. Here I use the command runif(2,-1.5,1.5) to generate a random point (x,y) in the region [-1.5,1.5] X [-1.5,1.5]. 
Note: if y is too large then exp(y) is Inf and cos(y-exp(y)) will return NaN. This can pose problems for maximizing f. One solution is to ignore the term cos(y-exp(y)) and cose up the function f as follows:

f <- function(x) { 
#x is a vector of length 2
s <- sum(x^2)
z <- -(s-2)*(s-1)*s*(s+1)*(s+2)* (2-sin(x[1]^2-x[2]^2)*cos(x[2]-exp(x[2])))
if (is.nan(z)) {
  z <- -(s-2)*(s-1)*s*(s+1)*(s+2)*2
  }
  return(z)
  }
