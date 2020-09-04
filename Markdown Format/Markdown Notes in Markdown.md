## Markdown Notes in Markdown

##### 8/24/2020
##### Aleksandra Ma

`Ctrl + shift + m for preview of Markdown in Atom`

#### Links
* Simple link:
  > [link](the website link)

  + For example, here is link to [Google](www.google.com)

* Reference link that could be referenced multiple times:

  >  Here's a [website you want to check out][link reference name]
  >
  > [link reference name]: website link

  + If you need to change the reference link, you only needs to change it once at the bottom `[link reference name]:`
  + Example: This is just an example linked to [Google][google link]
  + Interesting. This is also an example linked to [the same Google][google link]




#### Images
* Inline image link, similar to simple link:
> ![image name](website link)

  + For example, here is the cover photo of Taylor Swift's new album _folklore_: ![Taylor Swift's new album cover](https://downinthep.it/wp-content/uploads/2020/08/taylor-swift-folklore-album-cover-1100.jpg)


* Reference picture that could be referenced multiple times, similar to reference links:

  > Here's a picture of ![picture name][link reference name]  
  >
  > [link reference name]: website links

  + Example: Here is a picture of a cute axolotl
  ![Axolotl][axolotl link]
  + Here is the same picture of the same cute axolotl
  ![same picture of Axolotl][axolotl link]

#### Blockquotes
* Use `>` in front of your quote
  ` > Quote Quote`
  + Example:
    > "Whatever exists is alike just and unjust, and equally justified in both." - Friedrich Nietzsche

* Use `>` in front of every line including the blank line if you want to quote multiple paragraphs

  `> Paragraph 1`

  `>`

  `> Paragraph 2`
  + Example:
    > "Do you wanna build a snowman?"
    >
    > "It doesn't _have to_ be a snowman."

* Use `>>` for nested Blockquotes

  > Quote 1  
  >> Nested Quote 1  
  >>> Nested Quote 2


#### Lists

* Unordered lists: `*` or `+`
  * For indented lists, indent the sub-bullets with one tab (tutorial says indent with at least a space but didn't work for mine)

* Ordered lists: `1. `, `2. `, etc.
* For indented content (might not be sub-bullets):

  1. Start with a new line by itself, which means there should be a blank line between your indented content and the bullet.

  2. Indent with at least one space, could potentially just use a tab.

* Could use blockquotes, bolded, italic accordingly.

#### Paragraphs

* Failed to break - simply changing to a new line

  first line
  second line

* Hard break - forcefully adding a blank line in between lines

  first line

  second line

* Soft break - add two space after each line before entering a new line

  first line  
  second line  

* Works in indented content, blockquotes, etc as well

#### Emojis
* `:emoji name:` for emojis  :stuck_out_tongue_closed_eyes:
 * [Here](https://gist.github.com/rxaviers/7360908) for a complete list of all emojis in markdown language









  [google link]: https://www.google.com
  [axolotl link]: https://alpha.aeon.co/images/afd7c22f-dde2-457d-847c-ed3b188f8011/header_sized-2168831.jpg
