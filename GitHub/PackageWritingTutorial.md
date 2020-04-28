# Package Writing in RStudio
  * Tutorial
    * Packages allow for easy distribution of any functions apps etc through R
    * In order to create your own package:
      * write desired scripts, functions, files etc., and save them to one location
      * Select files in R Files window, go to file -> new project -> new directory -> R package, and add code files before clicking create project
      * This will open a new working directory with the file structure for a package that R expects
      * Some info then needs to be added before package will work:
        * Description file:
          * open the file and add title, author, etc.
          * add requisite packages under Depends: field
        * Add Data
          * create folder in package directory named "data"
          * save necessary data files into the newly created folder
        * Clean code
          * remove library statements from included code, and make sure code works as desired
        * add documentation to what your package does, and I/Os for each file
        * Run "check" within the build tab, and make sure package passes each check
        * Click Build & Reload, and this will finalize your packages
