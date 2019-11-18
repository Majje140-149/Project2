## Cache the inverse

makeCacheMatrix <- function(x = matrix()) {
## y will be the inverse of x
    y <- NULL

    ## Set the matrix
    set <- function( matrix ) {
            x <<- matrix
            t <<- NULL
    }

    ## Get the matrix
    get <- function() {
    	x
    }

    ## Set the inversed matrix
    setInverse <- function(inverse) {
        y <<- inverse
    }

    ## Get the inversed matrix
    getInverse <- function() {
        y
    }

    ## Return a list of the methods
    list(set = set, get = get,
         setInverse = setInverse,
         getInverse = getInverse)
}

cacheSolve <- function(x, ...) {

    ## Return a matrix which is the inverse of 'x'
    i <- x$getInverse()

    ## Return the inverse, if its already set
    if( !is.null(m) ) {
            message("getting cached data")
            return(i)
    }

    ## Get the matrix
    data <- x$get()

    ## Calculate the inverse
    i <- solve(data) %*% data

    ## Set the inverse
    x$setInverse(i)

    ## Return the matrix
    i
}
