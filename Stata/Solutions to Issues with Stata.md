# Solutions to Issues with Stata

If you have to access Stata through Citrix, you might run into errors running `.do` files while working on your reproduction. Some common issues are listed and explained below, with accompanying solutions.

This guide assumes familiarity with concepts like packages, file paths, working directories, etc. and is directed towards users new to Stata or who are using Citrix to access Stata for the first time.

### Issues with working directory

Your root directory is different when accessing Stata through a remote server like Citrix than when running files locally. Thus, when your working directory is set, either via the Stata command line or within your `.do` file, you need change your file path appropriately. The root directory in Citrix is `\Client`. For example, if my reproduction package was located at `C:\Users\myzha\Documents\GitHub\reprod-hamory-walker`, then my file path in Citrix would be `\Client\C:\Users\myzha\Documents\GitHub\reprod-hamory-walker`.

- If you need to manually change your working directory, you would enter a command like `cd \\Client\C:\Users\myzha\Documents\GitHub\reprod-hamory-miguel-walker`. Note the extra `\` before `\Client` that escapes the backslash in the root directory's name.
  - You will need to enter in this command each time you start up Stata.
- If your `.do` file has a line that changes your working directory, prefix your file path with `\Client` and an escaping backslash (like `\\Client\C:\Users\myzha\Documents\GitHub\reprod-hamory-miguel-walker`).

### Issues with packages/`.ado` files

Stata's packages are contained in `.ado` files. These files are stored in Stata's system directories. We cannot write to these system directories when using Citrix because we don't have permission to modify their server files. Thus, if you need to install certain packages to run your `.do` files, you will need to install those packages locally *and* tell Stata to look in your local folder when trying to use that package.

- Enter `adopath` in the command line to find out which directories Stata looks in when finding packages.
- Create a local folder where your packages will be installed. For example, mine are stored at `C:\Users\myzha\Documents\Stata\ado`.
- If you need to install packages from online, you would enter a command like `sysdir set PLUS \\Client\C:\Users\myzha\Documents\Stata\ado`. This command changes your `PLUS` directory (where Stata stores user-made packages installed from online) to the local folder you created.
  - Note that the file path includes the Citrix root directory `\Client`, along with an escaping backslash.
  - You will need to enter in this command each time you start up Stata.
- If you need Stata to be able to find `.ado` files that come downloaded with your reproduction package, you could enter a command like `sysdir set PERSONAL \\Client\C:\Users\myzha\Documents\GitHub\reprod-hamory-miguel-walker\ado`. This command changes your `PERSONAL` directory (where Stata stores personally made packages) to the folder that contains the downloaded `.ado` files.
  - When Stata looks for any `.ado` file, it looks in each directory listed in `adopath` for a folder named the lowercase initial of the package name, and then looks for the actual `.ado` file. For example, if Stata is looking for the package `fdr_adjustment.ado` in your `PERSONAL` directory, it will look first for a folder named `f` and then look inside for `fdr_adjustment.ado`.
    - Make sure to place your downloaded `.ado` files into a lowercase initial folder, so that Stata can find the file properly.
  - You will need to enter in this command each time you start up Stata.

After this, entering commands like `ssc install texdoc` will install packages appropriately to your `PLUS` directory. You can try entering commands like `which texdoc` to confirm that your packages are install properly.

---

For more details on these solutions, or solutions to smaller or more paper-specific issues, please look at the [readme](https://github.com/myzhang01/reprod-brodeur-cook-heyes/blob/main/README.md) for my 'Methods Matter' by Brodeur, Cook, and Heyes (2020) reproduction, or the [readme](https://github.com/myzhang01/reprod-hamory-miguel-walker/blob/main/README.md) for my 'Twenty-year economic impacts of deworming' by Hamory et al. (2021) reproduction. This guide may be updated as new issues and solutions are identified.
