# Deploy Rmarkdown Documents on GitHub Pages

Note: This tutorial is specific for deployment of OPA Dynamic Documents and takes the folder structure of OPA repository into consideration. However, it's applicable to all the Rmarkdown documents, which I'll annotate in the tutorial.

### Step 1. Add `index.html` to the root folder

Put this block of code at the very last of the YAML header. This chunk of code makes sure there is a `index.html` at the base level so that GitHub will know which html file to publish to GH Pages. It will recognize the file with the name `index.html`. At the same time, it updates the original html output we have in the `/code` folder as well.


```
knit:
    (function(input_file, encoding) {
    rmarkdown::render(input_file, encoding=encoding, output_file=file.path("..", 'index.html'));
    rmarkdown::render(input_file, encoding=encoding, output_file='01_final_opa.html');
  })
```
After you added the code chunk above to the `.Rmd` file, **Knit it** such that the `index.html` file gets written and updated.

If you want to only knit to a specific HTML file, you can do so by 1) deleting the `rmarkdown::render` code of the other file path 2) uncommenting the `rmarkdown::render` code of the other file and putting it outside of the function code chunk. This is because YAML header does not allow comments inside the function, but does support one-line comments outside of it.

*Note*: If you do not have the OPA folder structure, and your Rmd is already at the base folder, you can just change `output_file = 'file-name.html'`. But make sure `index.html` is at the base level and not in a subfolder, otherwise GitHub might fail to recognize it.

### Step 2. Add an empty file `.nojekyll` to the root folder

The easiest way to do this is on GitHub website. Click Add file and then change the file name to .nojekyll. Click save. But you could also do this locally, remember to push it to the remote repository.

### Step 3. Add a GitHub Page

1. Go to your remote repository and click on "Settings" on the top banner. Scroll all the way down until you see **GitHub Pages** as shown below.

![GitHubPages](./images/GitHubPages.png)

2. Choose the branch your `index.html` is on. (Most of the time it should be main/master.)

  Choose the folder. (Default should be `/(root)`, even though there is a `doc` folder in the OPA folder structure.)

3. Click Save, but expect to wait from half an hour to an hour for the website to be built.

 
