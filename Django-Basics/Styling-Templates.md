[[_TOC_]]

# **Important styling rules** <span style="color: gold"> &#9733; </span>
- Do not create additional styling sheets without the express direction of your instructor. 
- Do not globally override bootstrap classes in any of the style sheets. Ex: `.card { color: blue }`
- Do not use linebreaks, i.e. `<br>` to add spacing between elements. Use margin or padding instead. 
- Do create new classes/Ids/increasing specificity to override the built in bootstrap styling. 

## **Styling Naming Convention**
There are going to be many students coming through writing CSS rule-sets, it's important to have a method to prevent existing rule-sets from being overridden accidentally.  When writing CSS, please follow this naming convention for new classes and ids that you create to greatly reduce the likelihood of CSS being overridden.

<div style="padding-left: 40px; font-size: 1.5em">

.<span style="color: rgb(200, 230, 240);">[Model]</span>-<span style="color: rgb(180, 210, 220);">[Page]</span>--<span style="color: rgb(160, 190, 200);">[Element/Name]</span> {

}
</div>

<div style="padding-left: 20px;">

<span style="color: rgb(200, 230, 240)">[Model]</span> - The name of the model that you are currently working on.
<span style="color: rgb(180, 210, 220)">[Page]</span> - The CRUD page that this class will be used on.
<span style="color: rgb(160, 190, 200);">[Element/Name]</span> - The element or the name you gave that element.

<span style="color: gold">Examples</span>: `blog_author-index--container` `rental-create--form` `comment-index--content_text`
</div>

