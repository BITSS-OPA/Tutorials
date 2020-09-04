# How to Customize Reactions

## Reactivity

### Reactivity Model
<p align = "center">
  <img  width="100%" src="images in tutorial/reactivityModel.png">
  <br>
    <em>Reactivity Model</em>
</p>

* `expression()`: secondary object that's reactive in itself
* `Update`: user clicks update button to change the output
* `run(this)`: R code to run on server's side

Reactive values work together with reactive functions. If you put reactive values outside the reactive function, you will get error below:
`Error in .getReactiveEnvironment()$currentContext()`

<p align = "center">
  <img  width="100%" src="images in tutorial/twostepreactivity.png">
  <br>
    <em>Two Step Process for Reactivity</em>
</p>

### Reactive Toolkit (Some Indispensible Functions)

#### 1. Display output with render*()  

  Make objects display with various render*() functions, such as `renderDataTable()`, `renderImage()`. Details see renderPlot().
  <p align = "center">
    <img  width="100%" src="images in tutorial/renderfunc.png">
    <br>
      <em>render*() Function</em>
  </p>
  **Challenge Case**:  

  *Because render *() responds to all reactive values, sometimes it results in the challenge case presented below.*

  <p align = "center">
    <img  width="100%" src="images in tutorial/challengecase.png">
    <br>
      <em>Challenge Case for render*()</em>
  </p>

  Because render*() responds to any reactive values, whenever we change our input$title, it also results in shinyApp rerunning our code block and generating a new histogram.

#### 2. Modularize code with reactive()  
  reactive() builds a reactive object (reactive expression as seen in the Reactivity Model above). We use this function when our Shiny App needs to display two objects that need to use the same data.   

  <p align = "center">
    <img  width="100%" src="images in tutorial/reactive1.png">
    <br>
      <em>Failure case of render*()</em>
  </p>

  Here we are using the same input object and plugging into two separate render*() functions with rnorm() in the code block. Because of the randomness of rnorm(), we cannot guarantee that the data generated from `rnorm(input$num)` for renderPlot() and for renderPrint() are the same dataset. Hence, we need to save this same data to a reactive object in the server function.

  In our case, the reactive object would be something like:
  `data <- reactive({rnorm(input$num)})``

  After adding a reactive object, we now could use the same data for both `renderPlot` and `renderPrint`
  <p align = "center">
    <img  width="50%" src="images in tutorial/afterReactive.png">
    <br>
      <em>Added Reactive Object</em>
  </p>

  *NOTE*:
  1. When we call this reactive object, we need to call it like a function: `data()`
  2. Reactive expressions also cache their values to avoid unnecessary computation, meaning that the expression will return its most recent value, unless it becomes invalidated.

#### 3. Prevent reactions with isolate()

  Going back to our first reactive function, when we update `input$title`, the histogram also gets updated because a new modification to `input$title` will also cause the reactive function to rerun. We can solve this problem by using `isolate()`

  `isolate()` returns the result as a *nonreactive* value. So if we do `isolate({input$title})`, only changes in `input$num` will result the reactive function to rerun.


#### 4. Trigger Code with observeEvent()

* Works with *Action Buttons* (which goes in `ui <- fluidPage()`)
<p align = "center">
  <img  width="100%" src="images in tutorial/actionbutton.png">
  <br>
    <em>Action button function structure</em>
</p>

* It triggers code to run on server with observeEvent() and it goes in `server` objects
<p align = "center">
  <img  width="100%" src="images in tutorial/observeEvent.png">
  <br>
    <em>Observe Event function structure</em>
</p>

*NOTE:* the first input for the obserEvent() is the update button's inputId!!

<p align = "center">
  <img  width="100%" src="images in tutorial/observeEventAssembled.png">
  <br>
    <em>Action Button and observeEvent Assembled</em>
</p>

There is also the function observe(), which responds to **every reactive value** in the code block.

`observe({print(input$clicks)})`

It uses the same syntax as render*(), reactive(), and isolate()


#### 5. Delay Reactions with eventReactive()
* eventReactive() creates a reactive expression that only responds to specific values (normally action buttons)
* It works like reactive() to create a reactive object, but it only responds to specific values such as an action button.

<p align = "center">
  <img  width="100%" src="images in tutorial/eventReactive.png">
  <br>
    <em>How to Use eventReactive() with an Action Button</em>
</p>


#### 6. Manage state with reactiveValues()
* In Shiny App, you cannot change your input values through code, and only the users are allowed to choose input values.
* But you could create a reactive value with reactiveValues() that you could overwrite and add values to later on.

<p align = "center">
  <img  width="100%" src="images in tutorial/reactivevalue.png">
  <br>
    <em>How to Use eventReactive() with an Action Button</em>
</p>

Here we used `rv <- reactiveValues(**optional element**)` to create a reactive value and store a normal distribution consisted of 100 numbers in it.
Later on, we overwrite this reactive value in observeEvent() so that when we click action button with Id "norm" or "unif", rv is overwritten in the way specified by the code block.

#### Review!

<p align = "center">
  <img  width="100%" src="images in tutorial/updatedModel.png">
  <br>
    <em>Updated Model with New Functions</em>
</p>

***NOTE: Try to place code where it will be re-run as little as necessary!***

<p align = "center">
  <img  width="100%" src="images in tutorial/rerun.png">
  <br>
    <em>How Shiny App Runs Codes</em>
</p>
