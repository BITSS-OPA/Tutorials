# Debugging in RStudio Notes/Tutorial
  * debugonce() - opens debugger next time function in argument is around
    * will open different console with traceback
    * stops code mid execution in order to understand what's happening line by line
    * location of stop is indicated by highlight on the script
    * values in environment will display the value at that snapshot in time
    * code can be stepped through line by line using the next button
    * press "stop" to exit debugger mode
  * browser() - insert this code into script at a point where you want debugger to open at.
    * alternative to debugonce()
    * press continue to run code up until next brower() statement
    * Analyzing error messages
      * test_it() - provides error with traceback ability and option to rerun with debugger
