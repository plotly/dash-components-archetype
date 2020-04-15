# <%= packageNameCamelCase %>

<%= packageDescription %>

## Installation

<%= packageNameCamelCase %> is not yet available on CRAN, but you can install with:

```r
remotes::install_github("<%= packageGitHubOrg %>/<%= packageName %>")
```

## Usage

```r
library(<%= packageNameCamelCase %>)
library(dashR)

app <- Dash$new()

app$layout_set(
  ExampleComponent(id = "inputID", value = "initial value"),
  htmlDiv(id = "outputID")
)

app$callback(
  function(x = input("inputID")) {
    sprintf("You've entered: '%s'", x)
  },
  output("outputID")
)

app$run_server(showcase = TRUE)
```
