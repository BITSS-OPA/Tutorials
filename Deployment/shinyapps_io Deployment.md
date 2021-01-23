# Deploy Shiny Apps on shinyapps.io

Note: For shiny app deployment, we are using shinyapps.io. But if we were to change deployment channel in the future, [here](https://github.com/AleksandraMaa/Notes/blob/master/shinyAppDeployment/proposal.md) is a comparison of the pros and cons proposal of different deployment methods (AWS, Shiny Server, Shiny Proxy, etc).

### Step 1. Install `rsconnect`

Run this command on R console
```
install.packages('rsconnect')
```

Then load it to your R session:
```
library(rsconnect)
```

### Step 2. Create shinyapps.io account

Go to shinyapps.io and click the *Sign In* button. Follow the prompted instructions, and complete the set up process.

### Step 3. Configure your `rsconnect`

To configure your `rsconnect`, we need the name of your account and token. To access this, go to shinyapps.io Dashboard and click on your profile on the top right. Select *Tokens* from the dropdown menu.

There will be a popup window like the image shown below:
![token](./images/tokens2.png)

Click *Copy to clipboard* and paste it into Console command line in RStudio.

Note that in the future, you might be asked to configure your `rsconnect` to the shared opa account. In that case, simply populate the name and the token field to the corresponding opa shinyapps.io account.

### Step 4. Publish your Shiny App

Open your shiny app and on the top banner right next to Run App button, there is a blue Taiji-looking button. Click on the dropdown menu, and select *Publish Application...*

![publish](./images/publish_icon.png)

Connect to your account or opa account in the future, name the shiny app, and then click Publish.

*Note:*
1. The code that you're trying to publish should not install any packages. Using `library(packagename)` for the packages you use is enough because shinyapps.io server will install onto the server automatically. Having `install.packages("package-name")` might instead result in errors.

2. If someone publishes the same app already to the shared opa account, you can simply click the Publish to *app_name* and it should update the same app instead of writing another one.

![published](./images/published.png)
 
