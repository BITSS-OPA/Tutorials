# How to Customize Appearance

### Shiny App's User Interface

* So far you don't need to know HTML to build a user interface in ShinyApp because R functions assemble HTML for you.
* We can use `fluidPage()` to quickly set up a UI
* We use `input*()` and `output()` to add space for reactive elements in our user interface.
* At last, we save our output to ui like `ui <- fluidPage(...)`

### Add Static Content

When writing HTML, we need to use tags to tell HTML how to format our webpage. For example,
tag `<h1> </h1>` refers to headline with the biggest font.

In R Shiny, we could add content with `tags` functions that essentially recreate HTML tags for us.
> `tags$h1()` :left_right_arrow: `<h1></h1>`  
> `tags$a()` :left_right_arrow: `<a></a>`

* We could use a dollar sign `$` right after tags to access different HTML tags
* We need to call `tag$h1()` like a function for it to work

<p align = "center">
  <img  width="100%" src="images in tutorial/tagsSyntax.PNG">
  <br>
    <em>Tags Function Syntax Compared with HTML</em>
</p>

##### Different HTML tags accessible through tags function
* **h1("text") - h6("text"):** first level header to sixth level header
* **a(href = website.com, "text"):** hyperlink with the href argument
* **text:** character strings do not need a tag
* **p(“text”):** a new paragraph
* **em("text"):** emphasized/italic text
* **strong("text"):** strong / bolded text
* **code("code"):** code or monospaced text
* **br():** a line break
* **hr():** a horizontal rule
* **img(src = imageURL, height = , weight = ):** add an image

*NOTE:*
* You can also nest functions inside of others
  * For example,
  `tags$p("This is a", tags$strong("Shiny"), "app.")`
* Most of the `tags$.` functions come with a wrapper function, so you could take off the `tags$` and just call `h1()` instead.
* If you want to add static / text content, you could either
  * Use HTML() to pass a character string as a raw HTML

  <p align = "center">
    <img  width="100%" src="images in tutorial/rawHTML.PNG">
    <br>
      <em>Content Added with Raw HTML</em>
  </p>

  * Or, you could directly use the list of functions accessible through tags.
  <p align = "center">
    <img  width="100%" src="images in tutorial/tagsFunction.PNG">
    <br>
      <em>Content Added with Tags Function</em>
  </p>



### Create a Layout

Use layout functions to position elements within your app. Think of it as a 3D coordinate system with x being the length of your user interface, y being the width, and z being the layers.

Layout functions help us divide the UI into a grid. The two functions introduced below mostly work with the 2D coordinates.

##### fluidRow()
* Adds rows to the grid. Each new row goes below the previous one.  
<p align = "center">
  <img  width="100%" src="images in tutorial/fluidRow.PNG">
  <br>
    <em>fluidRow() Adds New Rows</em>
</p>

##### column(width = , offset = )
* Adds column within a row
* Each new column goes to the left of the previous column
* Need to specify the width and offset of each column out of 12
<p align = "center">
  <img  width="100%" src="images in tutorial/column.PNG">
  <br>
    <em>fluidRow() Adds New Rows</em>
</p>
* The first number is the width of the column, and you can also add how much you want to offset it by.
##### Assemble fluidRow() and column()
To place an element in the grid, call it as an argument of a layout function
<p align = "center">
  <img  width="100%" src="images in tutorial/layoutExample.PNG">
  <br>
    <em>A Layout Built with Layout Functions</em>
</p>

### Assemble layers of Panels

Remember we introduced our app as a 3D coordinate system? Now we will talk about how to group things on the z coordinate.

We use panels to group multiple elements into a single unit with its own properties.
<p align = "center">
  <img  width="100%" src="images in tutorial/12panels.PNG">
  <br>
    <em>12 Built-In Panel Functions </em>
</p>

#### wellPanel()

* groups elements into a grey "well" / rectangle  
<p align = "center">
  <img  width="100%" src="images in tutorial/wellPanel.PNG">
  <br>
    <em>Put the Slider and the Title Inside a "Well" </em>
</p>

Now as we can see, because we put the code for the slider and the title inside the `wellPanel()` function, on the UI page, those two elements are also grouped inside a grey well/box.

#### tabPanel()
* Creates a stackable layer of elements. Each tab is like a small UI of its own.
* Often uses with:
  * `tabsetPanel()`  
  `tabsetPanel()` combines tabs into a single panel.  
  It uses *tabs* to navigate between tabs.
  <p align = "center">
    <img  width="100%" src="images in tutorial/tabsetPanel.PNG">
    <br>
      <em>Combining multiple tabs into one panel with tabsetPanel() </em>
  </p>
  * `navlistPanel()`  
  `navlistPanel()` also combines tabs into a single panel.
  But here, it uses *links* to navigate between tabs.  
  <p align = "center">
    <img  width="100%" src="images in tutorial/navlistPanel.PNG">
    <br>
      <em>Combining multiple tabs into one panel with navlistPanel() </em>
  </p>

  * `navbarPage()`  
  `navbarPage()` replaces `fluidPage()` and combines tabs into a single **page**.  *Requires a title*
  * `navbarMenu()`  
  `navbarMenu()` combines tab links into a dropdown menu for `navbarPage()`

  <p align = "center">
    <img  width="100%" src="images in tutorial/navlistPanel.PNG">
    <br>
      <em>Using navbarMenu() with navbarPage() </em>
  </p>



### Use a Prepackaged Layout

#### sidebarLayout()
* Divides app into two sections
* Uses with sidebarPanel() and mainPanel()
* Add input/output elements as arguments into the two functions above

<p align = "center">
  <img  width="100%" src="images in tutorial/sidebarLayout.PNG">
  <br>
    <em>Combining multiple tabs into one panel with navlistPanel() </em>
</p>

### Style with CSS

* CSS - Cascading Style Sheets
* Framework for customizing the appearance of elements in a webpage, presents your webpage in a personalized way

<p align = "center">
  <img  width="100%" src="images in tutorial/css1.PNG">
  <br>
    <em>CSS Style Hierarchy </em>
</p>

You could style a webpage with CSS in three ways:

1. Link to an external CSS file
  * First place .css files in the *www* folder of your app directory. Shiny will share a file with your user's browser if the file appears in www.
  * Then set the theme argument of fluidPage() to the .css filename  

  <p align = "center">
    <img  width="100%" src="images in tutorial/link1.PNG">
    <br>
      <em>One Way to Link the Theme with a .css File </em>
  </p>

  * Or you could place a link in the app's header with to the file with `tags$head()` and `tags$link()`

  <p align = "center">
    <img  width="100%" src="images in tutorial/link2.PNG">
    <br>
      <em>Another Way to Link the Theme with a .css File </em>
  </p>


2. Write Global CSS in header
  * We could also write global CSS with `tags$head()` and `tags$style()` and `HTML()` ourselves

  <p align = "center">
    <img  width="100%" src="images in tutorial/link3.PNG">
    <br>
      <em>Write Global CSS in Header</em>
  </p>

  * Or you could save the CSS as a file in your app directory and include it with `includeCSS()`

  <p align = "center">
    <img  width="100%" src="images in tutorial/link4.PNG">
    <br>
      <em>Write Global CSS in a CSS File and Then Link It</em>
  </p>

3. Write individual CSS in a tag's style attribute

  * Set the style argument in Shiny's tag functions. Note that this will overrides global CSS or external CSS file.

  <p align = "center">
    <img  width="100%" src="images in tutorial/link5.PNG">
    <br>
      <em>Individual CSS in Tag's Style Attribute</em>
  </p>










## Resources to learn more

1. You could learn more about how to build a page that looks like a dashboard in the *shinydashboard* package
  * Find the package documentation/tutorial [here](http://rstudio.github.io/shinydashboard/)
  * Find Dynamic Dashboards with Shiny Webinar [here](https://vimeo.com/125265016)

2. Shiny uses the Bootstrap 3 CSS framework, which you can learn more about [here](getbootstrap.com)

3. Learn more about CSS & HTML
  * Find codeacademy tutorial [here](https://www.codecademy.com/catalog/language/html-css)
