The Here [package](https://here.r-lib.org/) streamlines file referencing in projects. It lets us easily reference the root of the project directory and build subpaths.

#### Usage Example

Suppose I am within a file in the deworming OPA project.
- `here()` returns  `"C:/Users/thepe/Documents/GitHub/opa-deworming"`.
- `here("links.csv") returns `"C:/Users/thepe/Documents/GitHub/opa-deworming/links.csv"`.
- `here("code", "shiny_app", "analysis.R") returns `"C:/Users/thepe/Documents/GitHub/opa-deworming/code/shiny_app/analysis.R"`.

#### Why?

The `here()` command is preferable to `setwd()` and `getwd()` for two main reasons:
1. `here` is invulnerable to changes in file location, since the file path is rooted at the project folder.
2. Over the course of a program executing, the working directory does not effect `here()`.

#### Extra

Check out [this](https://github.com/jennybc/here_here#the-fine-print) explanation for more details about *how* the package finds the top-leve of the project.
