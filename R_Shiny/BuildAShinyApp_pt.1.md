# R Shiny

#### Model

<p align = "center">
  <img  width="100%" src="images in tutorial/model.png">
  <br>
    <em>How R Shiny Works</em>
</p>

It consists of a server instruction part where you can change outputs and tell the server what to do, as well as a webpage user interface that presents to readers/users.

## How to Build a Shiny App

#### App Template

> `library(shiny)`  
> `ui <- fluidPage( *Input() functions,  
>                    *Output() functions)`  
> `server <- function(input, output){}`  
> `shinyApp(ui = ui, server = server)`

Build your apps around inputs and outputs!

### Build UI Object

#### Inputs
* Creates reactive inputs with **Input()* functions
* Input functions (built-in in shiny library)
  * Example:
  <p align = "center">
    <img  width="100%" src="images in tutorial/sliderInput.png">
    <br>
      <em>Input Function Example</em>
  </p>

  * inputId: important what you set it as! You will need to use the ID for the server object later.


#### Outputs
* Displays reactive results with *Output() functions in fluidPage()
* Output functions
  * Example:
  <p align = "center">
    <img  width="100%" src="images in tutorial/plotOutput.png">
    <br>
      <em>Output Function Example</em>
  </p>
  * Based on what you need to display, Shiny App also has other output functions such as `dataTableOutput(), imageOutput()`, etc.
  * outputId: important what you set it as! You will need to use the ID for the server object later.

#### Template Progress
<p align = "center">
  <img  width="100%" src="images in tutorial/templateProgress.png">
  <br>
    <em>UI Object Built with Input and Output Function</em>
</p>

Note: Putting a output function in the UI object only means there will be a space in the ui for an R object. You still need to *build what to display* in the server function.


### Build Server object

Server object assembles inputs into outputs

#### 3 Rules to Follow

1. Save objects to display as output$"outputId", as named in the output function above.

2. Build objects to display with `render*()` function  
  `output$hist <- renderPlot()`  
  <p align = "center">
    <img  width="100%" src="images in tutorial/render.png">
    <br>
      <em>Render Function Example</em>
  </p>

  In the curly brackets {}, you can customize your object by adding more codes.

3. Access input values with `input$"inputId"`This is where reactivity automatically occurs.
<p align = "center">
  <img  width="100%" src="images in tutorial/template2.png">
  <br>
    <em>Simple Server Function Example</em>
</p>

Input value changes whenever user changes it, whereas output will update automatically. For example, in our sliderInput() in the UI object, if a user changes the input value to another value, the histogram will update by itself because we already assembled input and output in the server function.

#### Template Progress So Far  

<p align = "center">
  <img  width="100%" src="images in tutorial/progress2.png">
  <br>
    <em>A Simple Shiny App Built</em>
</p>


### Share Your apps

**1. Save Your App**  
All the files should be in one directory! This includes datasets, images, code files, etc. There are two ways to save your app:
* Everything in one file: `app.R`, but in this case we needs to call shinyApp() function.
* Have a separate file for `ui.R` and `server.R`. In this case, `shinyApp()` is not required.

**2. Use Shinyapps.io as your server**
* Log into the website first
* Install "shinyapps" from Github
  * Run `devtools::install_github("rstudio/shinyapps")` in your console.
* Enter tokens to know which shinyapp account to pair ID with.
* Now you can publish it to ShinyApps!

**3. Could also build your own server with Shiny Server**
