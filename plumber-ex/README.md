
plumber-ex
==========

Minimal example of a R plumber API and Dockerfile.

The `plumber.R` example is the minimal example in the **plumber** package README.

If you open plumber.R in RStudio, there should be a "Run API" button at the top right of the pane. Assuming it runs, this will open a new window with a [swagger](https://swagger.io) UI for your API. 

But generally speaking, to start the API from R, use this code:

```r
library("plumber")

pr <- plumber::plumb("plumber.R")
pr$run(port = 5018)
```

And then go to the appropriate URL in your browser, `curl` around, etc. 

## Docker

This example also includes a minimal Dockerfile for running `plumber.R` in a container. If Docker is not installed, install and start it. Then the container can be built and run with this code:

```zsh
docker build -t plumberex .
docker run --rm --name plumberex -d -p 5018:5018 plumberex
curl "http://127.0.0.1:5018/echo?msg=HelloWorld"
docker stop plumberex
```
