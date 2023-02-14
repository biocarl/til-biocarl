# Things to learn and investigate

-   Get updated what is available for vim emulation in IntelliJ, see [Changelog](https://github.com/JetBrains/ideavim/blob/master/CHANGES.md)
-   Privacy engineering, read [link](https://www.ipc.on.ca/wp-content/uploads/resources/7foundationalprinciples.pdf)
-   research value of limiting amount of open tabs
-   Do the [OWASP Juice workshop](https://owasp.org/www-project-juice-shop/)
-   learn about different ways of teaching [link](https://www.youtube.com/watch?v=L0xTXGahEus)
-   Do a proper scrum vs kanban write-up (pros/cons)
-   Read what it means to be a tech lead [here](https://noidea.dog/glue)
-   Learn about thread-safety and extend existing TIL based on this [here](https://www.baeldung.com/java-thread-safety)
-   Next to DRY, there is also the WET and AHA principle (see [here](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself))
-   watch [Patterns of Effective Teams](https://www.youtube.com/watch?v=lvs7VEsQzKY) and Dreyfus model matrix for pairing
-   Learn more about https, [tls handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/) and [Fingerprinting](https://daniel.haxx.se/blog/2022/09/02/curls-tls-fingerprint/)
-   Encoding and emojjs [here](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)
-   read about cycles of group development in software teams, [paper](https://www.researchgate.net/publication/247720440_Software_Team_Formation_and_Decay_Extending_the_Standard_Model_for_Small_Groups)
-   Things you can do with [draw.io](https://drawio-app.com/interactive-diagrams-with-custom-links-and-actions/)
-   E-Macs Shortcuts you can use in macOS: [link1](https://jblevins.org/log/kbd)
-   GSuite/Google Shortcuts: [Link](https://support.google.com/chat/answer/7649271?hl=en&authuser=0)
-   Version manager for all kinds of languages/tools: [asdf](https://github.com/asdf-vm/asdf)
-   🎧: [brown noise](https://www.youtube.com/watch?v=RqzGzwTY-6w) and [rainymood](https://rainymood.com/)

---


# 📅 14.02.2023 consulting: Why best practice are bad
- they do not assume context. Instead of formulas and recipes we need patterns and sensible defaults
- Best practices try to impose a clear domain on complex environment which is bound to  fail (see cynefin)

# 📅 14.02.2023 css: What are ways of debugging css code?
- First and foremost: Browser Developer Tools (Chrome/Mozilla)
- But sometimes you also want to visualize the boxes in a useful way
- Use `outline`, better than `border` because it does not take up any space
```css
* {
    box-sizing: border-box;
    outline: 1px solid limegreen !important;
}
```
- If you want to to visualize overlaps use a rgba `background` color
```css
* {
    box-sizing: border-box;
    background: rgb(0 100 0 / 0.1) !important;
}
```
- For both it makes sense to use `!important` in order to really overwrite every single css rule

# 📅 14.02.2023 css: What is the difference between root selector and html element selector?
- `html` tag is root element, top layer of inheritance
```css
html {

}

/* Equivalent, although this has higher specificity */
:root {

}
```
- `:root` always overwrite `html` selector. The distinction exists because CSS works on DOM structure and does not need html to work: *"As an aside, CSS is not just about HTML. It will work with a DOM created in any namespace from any source. In particular it will work with DOMs created from XML. So the root element is not necessarily the <html> element."*

# 📅 14.02.2023 css: How to style user selection?
- Style the text user selection with this pseudo-selector
```css
::selection {
  background: black;
  color: white;
}
```

# 📅 14.02.2023 html: How to align text with html only (deprecated)?
- You can align in html (without css), although it is **deprecated**
```html
<h1 align="center">This is centered text</h1>
```

# 📅 14.02.2023 fun: Unicode characters I love
- Fish sequence: 𓆝 𓆟 𓆞 ‧̍̊˙· 𓆝 °
- Bears: 
```plaintext
ᶘ ͡°ᴥ͡°ᶅ

٩ʕ•͡×•ʔ۶

ʕ◉ᴥ◉ʔ
```


# 📅 14.02.2023 intellij: Do auto-refresh for web preview when editing html/css
- Useful if you want to see the change directly while live-coding (although an explicit save is sometimes better for asking questions)
- To toggle just search for the following command `Reload page in built-in preview` and select either `On Save` or `On Change` 
- Further [reading](https://www.jetbrains.com/help/idea/settings-tools-web-browsers.html#ws_configure_browsers_reload_behavior)


# 📅 14.02.2023 revealjs: Exclude certain elements on pdf export
- When you export pdf via the `?print-pdf` and browser native print function you can make usage of the media query targeting print
```css
@media print {
    .exclude {
        display: none;
    }
}
```
- Just annotate the elements you want to exclude on print
- Not possible for hiding whole slides (alternative approach would be to write a pre-processor script deleting out those slides when printing)


# 📅 13.02.2023 git: What to do when git push freezes?
- One possible reason can be that the postBuffer for files is to small (default 1Mib)
```bash
git config --global http.postBuffer 157286400
```

# 11.02.2023 training: What is the central idea of Papert's education critique?
- Described in his book Mindstorms
- Additional resources: https://medium.com/bits-and-behavior/mindstorms-what-did-papert-argue-and-what-does-it-mean-for-learning-and-education-c8324b58aca4
- formal notations like F=m*a are useful for science and application but very bad for learning. Learning requires a much more experimental, iterative and intuitive process
- this iterative character is much more like children naturally learn
- do not start with the abstract but find a imperfect language which connects to the current worldview way of thinking of the students, creating resonance and relatedness
- those easy languages provide a trial and error experience and therefore learning, especially a easy programing language which provides visual output is very powerful (Papert's programing language Logo) since experience is very direct and correlated to actions
- this process of constructing knowledge is best achieved my not having a curriculum but more a open space which enables the students to grow on abilities and knowledge which is already there
- A good example is the box-model template, explore by your own how padding, margin and border works. What happens when you do A?

# 11.02.2023 training: Why are mental models so important as a learner?
- the ultimate goal of teaching should be developing a mental model in the student. That is the thing they we remember, refine and work with
- it does not need to be correct but it needs to be intrinsically constructed by making your own experiences, it will eventually float to some more truthy model
- mental models are created through understanding, filling in the gaps
- For example when teaching some Unix commands, it's not about knowing all the commands but more about piping, directories and environment variables and how they play together and how to find out missing information

#  11.02.2023 training: What is the difference between a tutorial and a manual?
- a tutorial is for a complete beginner to build up a basic mental model
- a manual is for a more advanced learner who wants fill in the gaps of his mental model

#  11.02.2023 training: How to do formative tests in a good way?
- *Target group*: Can be either for one person or whole group
- *Type of questions*: Question should be simple to answer and should not interrupt the lesson flow too much
- *Formats*: Multiple choice questions for the group are a good way of doing them (MCQ). Here it is essential to design them well, create distractors and discuss them if a lot of students voted for it. Design formative questions requires quite some bit of thinking and deep knowledge about the domain "to make a point" with this question. That's why it is key to deeply understand the topic first
- *Frequency*: Do formative tests every 15-20 mins for 1-2 minutes (makes sure that you know quickly when you loose a large part of the group)
- Formative feedback is a good basis for deciding where to go next
    - If the majority chooses the wrong answer you should go back explaining the concepts
    - If the minority chooses the wrong answer it depends on how well engaged and patient the group is (or come up with a bonus task)


#  11.02.2023 training: What are notional machines?
- A notional machine is a way of describing a basic mental model the learner should develop to associate the written code with the real device excecuting it
- A notional machine is a sufficiently precise model of how the language works alias how it interacts with the machine in order to get the job done
- At university level this would be for example the register automata or the Turing Maschine
- But for children or a more practical audience this is too abstract and more intuitive models can be catered to the student
- Those models open up a specific language which help to explain those concepts in a more pragmatic way
- Examples
  - Metaphors like box or whiteboard metaphor for variables
  - Representations of variables with e.g. stickies 
  - Simple rules everyone understands
  - Using existing knowledge e.g. explain while-loop with for-loop
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/notational.jpeg" /></p>

#  11.02.2023 training: What makes a good notional machine?
- Should be factually correct (most of the times)
- Can leave out information to reduce complexity (e.g. in Java explaining references is enough, no need to explain memory addresses)
- Use good metaphors
- In the words of du Bulay, a notional machine is "the best lie that explains what the computer does"
- See a good example for python [here](https://teachtogether.tech/en/index.html#s:models-notional)


#  11.02.2023 training: What is understood under the expert blind spot?
- When you are deep into a topic you easily forget how difficult it was at the beginning
- Tackle this by
   - Slowing down
   - Cultivate empathy
   - Always learn something new by yourself

# 📅 05.02.2023 revealjs: How to print a slide to pdf
- Append `?print-pdf` to localhost url (or use `reveal-md` tool)

# 📅 05.02.2023 revealjs: How to show a website fullscreen on a slide?
```html
<!-- .slide: data-background-iframe="https://css-tricks.com/snippets/css/a-guide-to-flexbox/" -->
```

# 📅 02.02.2023 intellij: What to do when cloning of private repos of organization fails?
- One possible reason is that the Intellij OAuth App does not have permissions to do so, change this [here](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-your-membership-in-organizations/requesting-organization-approval-for-oauth-apps)

# 📅 30.01.2023 revealjs: How to link with id anchors?
- This markdown slide
```plaintext
# This is a header
```
- You can link with an document fragment anchor like this
```bash
http://localhost:1948/intro.md#this-is-a-header
```
- Make sure that those are unique across the document


# 📅 30.01.2023 revealjs: How to host a folder of md slides?
- Just point it to the folder itself, use the parent folder of the slides otherwise the relative image links won't work


# 📅 24.01.2023 revealjs: How to use flex-box layout with markdown?
- You can always html in markdown slide, but in order to evaluate markdown inside a html text node you need to leave two line breaks

```plaintext
<script>
    .container{
        display: flex;
    }
</script>

# Slide title

<div class="container">


- A unorder list with entries
- second entry

This element will be in the second column

</div>
```


# 📅 24.01.2023 revealjs: How to use speaker notes
- In combination with `reveal-md` just start the line as follows
```plaintext
# Title
- Some bullet
Notes: This is a speaker note not visible
```
- In localhost presentation mode just press `S` for opening the presenter mode

# 📅 24.01.2023 github: HTTPS clone with 2FA
- Generate new token [here](https://github.com/settings/tokens)
- On `git clone` provide username and as password use the token

# 📅 23.01.2023 css: What is the purpose of css?
- Styling (visual appearance of content) like colors and fonts
- Layout (how content is layed out accross the available screen) - also adapting to different screen sizes
- Animations (keyframe animations, etc.)

# 📅 13.01.2023 css: How does flexbox work?
- the parent container decides about the layout of the child elements (inner display value), use it with `display:flex` (note the the out display value still remains `block` for the parent container, to change this you would do `inline-flex`)
- How does flexbox behave if there is limited space available?
	- per default it just shrinks the size so that all flex items stay in one line
	- with `flex-wrap:wrap` flex items start to wrap to the next line
	- if you want to prohibit that a single flex item does not shrink, keeps its original size you would use `flex-shrink: 0`
	- if you want to take make a single flex item take up the remaining space `flex-grow: 1` (number denote proportions to one another)
	- `flex-basis:0` does not consider the original size for growing. So all boxes start at zero length or height and grow from there. 
	- shorthand for the properties above: `flex: <flex-grow> <flex-shrink> <flex-basis>`, for example: `flex: 1 200px 0px` means that each item gets `200px` at least and after that it will be split according to priority (equally because all elements have `1`)
- Layout of elements are based on the axis (`flex-direction`)
- when direction is row-based (`row`) (*default!*)
	- main axis (horizontal across flex box)
	- cross axis (vertical across the flex box)
- when direction is column-based (`column`)
	- main axis (vertical across the flex box) 
	- cross axis (horizontal across flex box)
- There is three properties to control layout
- `justify-content`: aligns the flex items on main axis
	- `flex-start`: At the beginning of the main axis (default)
	- `center`: Align at center of main axis
	- `space-between`: Takes all the space (left/right position) and equally distributes the space between the flex items (`space-around` also considers spacing around the outer elements)
- `align-items`: aligns the elements along the cross-axis
	- `stretch`: Fill out all available space along the cross-axis (default). If the parent does not have a fixed height all elements will have the same size as the biggest element.
	- `flex-start`: Keep original size of the element in the cross-axis dimension (e.g. when `height` is set in a row based layout) and align to beginning of axis
	- `flex-center`: Keep original size but align to center of cross axis (*used very often for centering*)
- `align-content`: align content when there are multiple lines in a flex-box. It controls how all the elements will be laid out along the cross-axis of the container. This is usually only visible if the flex-box has a fixed height and space needs to be distributed. Possible values are `flex-end`, `flex-start`, `center`, `space-between`
- Change single elements
- If you want to overwrite the cross-axis alignment for a single flex item you can use the `align-self` property e.g. with values like `center`, `flex-end`, `flex-start`
- If you want to change the order (independent of dom element order) use `order: n`. Don’t use this, since this messes up the flow of the screen reader and also tabbing through form items.

# 📅 13.01.2023 css: How does css grid work?
- flexbox layouts across one dimension, the grid layout across two dimensions, use it with `display:grid`. Per default we only get a 1-column grid.
- the parent container decides about the layout of the elements (inner display value)
- Terminology:
- grid items, elements with a certain size and position
- grid tracks, row/columns that the grid is composed of
- grid gaps, referred as gutters
- Syntax:
```css
.grid-container {
  display: grid;
  grid-template-columns: 2fr 1fr ; /* Defines two columns, first having double the width as the second - fr, fractions*/
  grid-auto-rows: 50px; /* each not-defined row will have 50px of height. Without each row has the height needed by the content */
  grid-template-rows: 10px 20px; /* Alternatively you can explicitly define each row, here two rows. Usually you do not know the amount of rows but maybe you want to style the first row as a header with a specific height?  */
 grid-row-gap: 10px; /* specify space between rows, also grid-column-gap, gap for both */
}
```
- Note that fractions `fr` distribute only available space in fractions, if one element needs more space due to content there is less space to distribute
- To define either row or columns in the `grid-template-`(`rows`/`columns`) you can also use `repeat(5,1fr)` to define 5 equally sized rows/columns in one go (without having to write them out one after another)
- If you have content which overflow the height of the specified row size, but you still want to have a minimum height defined you can use  `grid-auto-rows: minmax(50px, auto)`. Which ends up using either the size of the content but at least `50px`.
- How to position specific elements across cells instead of using the auto-placement described above?
- Option 1: With grid-area you can assign specific elements to the grid layout 
```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-areas:
“header header” /* first row */
“sidebar content”
“sidebar content”;
}

.header {
  grid-area: header; /* The element with that class will be stretched out along the cells annotated with header*/
}
```
	- Option 2: Specify for each element in each column and row it should start and end 
```css
.header {
  grid-column-start: 1;  /* shorthand for both: grid-column: 1 / 3 */
  grid-column-start: 3;  /* You actually count the grid tracks/the empty space between as columns. To cover two cells you cross over three gaps. -1 spans to the last column */

}
```
	- for specifying a row use `grid-row-start`/`end` or the `grid-row` shorthand (this will still span over 1 column even without specifying it)
	- for spanning over `n` rows or columns just `span(n)` as property value
	- `span(1)` is the default for either column and row area 
- Align grid and items (*justify-* is always row direction, *align-* is always column direction)
	- `justify-content`, align elements horizontally, along the row-axis. For example `center`, `start`, `end`
	- `align-content`, align the elements vertically, along the column axis, for example `center` or `stretch` to stretch the elements along the y-axis
	- `justify-items`(row)/`align-items`(column) is to align/stretch them inside the different row/column. Per default both are set to stretch.
	- To overwrite item layout on a item basis you can specify `justify-self`/`align-self`
- the `auto` keyword automatically defines width based on the content (widest element in the column)

# 📅 13.01.2023 css: layout: What is understood under normal flow?
- the site layout without any css for example the behavior caused by default `display` like `block` and `inline` elements, the element order defined in the source and no stacking on top of each other
- the normal flow is just the default layout of the html elements, but you can change everything through custom css. Try keeping the semantically correct html elements even if they do not match your layout/visual preference and change it with css. For example if you need a list items `<li>` which are `inline`and not `block` do this with css instead of using `<span>` or something else which does not match the semantic meaning of list

# 📅 13.01.2023 css: layout: How do floats work and what are they still good for?
- the float annotated element is taken out of the normal flow and aligned for example to the `left` and all block elements following afterwards surround the content (like a floating image in a newspaper or drop-caps)
- Ideally you would add some `margin` to the annotated element to create some additional space (does not work to add margin to the text because the annotated element is not part of the normal flow anymore, not-seen by the text)

# 📅 13.01.2023 css: layout: What is positioning for?
- `position` is usually not used for the main layout but more for fine-tuning specific elements
- `static` is the default, element is part of the normal flow
- `relative` is a offset to the original position in normal flow
- `absolute` is moved out of the normal flow, only reference is the parent container
- `fixed` is moved out of the normal flow, only reference is the viewport
- `sticky` is a combination of `relative` and `fixed` (when it hits boundaries)

# 📅 13.12.2022 css: layout: How to do sticky positioning?
- Element stays in the normal flow until it hits the viewport position defined with `top`/`left` and then stays in a fixed position on the screen
```css
.positioned {
  position: sticky;
  top: 10px;
  left: 10px;
}
```
- the above pushes the element actually `10px` down and to the right. Think of it as pushing from the `top` and `left`
- A typical use case for sticky positioning is a scrolling index, where the current header of a sections sticks at the top and is overlapped by the next header

# 📅 13.12.2022 css: How does responsive design work?
- HTML itself (with no CSS) is fully responsive with a few exceptions like long lines of text, especially when adding CSS dynamic behavior is needed
- Responsive web design is a approach, a set of best practices to gather a good web experience to all types of devices
- Tools for responsiveness 
- Grid/flexbox is responsive by default
- Fluid images
- min/max values for properties
- Viewport units (`vw`/`vh` - % of viewport)
- Use of media-queries (adaptive layout)
- With media queries you would define certain breakpoints for the different targeted devices
	- for mobile usually a single-column layout
	- for wider screen devices a multi-column layout
	- have the mobile experience in mind first is a common practice in web design (mobile first approach)
	- best is to use relative units rather than absolute units for media queries
- Use `columns` to not having super long lines of text when reading
- If you want to adapt the font-size based on the viewport never use viewport values alone but combine it with a fixed value (otherwise the user won’t be able to zoom in)
- This would be a appropriate example
```css
.heading {
  font-size: calc(2rem + 1vw);
}
```
- Include the viewport meta tag in the header (always). This tells the browser to set the viewport to the dimensions of the screen
```html
<meta name="viewport" content="width=device-width,initial-scale=1" />
```

# 📅 13.12.2022 css: How do media queries work?
- media queries allow to set certain breakpoints and associate certain selectors to apply certain rule changes based if the media condition is true
- Syntax
	- Logical operators like `and`, `not`, `and only`
	- Mediatypes (they are always mandatory before specifying a rule)
- `screen` (screen media)
- `print` (printed document)
- `all` (both above)
- Orientation
	- `landscape`, usually desktop
	- `portrait`, usually mobile
	- Example: `@media (orientation: landscape)`
- Pointing device, is it is possible to hover over elements, touchscreen and keyboard only evaluate to false
	- `@media (hover: hover)`
- Complete example
```css
@media screen and (min-width: 80rem) {
  .container {
	background: gray;
  }
}
```
- Note: With a well-thought grid, flexbox layout you might not need media queries at all

# 📅 12.01.2023 css: layout: box-model: How does margin work for `block` elements?
- Margin values can be either positive or negative, creating additional space or remove additional space around the content-box (this can also cause overlapping)
- Margin collapsing: The margin values of two neighboring boxes are 
	- in case of the same sign, max(abs(marginA), abs(marginB)) - so always the most negative or positive
	- in case of different sign, being added to each other, marginA-marginB (in case margin is < 0)

# 📅 12.01.2023 css: layout: box-model: How does the box-model work for `inline` elements?
- Vertical margins, padding and borders will be applied but won’t affect other inline boxes to create space
- Horizontal margins, padding and borders will be applied and will also affect spacing to other inline boxes
- In simple language: Space creating attributes like margin, padding and border will always work on the element itself. So in all directions. But since it is an outer display value it can also end up influencing other `inline` elements around it. For `inline` this is only the case for left/right elements but not top/bottom elements. When applying padding in all directions, another element located left would be pushed away by the padded element (since it just got bigger - maintaining the layout) but a element located above the padded element would stay at its place. Padding the element even further could even end up overlapping the top element.
- Example (`<span>` is `inline` per default) - here the span only pushes elements to sideways
```css
span {
  margin: 30px;
  padding: 30px;
  background-color: green;
}
```
```html
<p>
This is a very long text with a <span>span</span> inside the text. Here is some more text to have some more lines coming after.
</p>  
```
- If you want to avoid the overlapping (since vertical elements are not pushed away) but still want to have it inline you can use `inline-block`. This also allows you to specify `width`/`height`

# 📅 12.01.2023 css: How to style borders?
- Usually we use a shorthand to target all sides and several properties at once
```css
.box {
  border: 2px solid green; /* width, style, color */
}
```
- but those can be also target individually e.g. `border-top`, `border-width` or even `border-top-width`
- To created rounded corners use the `border-radius` property provide two arguments for horizontal and vertical radius (in `px`, `em` or `%`). You can also target single sides like `  border-top-right-radius: 15% 35%;`

# 📅 12.01.2023 css: How to style text to be vertical?
- Just use the property `writing-mode`
```css
h1 {
  writing-mode: vertical-rl;
  color: white;
  background-color: black;
}
```

# 📅 12.01.2023 css: How to handle overflow?
- Overflow happens if the content does not fit into the box (and the box does not have appropriate space to grow e.g. through `height` constraint)
- Controlled by property `overflow` (per default `visible`, because you do not want to hide something and a user might miss a important information)
- Cropping overflowing content with `hidden`, to create a scroll-window use `scroll`
- Directions can also be specified via `overflow-y` or `overflow-x`
- For text you usually do not want to overflow but want to wrap the text (see `overflow-wrap` and `word-break`)
- Use `overflow: auto` to let the browser decide which scrollbars are needed

# 📅 12.01.2023 css: What is the difference between `em` and `rem` unit?
- Ems, `em` corresponds to `font-size` of the parent element (`rem` of root element), use for response designs. `1.4rem` is 1.4 times the fontsize of the root element of the document
- `%` work is the same way as `em` but is using e.g. `70%` of the parents element of a specific property. `em` is always using the `font-size` independent where the value is used
- Example: In first list font size is always double because it refers to parent element. In the second the root element is static, so nesting does not change the font-size
```css
html {
  font-size: 20px;
}

.em li {
  font-size: 2em; /* equivalent to ‘200%’ */
}

.rem li {
  font-size: 2rem;
}
```
```html
<ul class="em">
  <li>A</li>
  <li>B</li>
  <li>C
    <ul>
      <li>A.1</li>
      <li>A.2
        <ul>
          <li>A.2.I</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
<ul class="rem">
  <li>A</li>
  <li>B</li>
  <li>C
    <ul>
      <li>A.1</li>
      <li>A.2
        <ul>
          <li>A.2.I</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>
```

# 📅 12.01.2023 css: How does sizing work?
- there is two types of sizes
- intrinsic size e.g. the dimensions of a picture, or zero size of a div without content or some size with content
- extrinsic size is a size we explicitly define via constraints `width`/`height`. Can cause overflow
- upper/lower bounds for sizes e.g. `min-height`/`max-height` for dealing with variable amount of content (and avoiding overflow). Also for example for big images to not break the layout


# 📅 12.01.2023 css: What are replaced elements?
- css can not affect the internal layout of those elements
- Example: image, video and forms
- this is also the case when placed in a flex or grid layout
- as for `block` elements, replaced elements also respect `weight`/`height` attributes

# 📅 12.01.2023 css: How to use custom variables?
- Reuse specific values throughout the stylesheet
```css
:root {
  --primary-color: brown;
}
```
- `:root` selector allows to use the variable globally (for local scope use a appropriate selector like e.g. `h1`)
- variable names must start with a double dash, `--var-name` and are case-sensitive
- to reference a variable use the `var` function
```css
span a {
  color: var(--primary-color);
}
```

# 📅 12.01.2023 css: How to style text?
```css
p {
  color: blue;
  font-family: "Arial", Verdana, sans-serif; /* called font stack, fallback options if font is not available */
  font-size: 1.5em; /*always good to use for font-size*/
  font-weight: bold; /*or 100 - 900*/
  text-shadow: 1px 1px 1px blue, 2px 2px 1px green; /*double shadow in two colors*/
  text-align: center; /* center text */
  letter-spacing: 2px; /* space between letters */
}
```

# 📅 12.01.2023 css: How to use web fonts?
- Custom font will be downloaded together with css
```css
@font-face {
  font-family: "someFont";
  src: url("myFont.woff2");
}
html {
  font-family: "someFont", serif;
}
```
- Website for partially free `woff2` files are for example [dafont](https://www.dafont.com/de/), [fontsquirrel](https://www.fontsquirrel.com/)
- Instead going the route over font-faces people usually use free services like [Google Fonts](https://fonts.google.com/) (embedded via <link> element)



# 📅 11.01.2023 html: How to ensure responsiveness of images (without css)?
- Why without css? You end up not even loading unneeded images on dom load, since the html is taking care of it
- *resolution switching*: Having several resolutions of the image depending on the screen/layout (download low-resolution version on mobile) and/or vector graphics can be a good alternative
- 🤖: *To ensure responsiveness of images without CSS, you can use the srcset attribute on the img tag to specify different image files to be used at different screen sizes.*
```html
<img
  srcset="profile-400w.jpg 400w, profile-800w.jpg 800w"
  sizes="(max-width: 600px) 400px, 800px"
  src="profile.jpg"
  alt="alt text" />
```
	- chooses `profile-800w.jpg` if it is above `max-width: 600px`
	- `max-width` is a media condition resolving in a boolean 
- *art direction*: Focus on different cropped images to ensure the correct layout (focusing on having the most important part of the image visible)
```html
<picture>
  <source media="(max-width: 799px)" srcset="profile-400w-close-portrait.jpg" />
  <source media="(min-width: 800px)" srcset="profile-800w.jpg" />
  <img src="profile-800w.jpg" alt="alt text" />
</picture>
```
	- `<source>` contain the images options with the media conditions
	- `<img>` is the default case which needs to be provided in any case
- both *art direction* and *resolution switching* pick a different source depending on the screen size. In the first case however the browser does not have a choice which image to choose (since it enforces the intended layout). In the second case the browser can also consider available bandwith.
- How to deal with sizing? (fluid images)
	- `width: 100%` would not be good because a image with intrinsic width smaller then the parent container width would be stretched and would not look good
	- `max-width: 100%` does not force to stretch (image never breaks the boundaries of parent container) but also scales the image down if the intrinsic width of the image is higher
- How to make an image maintain the aspect ratio of the parent container (automatically crop it)?
```css
img {
height: 100%;
width: 100%;
object-fit: cover;
}
```

# 📅 11.01.2023 html: How to create tables?
- table and cells adapt to content and not to parent size dimensions
```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
    <th>Country</th>
  </tr>
  <tr>
    <td>Emil</td>
    <td>12</td>
    <td>Germany</td>
  </tr>
  <tr>
    <td>Lisa</td>
    <td>14</td>
    <td>Poland</td>
  </tr>
</table>
```
- `tr` stands for table row
- `td` stands for table data
- `th` stands for table header (also important for accessibility since screen readers can read out data associated to a column)
- Use the attributes `colspan=”n”` and `rowspan=”n”` to make a cell span over several cols or rows
- Defining `<colgroup>`/`<col>` in the table allows to create some style columns so css can access specific columns for styling (otherwise you would have to select every nth row via css which is quite tedious)
- Defining `<caption>` in the table adds a caption (important also for screen reader)

# 📅 11.01.2023 css: What is a reset/normalizer stylesheet?
- Browser already already come with some basic default formatting e.g. blue links, bold headers, bullet points, search box, button, space between paragraphs for html (even without CSS) often called browser defaults or user agent styles
- you can also disable those in your browser and you will see that there is no formatting left at all, not even line-breaks and spacing
- This styling can be inconsistent across browser, a reset stylesheet aims to remove those inconsistencies by applying some default values (first described by [meyerweb](https://meyerweb.com/eric/tools/css/reset/)
- Popular normalizer stylesheet is [normalize.css](https://necolas.github.io/normalize.css/)

# 📅 11.01.2023 css: How does compatibility work?
- CSS is in the end just a specification published by the [CSS Working Group](https://www.w3.org/Style/CSS/)
- Browser have to implement that specification and make sure that a certain piece of CSS code results in the define visual outcome. Although all major browser manufacturers comply to those specifications at some point they usually take some time to comply
- Backwards compatibility is usually always ensured (a website from the year 2000 should still run today). Also old browser won’t break a website since declarations which are not understood by the browser are just ignored.
- Usually you find Browser compatibility tables online which show which feature is rolled out in which browser

# 📅 11.01.2023 css: What are the ways of adding CSS to a html document?
- External stylesheet (put this in your head), relative path or absolute url
```html
<!DOCTYPE html>
<html lang="en-GB">
  <head>
    <meta charset="utf-8" />
    <link rel="stylesheet" href="styles.css" />
  </head>
```
- Internal stylesheet
```html
<!DOCTYPE html>
<html lang="en-GB">
  <head>
    <meta charset="utf-8" />
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }
    </style>
  </head>
```
- Apply css directly on a single html element
	- this should not be done since this mixes content and styling and will require multiple edits for a single style change
	- Exceptions are for example when you have only a single html file in CMS
```html
<h1 style="color:red;">This is a header</h1>
</html>
```

# 📅 10.01.2023 html: How to style text with html?
- `<b>`/`<strong>` for bold
- `<i>` for italic
- `<u>` for underlined
- `<mark>` for marked text
- `<small>` for smaller text
- `<del>` for deleted text (crossed through)
- `<sub>`/`<sup>` for sub/superscript

# 📅 10.01.2023 html: How to create hyperlinks?
- this is what makes the web a web
- 🤖: *To create hyperlinks, use the a tag with the href attribute to specify the URL to be linked to.*
- Syntax
```html
​​<p>Here is a
    <a
href="https://www.google.com/"
title="Some description">
link
    </a>
</p>
```
- `href` also called the target or hypertext reference
- `title` provides some description which appears as tooltip on hover
- Both `title` and link text are important for screen readers but also for SEO
- you can make everything a link (just provide it as child to the `<a>` element)
- Linking inside a document: *Document fragment*
	- You just separate with `#` to link to a specific anchor/id of the target document: `<a href="about.html#last_section" </a>`
	- or you omit target if it is the current document, `<a href="#last_section" </a>`
- If you want to open the link in a separate tab provide `target="_blank"` as an additional attribute
- Linking for downloading a file
	- make it clear in text and description that it is not just a link to another website
	- using the `download="filename.exe”` will provide the user with a filename when persisting the file
- Linking to email address
	- `<a href="mailto:bioflash@web.de">Send me</a>`
	- you can send the mail with cc, bcc, subject and body ([reference](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks#specifying_details))

# 📅 10.01.2023 html: What are description lists?
- 🤖: *Description lists are used to create a list of terms and their associated descriptions. The dl tag is used for the list container, dt for the term, and dd for the description.*
- A little bit like `ul`/`ol` in the sense of that this is a list structure but no nesting allowed and used for describing semantic value pairs
- This can be used for example by search machines to extract a glossary out of a article (you can also have multiple terms (`<dt>`) per description (`<dd>`) or the other way round
- Example of [w3](https://www.w3.org/TR/html401/struct/lists.html#h-10.3)
```html
<dl>
  <dt>Dweeb</dt>
  <dd>young excitable person who may mature into a ...</dd>

  <dt>Hacker</dt>
  <dd>a clever programmer</dd>

  <dt>Nerd</dt>
  <dd>technically bright but socially inept person</dd>
</dl>
```

# 📅 10.01.2023 html: How to quote html?
- By using the `<blockquote>`, a `cite` attribute optionally provides the source of the quote
```html
<blockquote
  cite="www.google.com">
  <p>
    This <strong> normal html code which will be evaluated as plain text in the browser</p>
</blockquote>
```
- for inline quotations use `<q>` (with optional `cite` attribute)

# 📅 10.01.2023 html: How to create abbreviations/acronyms?
- 🤖: *To create abbreviations/acronyms, use the abbr tag with the title attribute to provide the full term.*
- the text node of `<abbr>` contains the abbreviation and the `title` attribute the long form (which is shown on hover)
```html
<p>This <abbr title="Very bad word">@/$&</abbr> is happening again! :(</p>
```
- `<acronym>` is deprecated

# 📅 10.01.2023 html: How to render code in html?
- Most of the below tags will style the code with monospace font by default, they are more for semantic clarity and/or will be targeted by css frameworks (like styling of code)
- Use `<code>` for block element and code formatting
- Use `<pre>` if you want to keep whitespaces and newlines
- Use `<var>` for describing variable names.
- Use `<kbd>` for key names of keyboard
- Use `<samp>` for terminal output

# 📅 10.01.2023 html: What are semantic elements and why do they exist?
- 🤖: *Semantic elements are HTML tags that give meaning to the structure of the content on a web page. They exist to help search engines and assistive technologies understand the purpose of the content.*
- Semantic elements clearly describe the content contained whereas non-semantic like `<div>` or `<span>` do not
- although this does not impact layout or visuals (done with css) this is very important for
- search engines, since search engines depend on this they punish or reward this with different SEO outcomes
- visually impaired people who navigate a webpage via a screen reader and depend on those tags for understanding the logical structure of the document
- developers, easier to read (in contrast to a "div soup")
- Following a convention of semantic elements allow to target them directly with css and therefore not needing classes and id’s (in many cases). There is even [drop-in css boilerplate](https://dohliam.github.io/dropin-minimal-css/) frameworks which allow you to style the whole document based only on the element tags
- Some of them are to structure the common areas of a website

<p align="center"><img height=400 src="https://www.w3schools.com/html/img_sem_elements.gif" /><p><br>

- header: heading, logo and tagline of website (`<header>`)
- navigation bar: consistent layout across the pages, links to other pages (often together with header) (`<nav>`)
- main content which subsections like article and section (`<main>`, `<article>`, `<section>`). This is unique to the page and will always change from page to page. A section should always start with a heading and contain several articles or the other way round.
- sidebar: supplements main content (`<main>`) like quotes, info, or related prodicts, secondary navbar (context dependent) (`<aside>`)
- footer: copyright, fineprint (`<footer>`) 

# 📅 10.01.2023 html: How to debug html?
- Browsers are usually parse and interpret HTML permissively, meaning that even with errors the page is still rendered (browsers usually have built-in mitigation strategies how to deal with erroneous html, compare source code and created dom by the browser)
- Most commonly is looking at the code and get support by IDE for missing enclosing tags etc.
- Or validate html with [Markup Validation Service](https://validator.w3.org/)  by W3C
- Further tips
	- Talk through what the code should do
	- Properly intent the html document
	- Check for closing tags

# 📅 10.01.2023 html: How to add images?
- Never use images hosted in places you do not own and you have to explicit permission linking from (called hotlinking)
- Use a `alt` text for accessibility/search engines/bad internet connection (same for `title`)
```html
<img
  src="images/profile.jpg"
  alt="A profile picture of a young, middle aged man, smiling" />
```
- Attributes of  `width`and `height` also reserve empty space when image is not yet loaded - so the layout does not change upon load (for scaling etc. use css)
- If you want to create captions in a semantic/accessible way you should use `<figure>`
```html
<figure>
  <img … />
  <figcaption>
	This is a caption below the image shown.
  </figcaption>
</figure>
```
- A caption is also for people who see an image, the alt text is a substitute for the picture. Caption and alt text should not be identical

# 📅 10.01.2023 html: How does embedding a 3rd party website work?
- when embedding of other webpages makes sense and is allowed: youtube videos, statistics and badges of social media, payment buttons/options
- In order to embed a website (via `<iframe>`) the host server needs to allow this (see [X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)), preventing clickjacking
```html
  <iframe
    src="www.hostserver.com"
    width="100%"
    height="500"
    border: none
    allowfullscreen
    sandbox>
    <p>
        Fallback for browsers that don't support iframes
    </p>
  </iframe>
```
- set the `src` attribute only after page has loaded to reduce loading time (since it would have to wait also for the host server response)
- always set the `sandbox` attribute, not allowing the externally website anything (like calling javascript or manipulating the parent documents dom)


# 📅 10.01.2023 css: How are conflicting styling rules resolved (cascading/specificity/inheritance)?
- In general: In case of a conflicting declaration block not the entire rule takes precedence but rules for single attributes are prioritized
- Cascading is the algorithm which defines which rules is applied in the end and follow the following increasingly important stages:
- Source-Order
- Specificity
- Origin: browser style, CSS from a browser extension, CSS from dev (see also layers)
- Important-Statement
- **Specificity**: Can be visualized like a waterfall: “At the top, we have more general selectors and as we trickle down specificity grows more and more… specific.”
- Most general: Universal selector -> Elements -> Classes -> IDs -> Inline Styling -> !important: Most specific
- See more [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)
- **Source order**: In case two selectors have the same precedence the rule defined last in the stylesheet will be applied (source order). You can even have the same rule in the same declaration block. This becomes useful for a fallback strategy (in this case if the `calc` function is available the line will be ignored but the previous line still is evaluated) 
```css
.box {
  width: 200px;
  width: calc(100% - 10px);
}
```
- *Inheritance*: Some rules applied on parent elements are passed down to child elements.
- Inheriting properties: `color`, `font-family`
- Not-Inheriting properties:  `height` , `width` , `border` , `margin` and `padding`
- Inheritance can be checked online e.g. for [color](https://developer.mozilla.org/en-US/docs/Web/CSS/color#formal_definition)
- Independent of the default inheritance properties you can also explicitly define a inheritance behavior described [here in depth](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance#controlling_inheritance) 
```css
.parent-element {
    color: blue;
}

.child-element-1 { /* inherit color from parent */
    color: inherit;
}

.child-element-2 {
    color: revert; /* default styling of browser */
}
.child-element-3 {
      all: revert; /* default styling of browser for all attributes */
}
```

# 📅 10.01.2023 css: syntax: What is the general syntax?
- CSS declaration block
```css
/* CSS declaration block */
p {  /* selector*/
  color: blue;  /* property and value combined = CSS declaration */
}
```
- property and values are american english and case-insensitive and must not contain whitespace
- wrong syntax of CSS declaration will be simply ignored

# 📅 10.01.2023 css: syntax: What are CSS functions?
- CSS also supports some native functions to calculate things at runtime
```css
.square {
width: calc(90% - 10px);  /* 90% of the parent width*/
}
```
	- other functions are `transform: rotate(0.8turn);`, `color: rgba(200,200,200,0.1);`


# 📅 10.01.2023 css: syntax: What are CSS @rules and how you use them?
- @rules are some instruction to the browser which modify CSS behavior
- Some examples
- `@import`: Import another stylesheet e.g. `@import "partial.css";`
- `@media`: Only execute enclosed declaration block if media condition resolved to true
```css
@media (min-width: 480px) {
  nav {
    background-color: gray;
  }
}
```
- for more see [here](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule) 

# 📅 10.01.2023 css: syntax: What are shorthand properties?
- Summarizes several CSS declarations into one line
```css
padding: 1px 2px 3px 4px; /* clockwise from the top */
/* Equivalent statements */
padding-top: 1px;
padding-right: 2px;
padding-bottom: 3px;
padding-left: 4px;
``` 
- Be careful with incomplete value in shorthands. CSS will fill those out with default values leading to potentially overwrite old values you did not intend
- Other shorthands are for example `font`, `background`, `border` and `margin`

# 📅 10.01.2023 html: What is a dom tree?
- 🤖: *The DOM (Document Object Model) tree is a way of representing the structure of an HTML or XML document as a tree-like structure, where elements are the branches and the text content is the leaves of the tree.*
- When the browser downloads the html it parses it and represents the document structure as a tree in memory, a document object model (dom)
- Each element, attribute or text content becomes a dom node
- CSS will be downloaded and parsed in a second step and will be then applied to each node before the dom is rendered to the user

# 📅 10.01.2023 css: What are CSS cascade layers?
- Allows you to put your css rules in different layers so that they take precedence over a different set of rules (independent of specificity or source order)
- In general the following order of priority: default browser style sheet, user style sheets, author/developer styles sheets, important declarations
- In the author/developer style sheets we have to possibility to introduce addition ordering with cascade
```css
/* from lowest to highest priority */
@layer basic, partials, custom, special-overrides;

/* Populate layers */
/* via external style sheet */
@import 'partial.css' layer(partials);

/* via direct snippet*/
@layer custom {
h1 {
  color: blue;
}
}

/* style with no layer have the highest priority */
a {
  color: pink;
}
```

# 📅 10.01.2023 css: layout: box-model: What are block and inline display types and how are they connected to the box model?
- Everything in css is a *box*, the layout is determined by the `display` property and either targets
- *outer display type*: This does not impact the child elements of the container but how it interact with other elements, the pageflow
- `block`
	- takes up the full width (nothing next to it)
	- e.g. default of `<div>`
- `inline`
	- takes up minimum amount of space possible (can’t have `width`/`height`)
	- e.g. default of `<span>`
- `inline-block`
	- same as `inline` element but you can set `width`/`height`
- `none`
	- box not displayed
- or the *inner display types* like `flex`/`grid`/`flow-root`/`table` which impacts the layout of the child elements of the styled container.
- A element always has both inner and outer display type (even if it is not explicitly stated in the display type). Sometimes you end up combining both types for the `display` value. For example `inline-flex`.
- But you can also combine outer display types like `inline-block`. For example for a button you would use an `inline-block` because we do not take up all the space like in `block` while still being able to provide a `width`/`height`. This also allows us to have several buttons in the same line
- The *box model* (content, border, padding, margin) fully applies to `block` elements and only partially to `inline` elements


# 📅 10.01.2023 css: layout: box-model: What is the difference between inner and outer display values?
- [source](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model#outer_display_type)
- Outer display values: Looking at the outside elements for deciding how it is interacting. For example `block` changes surrounding elements by introducing line breaks before and after (remember a `block` box has full-with). Example:
```css
.block {
  display: block;
} 
```
```html
<p>This is a paragraph with several <span class="block">spans</span> and <span>another one.</span>comes right after.</p>
```
- Inner display values: Looking at inside elements and deciding on layout accordingly. For example the `flex`/`grid` property does not impact neighboring elements but just child elements.
- So if you select `flex` as display type you only define the inner display value, the outer display value will default to a value (e.g. `block` if it is a `<div>`). To still also define the outer display value you can create combinations e.g. `inline-flex`. So the element behaves on the outside like a inline element and on the inside you create flex logic. Explained in depth [here](https://www.youtube.com/watch?v=ty4lnEUy7SY)

# 📅 09.01.2023 xml: What is xml and what is it used for?
- Stands for eXtensible Markup Language, which is a widely used standard
- the structure is described in the data itself via nested tags and attributes
- applications:
	- Data transfer e.g. SOAP
	- Web: HTML and XML share SGML as common ancestor
	- Formating: PDF, Word, Powerpoint documents
	- Configuration data

# 📅 09.01.2023 xml: What are the basic elements of a xml document?
- XML prolog: Should include version and character encoding
```xml
<?xml version="1.0" encoding="UTF-8"?>
```
- Root element: Single parent element at the very top (in html this is the `<html>` element)
- XML element
- Need to have opening and closing tags
- tag names are case-sensitive
- attribute values need to be defined in quotes `<element style=”value”> </element>`
- Comments are created with this: `<!-- A comment -->`

# 📅 09.01.2023 html: What are the basic elements of a html document?
- A html element has opening, closing tag and a content (there is also a empty element which has only a opening tag)
- A content can contain other elements or a text or comments (later parsed as element, text and comment nodes in the dom)
- A html element can have attributes with values


# 📅 09.01.2023 xml: What are the differences between html and xml?
- html tags are case-insensitive (where xml is case-sensitive)
- html has predefined tags (like <h1>, <a>) where in xml it has to defined in a spec

# 📅 09.01.2023 html: What are custom elements?
- introduced with html5
- allow users to reuse html snippets (like components for frontend-frameworks)
- done by defining a javascript class representation of the new (or to be extended html element)
- custom elements must contain a dash (e.g. `<my-app></my-app>`)
- Read more [here](https://developer.mozilla.org/en-US/docs/Web/Web_Components/Using_custom_elements)


# 📅 09.01.2023 html: What is the doctype declaration doing at the beginning of a document?
- 🤖: *The doctype declaration at the beginning of a document is used to specify which version of HTML the document is using.*
```html
<!DOCTYPE html>
```
- this is not a html tag but a information to the browser what to document to expect and render
- declaration is not case-sensitive
- the doctype allows you to invoke different rendering modes in the browser and different html specs (also xhtml) - see here [here](https://www.w3.org/QA/2002/04/valid-dtd-list.html)


# 📅 09.01.2023 html: What are void elements?
- 🤖: *Void elements are HTML tags that don't have a closing tag and don't have any content. Examples include `<img>` and `<br>`.*
- html tags which do not require a closing tag
- they are called void elements because they are empty (sometimes also referred as singleton tags or empty elements)
- those include: `<br>`, `<col>`, `<img>`, `<hr>` and a lot more html5 tags (e.g. media tags)
- you do not need a trailing slash like `<br/>` (only used for xhtml compatibility)

# 📅 09.01.2023 html: What is xhtml?
- 🤖: *XHTML is a version of HTML that adheres to stricter rules for well-formedness, such as all elements must be closed and all attributes must have a value.*
- was designed to create a bridge between html and xml to have a common spec
- for example a void element like `<br>` in html is not valid xml since every element needs a a closing tag. In xhtml you need to write `<br/>`
- should not be used anymore, use html5 instead
-  only in very special cases where you need both properties e.g. chat logs which you want to conveniently render in the browser and use all the xml parsing capabilities and tools (e.g. with XSLT) 

# 📅 09.01.2023 html: What is the head element used for?
- 🤖: *The head element is used to contain metadata about the document, such as the title, which is used by browsers and search engines.*
- Used for metadata and is not displayed/rendered by the browser
- document title (also shown in browser tab or when saving as favourite)
- character set
- styles (load external style sheets) - with `<link>`
- scripts (load external javascript) - with `<script>`
- custom favicons (comes from ​​”favorites icon”)
- metadata for search engines like author, keywords (formerly), description (SEO) - this also pops up in the search results then (or when pasting a link on social media)
- other functionalities like automatic refresh of the page (see `meta/http-equiv/refresh`)
- Should live inside html tag and before body tag 
- Example
```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="favicon.ico" type="image/x-icon" />
    <meta
        name="description"
        content="Some description text." />
    <title>My title</title>
  </head>
  <body>
    <p>Visible body</p>
  </body>
</html>
```

# 📅 09.01.2023 html: How to add a emoji as a favicon?
- Define this in the html `<head>`
```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <title>My title</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>👵</text></svg>">
  </head>
  <body>
    <p>Visible body</p>
  </body>
</html>
```

# 📅 09.01.2023 html: How to load javascript only when dom is rendered?
- with the `defer` keyword
```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <title>My title</title>
    <script src="script.js" defer></script> 
  </head>
  <body>
    <p>Visible body</p>
  </body>
</html>
```

# 📅 09.01.2023 html: How to specify different languages in html?
- Important for search engines and browsers to filter for languages or offer translation services
- Can be applied on document level or to specific element with the `lang` keyword
```html
<!DOCTYPE html>
<html lang="en-US">
   <body>
    <span lang=”zh-Hans”>野外</span>
  </body>
</html>
```

# 📅 09.01.2023 html: What is the difference between block and inline elements?
- For block elements, every element after a block element will appear on a new line
- Inline Elements do not trigger a line break, often used for text e.g. `<a>`, `<em>`, `<strong>`

# 📅 09.01.2023 html: What are boolean attributes?
- booleans in html are usually modelled by just repeating the attribute as the value (resulting to true)
```html
<input type="text" disabled="disabled" />
```
- which also can be written as such
```html
<input type="text" disabled/>
```
- for a falsy value just do not set the attribute


# 📅 09.01.2023 html: How to write special characters?
- Possible with the so called entity references
- `<`: `&lt;`
- `>`: `&gt;`
- `"`: `&quot;`
- `'`: `&apos;`
- `&`: `&amp;`
- For more see [here](https://en.wikipedia.org/wiki/List_of_XML_and_HTML_character_entity_references)

# 📅 09.01.2023 html: What is the purpose of HTML?
- Provide layout and formatting
- Basic styling (without css!)
- Help out search engines to find things (e.g. `<author>` or `<article>` tag), adding a semantic structure

# 📅 14.12.2022 java: oop: What are the basic terms with easy explanations?
- things a object knows about itself -> instance variables
- things an object can do -> methods
-  A `class is not the `object: e.g. a list of contacts, a contact form is `class` defining how a contact looks like, and `object` is a specific entry
- `instance` is another way of saying `object`
- `constructor` Is a `method` which runs if you create a new `object` and which accepts parameters you can use to create a certain initial state. 
- `class` is a blueprint for a `object` and tells JVM how how to make an object of that type


# 📅 14.12.2022 fun: What are some common animal sounds? (onomotopoeia)
- [source](https://www.fluentu.com/blog/english/animal-sounds-in-english/)
- Cats — `meow`
- Dogs — `woof`
- Horses — `neigh`
- Goats and sheep — `baa`
- Pigs — `oink`
- Cows — `moo`
- Donkeys — `hee-haw`
- Chickens — `cluck`
- Roosters — `cock-a-doodle-do`
- Birds — `chirp`
- Mosquitoes — `buzz`

# 📅 14.12.2022 programming: How do I approach a programming problem?
- Read through the whole problem statement (!)
- Which data types are involved. Do I already have all of them available or do I have to convert something?
  - Which of the types are primitive? I can do very little with them (look for static methods `Primitive.method`) or use the wrapper types instance methods
  - What are reference types?
- Learn how to read documentation of available methods with its parameters
- What is the first step I can do to come close to the solution? Can I simplfy the problem somehow?

# 📅 14.12.2022 intellij: Convenient tools 
- Show shortcuts when using the mouse, [key-promoter-x](https://plugins.jetbrains.com/plugin/9792-key-promoter-x)

# 📅 14.12.2022 java: Why can't you overwrite static methods?
- static methods in Java are resolved at compile time
- since method overriding is part of Runtime Polymorphism, static methods can't be overridden

# 📅 14.12.2022 training: What will you learn in a coding bootcamp?
- You will start walking but it will take a lot longer to master the skill
- Recommended [article](https://norvig.com/21-days.html)

# 📅 14.12.2022 memes: What are some good source for memes?
- [xkcd.com/](xkcd)(and [site](https://explainxkcd.com/wiki/index.php/1188:_Bonding) which explains some of those)
- [/r/ProgrammerHumor](https://www.reddit.com/r/ProgrammerHumor/) on reddit
- SD,MJ etc ;)


# 📅 14.12.2022 h2: How to access the ui locally?
- Add this in `application.yaml/.properties`: `spring.h2.console.enabled=true`
- And access via url: `http://localhost:8080/h2-console`


# 📅 08.12.2022 vuejs: How to style bind css functions?
- Treat the function as a string and concat the function call if you have arguments
```html
<li :style="{filter: 'brightness('+ (1 - depth/10) +')'}"  >{{name}}</li>
```

# 📅 08.12.2022 github actions: How to reuse workflows?
- For the workflow you want to reuse change the `on` trigger to `on: [workflow_call]`
- and reference that workflow from another workflow like this
```yaml
name: "Some other workflow"
run-name: ${{ github.actor}} is running the build job
on: [push]
jobs:
  call-build-job:
    uses: ./.github/workflows/build-job.yaml
```

# 📅 08.12.2022 github actions: How to upload and download artefacts/files?
```yaml
name: "Workflow for uploading/downloading files"
on: [push]
jobs:
  upload-download-files:
    runs-on: ubuntu-20.04
    steps:
      - name: "Upload file"
        uses: actions/upload-artifact@v3
        with:
          name: "Users.txt"
          path: ./files/users.txt
     - name: "Download file"
       uses: actions/download-artifact@v3
       with:
         name: "Users.txt"
```

# 📅 08.12.2022 devops: What is continous integration?
- The idea is that developers should aim for integration into the shared repository as soon as possibily
- Integration here means resolve merge conficts but also pass the automated suite of tests/and or manually validate new changes
- The overall goal is that software is always in a state where it can be released and deployed to production
- One methodlogy to achieve this is for example trunk-based development (avoiding branches alltogether)

# 📅 08.12.2022 devops: What is devops?
- Devops is a general approach which tries to improve the path to production
- it puts emphasis on people, processes, and technology in order to focus on the fast iterations and product value (agile mindset)
- the general idea is that infrastructure related tasks should be at best fully automated so that developers can focus on developing new features or incorporate collected feedback

# 📅 08.12.2022 devops: What is the difference between Continuous delivery and continuous deployment?
- They are both almost identical, they both encompass building and testing and releasing updates
- The difference is that Continuous Delivery software is only released but not deployed to a production environment
- This allows the team to manually review changes and decide if the changes should be deployed to production
- With Continuous Deployment the only quality gate before source is deployed to production are the tests, everything is fully automated

# 📅 07.12.2022 vuejs: How to share css between components?
- Extract into shared css and do this in each component
```html
<style scoped>
@import "@/assets/shared.css";
</style>
```

# 📅 06.12.2022 vite: How to debug preview app?
- Disable minify of js in `vite.config.js` so you can inspect javascript in browser
```json
{ //config
    build:{
        minify: false
    }
}
```
-

# 📅 06.12.2022 npm: How to list a dependency tree?
```bash
npm list --depth=10
```

# 📅 06.12.2022 npm: How to update dependencies?
```bash
npm update --save // to store it in package.json
```

# 📅 06.12.2022 vite: How to user-test production ready app?
```bash
# Instead of only using hot-reload dev command with vite
vite
# You should generate the build files locally and preview it
vite build && vite preview
```
- for the preview to work you might need to adapt the `vite.config.js` (since local server is spawn relative to src dir)
```javascript
{ //config
  base: '/dist/',
}
```

# 📅 06.12.2022 git: How to create a tag and push it?
```bash
git tag TAG_NAME
git push origin --tags
```

# 📅 06.12.2022 css: How to preverse whitespace in a text node?
```css
#target{
    white-space: pre; /* use pre-wrap to keep wraps*/
}
```
```html
<div id="target">H   e ll   o </div>
```


# 📅 06.12.2022 css: What are some interesting use-cases for pseudo-classes?
- `:first-letter`, matches first letter of text (same for `:first-line`)
- `:first-child`, matches first child (same for `:last-child`, `:nth-child(2)`)
- `:hover`, matches element when it is hovered over

# 📅 06.12.2022 css: How to create element counters?
- In css you can keep track the number of times an element appears on a page with the counter variable you define
- In this example you have several `.bubble` elements on the page and you want to number them
```css
.bubble{
    counter-increment: myCounter 1; /* you can also supply a counter increment, defaults to 1 */
}

.bubble:before{
    content: "(" counter(myCounter) ")" ; /* increments counter and returns it*/
}
```

# 📅 06.12.2022 css: layout: How to do absolute positioning?
- Absolute positioning allows you to position an element relative to its parent container
```css
#target{
    position: absolute;
    top: 0; /* you can also use relative units like 50% */
    left: 0;
    z-index: 4; /* High number puts the element in the foreground */
}
```
- this only works if the parent container is also positioned in absolute or static way, if not the reference is the viewport. (but won't stick to the viewport as in fixed or sticky)

# 📅 06.12.2022 css: layout: How to do fixed positioning?
- Fixed positioning allows you to position an element relative to the browser window.
- The element will remain in the same position on the page, even if the user scrolls the page
```css
#target{
    position: fixed;
    top: 90%; /* floating nearly at the top */
    left: 0;
    width: 100%; /* like a banner*/
    z-index: 4; /* High number puts the element in the foreground */
}
```
- Some usecases would be a navigation banner, or a chat bot icon
- `top: 0` results in sticking at the very top

# 📅 06.12.2022 css: layout: How to do relative positioning?
- You would use this if you want to finetune a layout but do not want to change the other elements layout
- It is called relative because you define offsets relative to its original position
```css
#target{
    position: relative;
    top:  10px; /* relative to orginal position */
    left: 10px;
}
```
- the above pushes the element actually `10px` down and to the right. Think of it as pushing from the `top` and `left`

# 📅 06.12.2022 css: layout: What is the difference between block elements and inline elements?
- Block elements provoke a line break after them like `body`,`br`,`div`,`article`,`ul`,`li`,`...`
    - they usually take up all the width of the parent element
    - the try to accomodate the contents by growing the height (sometimes called block dimension)
- Inline elements do not have breaks like `a`,`span`,`code`, `input`,`img`,`...`
    - the size depends entirely on the content, you can't set `width`/`height` attributes (except images)
- Those elements default for `display` property to either `block` or `inline`
- both `display` types have also different `margin`, `padding`, `border` effects regarding the interaction with other elements (more in-depth in box-model)

# 📅 06.12.2022 css: What are the common unit types and when to use them?
- There is absolute length units (like `px`, `mm`, `pt`) and relative ones (`em`, `ch`, `%`)
- Pixel, `px`, use for example for raster images or any fixed size requirements
- Ems, `em` corresponds to font-size of current element (`rem` of root element), use for response designs. `1.4rem` is 1.4 times the fontsize of the root element of the document.
- Percent, `%` of the parent elements value for the same property, use for responsive designs
- Points, `pt` often used for fonts
- Usually you should use: `em`, `rem`, `%` and `px` for fixed elements
- You should avoid using viewport units like `vw`, `vh`, `vmin`, `vmax` (percentages relative to viewport)
- Unit examples
    - Borders you would specifiy in `px` because you typically do not want them to scale: `border-bottom: 2px solid #fff;`
    - Font sizes you would specifiy with `em` always relative to the current/parent element  `font-size: 0.9em;`
    - For padding/margins you should use `rem`, if in component it is better for reusability
    - For media queries always use `em` (never use `px`) - [source](https://cloudfour.com/thinks/the-ems-have-it-proportional-media-queries-ftw/)

# 📅 06.12.2022 css: layout: box-model: What is the difference between border, margins and padding (box model)?
- Both padding and margin are used to create space around elements
- Boader is surrounding all of your content and padding, outside the border is the margin defined
- Or put differently: Margin is used to create space around an element, while padding is used to create space within an element (e.g. button).
- When to to use what?
    - Per default you should always use margin, except you have a visible background and want to show some empty space between content and border
    - Be aware then margins auto-collapse - think of it as a min space between two elements if two elements have margin=100px then the total space between will be 100px. padding is added though since it is part of the element within the boarders
    - Be aware that margin is not part of the click region (contrary to padding)

# 📅 06.12.2022 css: What are the different css selectors?
- [source](https://www.w3schools.com/cssref/css_selectors.php)
```css
/* Matches dom tags */
h1 {
    color: blue;
}
/* Matches classes */
.title {
    font-size: 2em;
}

/* Matches id */
#logo-vip {
    height: 20px;
}
/* Matches all elements having an attribute (e.g. all img elements with an height attribute) */
img[height]{
    width: auto;
}
/* You can also match for specific attribute values (equal '=', contains '*=', starting with '^=', ending with '$=' */
img[height=200]{
    width: 100px;
}
/* You can also combine several attribute selectors, in this case both attributes need to be set with the specified value in order to match the element. */
input[name="Sex"][value="M"]{
    color: green;
}
/* Append/Prepend to element e.g. prepending '>>>' before each header */
h1:before { /* also :after */
    content: ">>>";
}
```

# 📅 06.12.2022 css: How to combine css selectors?
- style several entities at once, called a **grouping selector**
```css
h1, h2 {
    color: blue;
}
```
- match all elements with a important class which are located inside a span (decendants of span)
```css
span .important {
    color: red;
}
/* for direct decendants use this*/
span > .important {
    color: red;
}

```
- match all span elements with a important class, called **compound selector**
```css
span.important {
    color: red;
}
/* also works with other selectors like id matcher */
span#specialAlert {
    color: red;
}
```
- one selector following the other, in the same hierachy (first paragraph after each header), aka. adjacent sibling combinator
```css
h1 + p {
    font-style: italic;
}
```
- match based on state (for more see pseudo-elements)
```css
a:visited {
    color: green;
}
```

- you can also combine several selectors
```css
/* a sequence of those elements in same hierachy */
h1 + p + span {
    color: green;
}
/* a nesting of those elements */
section p span {
    color: green;
}
```

# 📅 06.12.2022 css: How to style several entities at once?
- Just comma-seperate them
```css
h1, h2 {
    color: blue;
}
```

# 📅 06.12.2022 css: How to select every element there is?
```css
/* Matches everything */
* {
    font-family: Arial;
}

/* Matches every child element of div */
div * {
    color: red;
}
```



# 📅 06.12.2022 css: How to import other css files?
- Imports must be at the very top of the file
```css
@import "someOtherFile.css"
```




# 📅 05.12.2022 javascript: What is hoisting?
- All variable or function declarations are moved to the top of the file/or scope so you do not have to order the functions accordingly
```javscript
console.log (var1);
var var1 = "hey";
//results in
var var1;
console.log(var1); //still undefined
var1 = "hey";
```

# 📅 05.12.2022 javascript: What is the difference between var, let and const?
- `var` can be locally or globally scoped (dependning on if you declare it in function or outside in file)
    - can be update but also redeclared
```javascript
var var1 = "Hello";
var var1 = "redeclared";
var1 = "update";
// problem: it also redeclares from nested scope
if (isSunshine) {
        var var1 = "onlyInternal?";
}
console.log(var1); // can result in 'onlyInternal?'
```
- `let` can be updated but not redeclared (in nested scope it will be a second scoped local var instead): this is why you should prefer using `let`
- Both `var` and `let` declarations are hoisted but `var` will result in undefined at runtime and `let` in a Reference Error
- `const` is like `let` but is final, meaning it needs to be assigned at the moment of declaration and can't be updated (but we still can update properties of an object)


# 📅 05.12.2022 node: How to use import statements in node?
- ES6 Modules are not supported by default in node.js
- In `package.json` you need to add `"type":"module"`
- and instead of `require` you need to use now `import { someFunction } from  "../../src/functions.js";` or e.g. `import assert from "assert";`
- of course this requires that you also use the correponding `export` statements

# 📅 25.11.2022 mocha: What is it and for what do we use it?`
- Install and run `npm install --save-dev mocha && npm test`
- Provided you create a npm task like this (in `package.json`)
```json
{
  "scripts": {
    "test": "mocha test/**/*.js"
    },
  "type":"module"
}
```
- And Create a `./test` folder with test files with following skeleton
```javascript
import { methodName } from  "../../src/services/helpers.js";
import assert from "assert";

describe('Unit test helper functions', function () {
    describe('methodName', function () {
        it('should return expected string', function () {
            assert.equal(
                "expectedString",
                methodName());
        });
    });
});
```

# 📅 25.11.2022 javascript: How to destructure function parameters?
- Destructuring object based on keys
```javascript
func({name: "Lara", age: 29});

function func({name, age}) {
    console.log(`${name} && ${age}`)
}
// give different local var name
function func({name: n1, age: a1}) {
    console.log(`${n1} && ${a1}`)
}
// give default value
function func({name = 'James', age = 12}) {
    console.log(`${name} && ${age}`)
}
// and combined
// give default value
function func({name: n1 = 'James', age: a1 = 12}) {
    console.log(`${n1} && ${a1}`)
}
```
- More on destructuring [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) e.g. arrays

# 📅 25.11.2022 javascript: How to assign several properties to a object at once?
- Option 1 (ES2015)
```javascript
const originalObject = {
    school: "Bogy",
    studentCount: 30,
    country: "Germany"
};
const thingsToChange = {
    school: "Bogy+VHG",
    studentCount: 60,
};

const combinedObject = Object.assign({}, originalObject, thingsToChange);
// resulting in
combinedObject = {
    school: "Bogy+VHG",
    studentCount: 60,
    country: "Germany"
};
```
- Option 2 (ES2016)
```javascript
const combinedObject = {...originalObject, school: "Bogy+VHG", studentCount: 60}
// or with object reference (don't mix up the order!)
{...originalObject, ...thingsToChange}
```

# 📅 23.11.2022 vuejs: How to pass data into a component?
- There is ways of doing this
    - via probs (think of them like parameters or attributes in the html context)
    - via slots (like text nodes, think of parameterized templates)
- `Props`
- Use custom attributes to pass them into a component, called `props`
- `props` should be always read-only (in theory you can mutate objects because they are passed by reference but you don't want this because data flow becomes very messy)
```javascript
app.component('my-component-name', {
    props: {
        isDarkMode: {
            type: Boolean, // we can enforce types here. Others are e.g. Array, Object, Date, Function
            required: true, // gives warning if not supplied
            default: true // default value, for booleans defaults to false if not stated otherwise

        }
    }
    template: `<h1>{{isDarkMode ? "Darkmode" : "LightMode"}}<h1>`, // use prop fields like normal data fields
    })
```
- Then in parent component, given below state
```javascript
// return data() from app
{
    isDarkModeSelection: true
}
```
- with corresponding html template, you can call the nested component like so (notice `:attribute` binding only needed when value is dynamic)
```html
<my-component-name :isDarkMode="isDarkModeSelection"></my-component-name>
```
- `Slots`
- In the template
```html
<MyComponent> This is some content I pass in!</MyComponent>
```
- In the component
```html
<template>
  <div>
    <strong>Below the content we passed in:</strong>
    <slot />
  </div>
</template>
```
- `<slot>` is like a placeholder where we can inject text node content into

# 📅 23.11.2022 vuejs: Why can't you alert/log in a v-directive expression?
- Due to the restricted exposure of globals, see [here](https://vuejs.org/guide/essentials/template-syntax.html#restricted-globals-access)
- Template expression are sandboxed and can only access certain globals like `Math` or `Date`
- If you want to log something in a template expression of a click handler just write wrap this in a method and reference it in the expression
- If you want to expose certain globals you can do this in [`app.config.globalProperties`](https://vuejs.org/api/application.html#app-config-globalproperties)

# 📅 23.11.2022 programming: What is the difference between a statement and a expression?
- [source](https://www.baeldung.com/cs/expression-vs-statement)
- An expression is a piece of code that can be evaluated to a value. Often you can think of it as something you could write into a `return` statement
    - `1+2`
    - `Singleton.getInstance()`
    - `1 < 4`
- An statement is valid code which can stand for itself and resembles a complete piece of information the compiler/computer can react on. Usually a statement returns `void`

# 📅 23.11.2022 programming: What are the different cases used in programming languages?
- Camel case
    - is usually `lowerCamelCase`
    - Origin: By Newton Love, "he mentioned that the humpiness of the style made him call it HumpyCase at first"
- Pascal case
    - sometimes also referred as `UpperCamelCase`
    - Origin: "The casing style was popularized by the Pascal programming language"
- Snake case
    - is `snake_case` or `SNAKE_CASE` (sometimes called `SCREAMING_SNAKE_CASE`), both delimiting words words with `_`
    - Origin: Because the `______(-)<` is like a snake on the floor
- Kebab case
    - is `kebab-case` (delimiting words with `-`)
    - Origin: Because the `-` look like a skewer in a kebab: `-{}-@-{}@{}--`
- Read more on different formating options [here](https://en.wikipedia.org/wiki/Naming_convention_(programming)#Multiple-word_identifiers) and [here](https://stackoverflow.com/questions/17326185/what-are-the-different-kinds-of-cases)


# 📅 23.11.2022 javascript: How to create a copy of an array?
- Example for `reverse()` because this mutates original array
```javascript
[...numbers].reverse()
```
- `...` is the [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) where you expand a list into arguments


# 📅 23.11.2022 vuejs: How render a element n times?
- Render a `div` 10 times
```html
<div v-for="n in 10">{{ n }}</div>
```
- If you want to render several elements without a enclosing div you can wrap this in a `<template>` tag and add the `v-for` directive there

# 📅 23.11.2022 vuejs: How render a object (key/value) with a loop?
```html
<li v-for="(value, key) in propertyObject">
  {{ key }}: {{ value }}
</li>
```
- optionally you can also access the index with a third parameter

# 📅 23.11.2022 vuejs: How so vue directives work?
- Vue directives are instruction for VueJS to do things in a certain way
- General syntax
<p align="center"><img height=400 src="https://vuejs.org/assets/directive.69c37117.png" /></p><br>

- Arguments (demarked by `:`) can also be dynamic
```html
<!-- Evaluates e.g. to attributeName="src"-->
<a v-bind:[attributeName]="url"> </a>
<!-- Shorthand for event binding, evaluates e.g. to eventName="click"-->
<a @[eventName]="doSomething">
```


# 📅 23.11.2022 vuejs: How to bind multiple attributes to an element at once?
- Usually you would define a attribute object and bind that to an element
```javascript
// return data() from app
{
    someProperties: {
        src: "oma.app/profile.png",
        height: 12px,
        width: 12px
    }
}
```
```html
<!-- Note that no argument is provided for the bind directive-->
<img v-bind="someProperties">
<!-- Evaluates to this:-->
<img src="oma.app/profile.png" height="12px" width="12px" >
```
- as a binding object you can also use computed attributes which is quite powerful (e.g. calculate booleans in property and not inline in template)

# 📅 23.11.2022 vuejs: How to evaluate HTML when injecting into a template?
- There is a `v-html` directive, which you would use like this
```html
<p>Evaluated html: <span v-html="someHTML"></span></p>
```
- Note this evalates raw html and no template syntax like bindings etc. (for this you should use components)

# 📅 22.11.2022 npm: How to run several tasks at once?
- The usual unix operators apply
```bash
# Run run sequentially
"dev": "vite && json-server --watch mocks/db.json --routes mocks/routes.json",
# Run run in parallel
"dev": "vite & json-server --watch mocks/db.json --routes mocks/routes.json"
```
- If you want to have them in one task, having the option to interupt them both with `Crtl + C`, use package `concurrently`
```bash
"dev": "concurrently --kill-others \"command1\" \"command2\""
```

# 📅 22.11.2022 vuejs: vite: How to inject environment dependent variables on build time?
- Vite has the concept of different modes: `development` (on `dev` task) and `production` (on `build` task)
- Depending on the mode environment variables are loaded from either `.env` (always loaded) or `.env.development`/`.env.production` (overwrites more general definition)
- A env-file is a simple key-value mapping, variables need to be prepended with `VITE_` for exposing them to the application
```plaintext
# in .env.development located in root folder (defined in `envDir`)
VITE_URL=http://localhost:3000
```
- Environment variables can be accessed via
```javascript
console.log(import.meta.env.VITE_URL);
// Current mode can be checked with
console.log(import.meta.env.MODE); // or check for boolean: import.meta.env.PROD/DEV
```

# 📅 22.11.2022 javascript: How to do string interpolation?
```javascript
console.log(`also for normal String`);
console.log(`string text ${1+1} string text`);
```

# 📅 22.11.2022 javascript: How to create anonymous functions?
```javascript
// you can pass this a parameter
function (a, b) {
    return a + b;
};
// Since ES6
(a, b) => a + b;
```
# 📅 22.11.2022 vuejs: How to react on a state update with a side-effect?
- In vue you can bind state changes to a attribute (`v-bind:..`) or a text node (`{{...}}`)
- But also a value calcultion with `computed` properties
- If you just want to trigger a side-effect like an API call on state change, use `Watcher`
```javascript
export default {
    data() {
        return {
            someVar: "",
        }
      },
      watch: {
        someVar(newVal, oldVal){
          console.log("Changed!! With " + newVal);
        }
      }
}
```
- If you have multiple values you can either
    - create a `computed` composite and observe this
    - or store it in a composite object in the first place (but then do not forget to use a [Deep Watcher](https://vuejs.org/guide/essentials/watchers.html#deep-watchers) -> `deep:true` option)

# 📅 22.11.2022 vuejs: How does the component lifecycle work?
- Most important state changes are
    - `created`: Here you would normally fetch data before populating the view of a component
    - `mounted`: Used when you need the rendered dom for applying a side-effect
    - `updated`
    - `unmounted`
- Exposed for instance through Options API like so
```javascript
export default {
  mounted() {
    console.log(`Finished`);
 }
}
```


# 📅 21.11.2022 unix: How to change to different user in cli?
- `su -i "USER"`

# 📅 21.11.2022 npm: What is npm?
- A package manager for node.js (Javascript)

# 📅 21.11.2022 npm: How to update?
- `npm update -g`

# 📅 21.11.2022 vuejs: What is vite?
- The official build tool for vue

# 📅 21.11.2022 javascript: What is ECMAScript?
- Since each browser has its own Javascript interpreter a standard was needed to ensure the written Javascript is compatible with all the different browsers
- Common verisons are
    - ES6(ECMAScript 2015)
    - ES7(ECMAScript 2016)
    - ES8(ECMAScript 2017)
- Since 2016 version are usually named by the year only
- For versions and compability see [here](https://www.w3schools.com/js/js_versions.asp)

# 📅 21.11.2022 javascript: What is Typescript?
- A superset of Javascript
- Extends the language by a static type system


# 📅 21.11.2022 javascript: What is JSX?
- A Javascript extension allowing to work with xml sytnax
- Stands for Javascript XML
- Originally HTML (subset of XML) with javascript in `<script>` tags, now it is the other way round: Javascript with xml tags
- Allows you to something like this
```javascript
var nav-bar = (
    <ul id="nav-bar">
        <li><a href="#">Home</a></li>
        <li><a href="#">Settings</a></li>
        <li><a href="#">About</a></li>
    </ul>
);
```
- Since JSX is not supported by browsers, written JSX code needs to converted into ordinary Javascript code (done by a preprocessor)


# 📅 21.11.2022 networking: What is a CDN?
- CDN := A content delivery network delivering content from a content delivery server based on the geographical location of the client

# 📅 21.11.2022 vuejs: What is the difference between views and components?
- A View is a specific component which is used for routing (orchestrated by Vue Router)
- When a certain route is matching view is shown in the corresponding `<RouterView />`
- Example of how a router could look like
```javascript
import Home from '@/views/HomeView.vue'
import About from '@/views/AboutView.vue'

export default [
  {
    path: '/',
    name: 'home',
    component: HomeView,
  },
  {
    path: '/about',
    name: 'about',
    component: AboutView,
  },
]
```
- A view itself usually would contain some other resuseable components
- The distinction between views and components is a artifical one and does not have to be followed, it is just a convention scaffolding tools like `vite` is using

# 📅 21.11.2022 How to test my frontend with backend rest dependencies?
- Spin up local backend yourself
- Spin up a mock server serving a REST api, recommended tool: [json-server](https://github.com/typicode/json-server)
- Tooling for intercepting calls (also possible from Chrome Browser), recommended tool: [msw](https://github.com/mswjs/msw)


# 📅 17.11.2022 sql: normalization: What is understood under 4NF?
- **If we break 3NF we also violate 4NF**
- **If we do have multi-valued dependencies on a non-key attribute we break 4NF**
- For example a NPC with a certain race can have one of several skin-colors, this needs to be moved out to a separate table
```plaintext
id,race,skin_color
1,elve,white
2,elve,green
3,dwarf,white
4,dwarf,brown
```
- if not moved out you might add a new color to a race but only for a certain sub-race which was not the original intent of the database designer

# 📅 17.11.2022 sql: normalization: What is understood under 5NF?
- **If we break 4NF we also violate 5NF**
- **If we can think of creating the existing table based on joining imagined subtables we break 5NF**


# 📅 17.11.2022 vuejs: How to create an app?
- In `main.js` the vue app is created via `createApp`, with a mandatory options object, containing
    - `data` which is the data model which is used in the view/html template
```javascript
const app = Vue.createApp(
    { data: function {
        return { item: 'Tomato' }
        }
    }
);
```
- Shorthand in ES6
```javascript
const app = Vue.createApp(
    { data() {
        return { item: 'Tomato' }
        }
    }
);
```
- import main.js into your index.html and mount it (injecting into dom element with id `main`)
- each `{{value}}` creates a connection (like a telephone line) to the dynamically created hash map in main.js/app
```html
<div id="main">
    <h1>{{item}}</h1>
</div>
<!-- Import vue.js-->
<!-- ...-->
<!-- Import app-->
<script src= "./main.js"></script>
<!-- Mount app-->
<script>
    const mountedApp = app.mount('#main');
</script>
```
- if the app options do not contain a template field, the html in the container will be used as template (called in-DOM template)
    - here you have to use kebab-case for components to comply to the Dom parsing of the browser
    - For more in-DOM template implications see [here](https://vuejs.org/guide/essentials/component-basics.html#dom-template-parsing-caveats)

# 📅 17.11.2022 vuejs: What does {{someThing}} mean in my html?
- Called mustache syntax and allows us to run javascript in our html (without an explicit script syntax)
```html
<h1>{{alert('Hello World!')}}</h1>
<h1>{{'This is ' + myName}}</h1>
<h1>{{isSunshine ? 'Wuhu!' : 'Oh, no!'}}</h1>
```
- In the context of vuejs we can also access variables dynamically generated by the app
- This works because vue is reactive, so whenever a value changes in our javascript code it automatically updates the html dom for us
- In the end this:
```html
    <h1 id="myHeader">{{'This is ' + myName}}</h1>
```
- is just a shorthand for
```javascript
    document.getElementById("myHeader").innerHTML = 'This is ' + mountedApp.item;
```
- What the framework additionaly is doing is running this code whenever that specifc value has changed
- For more read into `Vue's Reactivity System`

# 📅 17.11.2022 vuejs: What is attribute binding?
- With the moustache syntax `{{}}` you can only use in text nodes but not for values of HTML attributes
- Given you expose `url` field
```javascript
// return data() from app
{
    url: "oma.app/img/profile.png"
}
```
```html
<!-- This works, text node -->
<div>{{url}}</div>
<!-- This is not allowed -->
<img src={{url}}>
<!-- In order bind expression to attribute-->
<img v-bind:src="url">
<img :src="url"> <!-- shorthand-->
```
- if the bound value is null or undefined the attribute will be removed
- those custom dom attributes like `v-bind` are called vue directives, see [here](https://vuejs.org/api/built-in-directives.html) for complete overview of native directives

# 📅 17.11.2022 vuejs: What is conditional rendering?
- Like a if-else helping you to decide which dom elements you want to render
```javascript
// return data() from app
{
    isDarkmode: true,
    credits: 99
}
```
```html
<p v-if="isDarkmode">Dark-Mode</p>
<p v-else>Light-Mode</p>

<!-- expression can also hold conditions supporting the usual control flow structures -->
<p v-if="credits > 99">You are VIP!</p>
<p v-else-if="credits == 0">You are out of credits</p>
<p v-else>Good to go...</p>
```
- You do not need a fall-back element with `v-else` if there is nothing to show
- If you want to just toggle visibility on a condition use `v-show` (will always be part of the dom). Often used for instance for a modal
- When you want to conditionally render several elements without wanting to introduce a parent element, use template
```html
<template v-if="renderThis">
  <h1>Hello World</h1>
  <p>Some subtitle</p>
  <p>and more text</p>
</template>
```
- When rendering the dom the `<template>` tag will be not part of it

# 📅 17.11.2022 vuejs: How to render lists?
- for creating several elements at once we need to use the `v-for` directive on the element we want to repliate e.g. `<li>`
- same principle as a for-each loop, for each element `item` of `items`
- The current element can be accessed with the alias `item`
```javascript
// return data() from app
{
    items: [{ name: "Tomato", quanity: 12, id: 1},{ name: "Milk", quanity: 2, id:2},{ name: "Cheese", quanity: 8, id:3}]
}
```

```html
<div>Items:</div>
<ul>
    <!-- Instead of in you can also use for-->
    <li v-for="item in items">{{'Product: '+ item.name + ', Stock: '+item.quantity}}</li>
</ul>
```
- Each list item should have a unique id (note the shorthand for attribute binding `:key`)
    - gives us performance improvments
    - track item for instance when identifying clicked element
    - very important if child elements are components or dom elements with state
    - See more details [here](https://vuejs.org/guide/essentials/list.html#maintaining-state-with-key)
```html
<div>Items:</div>
<ul>
    <li :key="item.id" v-for="item in items">{{'Product: '+ item.name + ', Stock: '+item.quantity}}</li>
</ul>
```
- Alternatively we can also use the current index of each element e.g. key="item_"+index

# 📅 17.11.2022 vuejs: How to do event handling?
- First the event handler needs to be written and registred in the vue app (in the `methods` field of our options object)
- Note how data attributes are referenced with `this`. You can also assign other attributes to `this` but they want be reactive as they are when declared in the `data` object
```javascript
const app = Vue.createApp(
    {
        data: function { return { item: 'Tomato' }},
        methods: {
            alertTheWorld(){
                alert('Hello World!');
                this.item = "Clicked!"; // access data from app with `this`
            }
        }
    }
);
```
- In order to register the event handler on the `click` event, we use the `v-on` directive
```html
<button v-on:click="alertTheWorld">Click-me!</button>
<!-- Shorthand for v-on is @ -->
<button @click="alertTheWorld">Click-me!</button>
```

# 📅 17.11.2022 vuejs: How to add click handlers to a list of elements?
```javascript
// return data() from app
{
    items: [
                { name: "Tomato", quanity: 12, id: 1},
                { name: "Milk", quanity: 2, id:2},
                { name: "Cheese", quanity: 8, id:3}
    ]
}
```
- First possibility when `id` is available
```html
<div>Items:</div>
<ul>
    <!-- Here you can also specify a custom function/event handler and pass in the item.id/update state etc.-->
    <li v-for="item in items" @click="console.log(item.id)">{{item.name}}</li>
</ul>
```
- Second possibility by position in the list (for-loop with index)
```html
<div>Items:</div>
<ul>
    <!-- Current selection can also be stored as state with a function like below -->
    <li v-for="(item, index) in items" @click="currentSelectionIndex = index;">{{item.name}}</li>
    <!-- Since you should always use a key per dom element for performance reasons you can use the index for that -->
    <li v-for="(item, index) in items" :key="index" >{{item.name}}</li>
</ul>
```
- If you want to access the current element directly from other places you can use a computed property like this
```javascript
computed: {
    currentSelection(){ return this.items[this.currentSelectionIndex]}
}
```

# 📅 17.11.2022 vuejs: How to do style binding?
- **Inline styling**
- Notice the shortcut hand `:attribute` for style, which is binding a style object to the style attribute
```html
<div :style="{backgroundColor: mainColor}">Hello</div>
```
- behind the scene vue.js is converting the above in something like this
```html
<div style="background-color:green">Hello</div>
```
- Note that `backgroundColor` is key of a javascript style object and therefore kamel-case
- if you want to use kebab-case `background-color` you need to put this in quotes
```html
<div :style="{'background-color': mainColor}">Hello</div>
```
- **Reference js style object**
```javascript
// return data() from app
{
    styleHeader: {
        fontSize: '12px',
        color: 'blue'
    }
}
```
```html
<div :style="styleHeader">Hello</div>
```
- **Reference and toggle css classes: Class binding**
- See `How to do class binding?`

# 📅 17.11.2022 vuejs: How to do class binding?
```css
.disabledElement{
    background-color: #FFFf;
}
```
- Notice orginal `class` attribute does not get overwritten by bound classes
- Notice `:class` is expecting a object with class names and toggle state (not `{{...}}` notation)
```html
<button class="button" :class="{disabledElement: points < 1}" >Enter VR</button>
```
- Also allows for ternary expressions, note the `[]` brackets
```html
<button class="button" :class="[isDisabled ? disabledElement : fancyHighlightedButtonClass]" >Enter VR</button>
```

# 📅 17.11.2022 vuejs: What are computed properties and how to use them?
- Allows to compute certain values in the vue backend without needing to this in the html (caches the value)
- in the end it is functions but in the html you can reference them as a data property
```javascript
const app = Vue.createApp(
    {
        data: function { return { item: 'Tomato', size: 'XXL' }},
        computed: {
            productName(){ return this.item + "(" + this.size + ")"}
        }
    }
);
```
- this is also useful as a alias e.g. if you need to do this often `this.items[this.currentItemIndex].variant[this.variantSelection].name` is probably better to create an computed property
- Or also used if you want to provide a sorted list
- You can also use computed properties to calculate values and have a different type as output
- Creating a message like this: `message=this.author.books.length > 0 ? 'Yes' : 'No'`

# 📅 17.11.2022 vuejs: What are components?
- Basic building blocks of a vue.js app
- You can block them into each other into a component hierachy. A component can have child components.
- Usually stored in a sperate javascript file (need to import it seperately then)
```javascript
app.component('my-component-name', {
    template: `<h1>Hello World<h1>`, // template literal
    data: function { return { item: 'Tomato'}}, // data properties
    computed: { someName(){ return this.item + "(" } }, // computed properties
    methods: { hello(){ return "uhu!"}}, //available methods
    })
```
- Then use it in html template like this
```html
<my-component-name></my-component-name>
```
- [Single-File-Components](https://vuejs.org/guide/scaling-up/sfc.html): Since you will end up creating and using a lot of components you can also use an **alternative way** of declaring components
    - you can use specific dom tags for defining script/template logic
    - Syntax described [here (SFC))](https://vuejs.org/api/sfc-spec.html)
    - File extension is `.vue`
    - A compiled SFC is a proper Javascript module and therefore can also be imported like a module `import MyComponent from './MyComponent.vue'`
    - Therfore do not forget the `export default {..}` (alternatively you can also export several components from the same file if you use named exports)
    - For Single-File-Components you should use `PascalCase` in order to differentiate from html tags (even though the compiled html is case-insensitive)

```html
<script>
    export default {
      data() {
        return {
          greeting: 'Hello World!'
        }
      }
    }
</script>

<template>
  <p class="greeting">{{ greeting }}</p>
</template>

<style>
    .greeting {
      color: red;
      font-weight: bold;
    }
</style>
```

# 📅 17.11.2022 vuejs: How to trigger state changes outside of component?
- In short, emit an event to the parent component that a certain thing happened
- Note the `$` prefix, this is reserved for Vue's internal API's (same for `_` which is for internal properties)
```javascript
app.component('my-component-name', {
    // template, probs, computed ...
    methods: {
        notifyParentComponent(){
            this.$emit('my-event','someOtherParamValue'); // sometimes also called bubbling up a event, 'someOtherParam' is the payload of the event
        }
    }, //available methods
})
```
- Meanwhile in the parent component we are listening to that event
```html
<my-component-name @my-event="logMe"></my-component-name>
```
- with method definition, method needs to match the expected signature which is one parameter for the payload
```javascript
const app = Vue.createApp(
    {
        // data, computed ...
        methods: {
            logMe(someOtherParam){
                console.print('State change from child, with param ' + someOtherParam);
            }
        }
    }
);
```
- Apart from emitting events you can also
    - Pass down a hook which updates parent state
    - Use tech like `vuex store` which maintains a global state everyone can read and write from

# 📅 17.11.2022 vuejs: How to create forms?
- `v-bind`/`:attribute` only binds from vue backend to template (on-way)
- `v-model` creates a two-way binding (change on one side, updates the other side
```javascript
app.component('my-form', {
    // template, probs, computed ...
    template:
    `<form @submit.prevent="onSubmit">
        <h2>Configure your car</h2>
        <label for="name">Brand:</label>
        <input id="name" v-model="name">
        <label for="wheelsExtra">Extra Wheels:</label>
        <select id="wheelsExtra" v-model.number="wheelsExtra">
            <option>0</option>
            <option>1</option>
            <option>2</option>
            <option>3</option>
        </select>
        <input class="button" type="submit" value="Submit">
    </form>`,
    data() {
        name: '',
        wheelsExtra: null
    },
    methods:{
        onSubmit(){
            this.$emit('my-form-submitted', { name: this.name, wheelsExtra: this.wheelsExtra}) // bubbles up event with form data as payload
            // afterwards you could reset the form or open new component
        }
    }
})
```
- Note if input type is number you need to use `v-model.number` for binding (modifier `number`does typecast to `number`)
- Note that `null` as value would not select/show any value in the form
- `prevent` of `@submit.prevent` is also an modifier prevent browser refresh on submit

# 📅 17.11.2022 javascript: What evaluates to false (aka falsy values)?
```javascript
// 0 or "0"
arr = [];
(0 == false)
(arr.length == false) // eventually usueful
("0" == false) // type converted into number
(undefined == false) // type converted into number
(null == false)
(NaN == false)
```
- when talking about the opposite of falsy we often talk about the truthiness of e.g. a property

# 📅 14.11.2022 sql: How to update a value in a row?
```sql
UPDATE customer SET name = "James Potter"
WHERE id = 1;

-- reference column name
UPDATE customer SET order_count = order_count + 1

```

# 📅 14.11.2022 sql: How sort returned rows?
```sql
SELECT * FROM customer
ORDER BY age DESC; -- opposite is 'ASC'
```

# 📅 14.11.2022 sql: What are the naming conventions?
- Use understores where you would end up using whitespaces `order_count`
- Always prefer lower-case for table, column names
- For tables, try to use a singular collective name e.g. `stuff`
- Never call a column name the same as the table name, e.g. don't do this `profile.profile`
- For aliases, use first letter of each word of column, if alias have conflict use numbers
```sql
SELECT first_name AS fn
FROM person AS p1
JOIN profile AS p2
ON p2.some_id = p1.other_id;
```
- Reserved keywords are always in uppercase e.g. `SELECT`
- Always intend on joins
```sql

SELECT c.last_name
    FROM customer AS c
        INNER JOIN profile AS p
        ON c.order_count = p.some_id

        INNER JOIN orders AS o
        ON o.id = c.order_id
```

# 📅 14.11.2022 sql: How and when to self-join within a table?
- Why?
    - Often used if a value references in to another row and you want to return actual values of that row and not reference
    - This scenario is often the case for employee hierachies e.g. person A needs to work for person B
- How?
    - You just reference the table twice but with different aliases (otherwise will cause an error)
```sql
SELECT
    CONCAT(m.last_name, ', ', m.first_name) AS manager,
    CONCAT(e.last_ame, ', ', e.first_name) AS employee
FROM stuff m
    INNER JOIN employees e
    ON m.id = e.works_for
ORDER BY manager;
```
    - In the above case, the top manager which does not refer to anyone would be ommited (to include him/her use `LEFT JOIN` with `IFNULL`)

# 📅 14.11.2022 sql: What is a index?
- ELI5: A data structure used to speed up queries
- Without an index a simple `WHERE` statement forces the query algorithm to over each field and check if e.g. a equal check is satified
- With a faster data structure (e.g. tree-like) that search can be shortned substantially, decreasing query time by a lot
- You can think of it like a map where the key is the value you define a index on and the value is the containing row

# 📅 14.11.2022 sql: normalization: What is normalization and the different normal forms?
- Normalization is structuring data in such a way so that
    - it can't express redundant information
    - easier to understand and extend
    - protection against insertion/update/deletion anomalies
- How do we determine that redundant data can get into the database?
    - there is several levels of security regarding the danger of happening this, called NF1, NF2, ... NF5
    - like safety assessments
- Good beginner introduction into normalization [here](https://www.youtube.com/watch?v=GFQaEYEc8_8&list=PPSV)

# 📅 14.11.2022 sql: normalization: What is understood under 1NF?
- **If we use row order to convery information we violate 1NF**
- Row order is never considered in a relational database
- If you need to express an order of entries then introduce a sorting key e.g. `priority`
- **If we mix up data types we violate 1NF**
- e.g. `height` containing 120, 214, "something between 120-140"
- Usually the database does not even allow this, usually enforces type safety
- **If we do not define a primary key we violate 1NF**
- Once we define a primary key we automatically define a unique constraint of that column
- Without this two identical id's but with different date of birth date would result in a failed data integrity: Data disagrees with itself
- **If we repeat groups we violate 1NF**
```plaintext
username,inventory
bioflash,"12 coins, 1 sword, 2 carrots" (repeating group := one column encoding several entities)
mal13,"110 coins, 3 tomatoes"
```
- 🛠 Repair this: A good way to represent this would be create a `inventory` table
```plaintext
username,item_type, item_quantity
bioflash,coin,12
bioflash,sword,1
bioflash, carrot,2
mal13,coin,110
```
- the primary key would be `PK(username,item_type)` since each single value would potentially not be unique

# 📅 14.11.2022 sql: normalization: What is understood under 2NF?
- **If we break 1NF we also violate 2NF**
- Having redundant values in your table creates several problems
    - Deletion anomaly happens if we extend a a column to a table which have rows which do not need to exist
        - e.g. player has items (`PK(username,item_type)`)and we do add a `age` column to that table
        - if player happens to have no items, we have not row left in that table and therefore no `age` column even though age exists independently of inventory status
    - Update anomaly happens if we update only one of the duplicated values (e.g. failing after first half of update), we have inconsistent state
    - Insertion anomaly, we can't record `age` of a new player because he does not have something in inventory yet
- Non-key attributes (attributes which are not part of `PK(..)`)
- **We break 2 NF if a non-key attribute depends not on the entire primary key**
    - `item_type` depends entirely on `PK(username,item_type)`
    - `age` depends not entirely on `PK(username,item_type)` since age does not change for a specific username/item_type combination. It only depends on username
- 🛠 Repair this: here we should realize that a `user` is an important concept in its own write, create a user table and add the `age` column there. then `age` will depend entirely on `PK(username)`

# 📅 14.11.2022 sql: What is the usecase of EXISTS?
- `EXISTS` returns true if a subquery returned results and (!) short circuits if there is a match
- Use-case: Retrieve all customers which have bought at least product below 100$
```sql
SELECT *
FROM customer
WHERE EXISTS
    (
    SELECT * FROM order
    WHERE customer_id = customer.id AND price < 100
    )
```
- This also can be rewritten with `JOIN`
```sql
SELECT * FROM customer as c
    INNER JOIN order as o
    ON o.customer.id = c.id
    WHERE o.price < 100;
```
- But with `JOIN` the whole table is joined and matching process is not short-circuited
- [further](https://stackoverflow.com/a/7082510)

# 📅 14.11.2022 sql: normalization: What is understood under 3NF?
- **If we break 2NF we also violate 3NF**
- When having two columns depending on each other (transitive dependency) it can happen that you update one but fail to update the other, you end up with a data inconsistency
- Example would be a `skill_level` (1,2,...9) and `skill_band` ("beginner", "intermediate", "expert"). `skill_band` depends on `skill_level`
- **If we have a non-key attribute depending on another non-key attribite we violate 3NF**
- 🛠 Repair this: Extract `skill_band` out in a look-up table and whenever we need the `skill_band` we join/generate those values based on the `skill_level`
- The complete 3NF can be summarized as the following (Boyce-Codd Normal Form - when leaving out non-key)
```plaintext
Every (non-key) attribute in a table should depend
    on the the key,
        the whole key
            and nothing but the key.
```

# 📅 10.11.2022 sql: What is the difference between Datetime, timestamp?
- `TIMESTAMP` is like a unix timestamp denoting a point in time in UTC, is converted back and forth when retrieved
- `DATETIME` is stored with the current timezone and not converted in UTC
- `TIMESTAMP` is usually used for internal creation/update timestamps

# 📅 10.11.2022 sql: What is the difference between VARCHAR, TEXT and BLOB?
- `TEXT` datatype is quite similar to `VARCHAR` - see differences [here](https://www.navicat.com/en/company/aboutus/blog/1308-choosing-between-varchar-and-text-in-mysql)
- both of them are a bunch of bytes with an character set associated to it
- A blob stores binary data, just a bunch of bytes used for example to store image data
- To convert between binary and text representation see [charset conversion](https://dev.mysql.com/doc/refman/8.0/en/charset-conversion.html)

# 📅 10.11.2022 sql: What is the difference between SET and ENUM?
- both of them act as a constraint on values entered into the column
-`ENUM`, like radio fields: you can choose one of the accepted values. Error value 0 or empty string are rejected
-`SET`, like checkbox fields: you can choose choose multiple of the accepted values. Empty string is not rejected since it always part of `SET`

# 📅 10.11.2022 sql: How to rewrite a inner join with a WHERE statement?
- from a performance standpoint both statements are the same
```sql
SELECT product_name, category_name
FROM product, category
WHERE product.category_id = catgegory.id;
```
- but don't do this
- since the WHERE statemen does not comply to the ANSI Syntax for JOINS
- `INNER JOIN` is easy to replace with `OUTER JOIN
- `STRAIGHT JOIN` also allows to define inner/outer loop, joining order

# 📅 10.11.2022 sql: What is the ANSI Syntax?
- ANSI SQL := a series of standards for modeling and manipulating data
- Some vendors comply to that standard, some not or only partially

# 📅 10.11.2022 sql: Which JOINS will I use the most often?
- Most frequent `JOINS` you will end up using
- `INNER JOIN`
- `LEFT OUTER JOIN` aka. `LEFT JOIN`

# 📅 09.11.2022 javascript: Why should you learn javascript?
- Not really an alternative (except wasm) when you want to do something in the frontend
- You can manipulate HTML, CSS and have custom logic in frontend
- there is also other frontend languages you can use but even those languages are in the end transpiled to javascript

# 📅 09.11.2022 javascript: How to interact with the dom?
- Access dom elements
```javascript
// Access dom tree directly
document.childNodes[1].style.backgroundColor = 'green'; // should always target <html> tag
// Access dom element(s) based on id
document.getElementById("someId").innerHtml = "newValue";
// Access dom elements based on tag type
document.getElementsByTagName("p")[0].style.backgroundColor = 'black'; // style first match
```

- Check/change attributes of elements
```javascript
someNode.hasAttribute("id");
someNode.getAttribute("id");
someNode.setAttribute("id", "so22");
someNode.attributes[0].nodeName; //access all attributes
someNode.attributes[0].nodeValue;
```

- Create elements and associate with dom tree
```javascript
// Create element
var myDiv = document.createElement("div");
myDiv.innerHtml = "Some text here";

// plug into dom tree
someOtherNode.appendChild(myDiv); // inserts as last child of someOtherNode
someOtherNode.insertBefore(myDiv,someNode.childNodes[0]); // inserts as first child of someOtherNode

// Write to document directly
document.write("1+2",1+1,"<div>someDomElement</div>");
```

# 📅 09.11.2022 javascript: oop: How to do OOP?
- The analogon of a object is usually a simple map where we also introduce functions
```javascript
var person1 = {
    name : "James",
    age : 12,
    greet: function (name){
        return "Hey "+ name + ", my name is "+ this.name;
    }
};

// access/assign values
person1.name = "Dr. James";
person1["name"] = "Dr. James"; //analogous

// delete a specific property
delete person1.age;
```
- Map analogy because you can also access fields via key-value notation
```javascript
// iterate over all fields
for(key in person1){
    console.log(person1[k]); // access value like you would access an ordenary map
}
// Check if property is in object
var hasName = "name" in person1;
```

- If you want to define a generic object there is also object constructors
- Note the differences to the object map (use of `this`, `=` instead of `:`, field declarations ending with `;`)
```javascript
function Person(name, age){
    this.name = name;
    this.age = age;
    this.greet = function (name){
        return "Hey "+ name + ", my name is "+ this.name;
    };
}
var person2 = new Person("Billy", 12);
```

# 📅 09.11.2022 javascript: oop: How to define class/static variables?
```javascript
// shared values
Person.prototype.isSmartestSpecies = false; // shared value for all persons
// shared functions (aka prototype methods)
Person.prototype.compare = function(p1, p2){
    return p1.age.compare(p2.age);
};
// you can also overwrite methods (all objects have toString)
Person.prototype.toString = ...
```

# 📅 09.11.2022 javascript: How does regex work?
```javascript
var regex = /^A.{4}/;
regex.test("Abcde");
```

# 📅 09.11.2022 javascript: How do exceptions work?
```javascript
// catch error
try{
    // throw a new error
    throw new RangeError("Out of range!");
}catch (ex){
    if(ex instanceof RangeError){
        console.log("Range error occured");
    }
}
```

# 📅 09.11.2022 javascript: How to interact with the browser (apart from dom)?
- Read/Write current url/host/path
```javascript
alert(window.location.href);
alert(window.location.hostname);
alert(window.location.pathname);
// you can also dynamically change those
window.location.href = "www.google.com";
```
- You can reload the window
```javascript
window.location.reload(true);
```
- Go back and forth through browser history
```javascript
history.forward();
history.back();
// to jump several at once do
history.go(-2); // jump 2 backwards
```

# 📅 09.11.2022 javascript: datatypes: How to create variables?
- Javascript has a dynamic type system, "figures out the types at runtime"
```javascript
var someInteger = 3;
var someString = "hi";
```

# 📅 09.11.2022 javascript: datatypes: Which range does the integer type hold?
```javascript
var someInteger = Number.MAX_VALUE; // or Number.MIN_VALUE
```

# 📅 09.11.2022 javascript: datatypes: How to work with decimal numbers?
- Precision is up to 16 digits
```javascript
// test
0.2 = 0.1000000000000000000000000001 + 0.1000000000000000000000000001
```
- Rounding to two decimal places
```javascript
(120.122/12).toFixed(2);
```

# 📅 09.11.2022 javascript: datatypes: What are some math functions are available?
```javascript
Math.abs(-3);
Math.ceil(4.4);
Math.floor(4.4);
Math.log(10);
Math.min(10,1);
Math.max(10,1);
Math.pow(10);
Math.sqrt(10);
```
# 📅 09.11.2022 javascript: datatypes: How to generate a random number?
```javascript
var from = 3;
var to = 14;
Math.floor((Math.random()*to)+from);
```

# 📅 09.11.2022 javascript: datatypes: How to convert a string into a number?
```javascript
Number("3.41");
// or specific type
parseInt("21");
parseFloat("3.2")
```
# 📅 09.11.2022 javascript: datatypes: How to work with strings?
- The usual string methods
```javascript
var someString = "ab" + "cdefgh";
someString.length; // number of characters
someString.indexOf;("ab") // 0 (start of string)
someString.slice(2,5); // get substring by index
someString.substring(2,2); // same as above but second argument is length starting from position 2022
someString.replace("ab", "--");
someString.charAt(2); // access char array
someString.split(";"); // returns string array based on delimiter
someString.trim(); // trim leading/trailing whitespaces
someString.toLowerCase();
```
- Flank strings with certain styling tags
```javascript
var message = "Welcome!";
// all those returns dom elements
message.big();
message.bold();
message.fontcolor("blue");
message.fontsize("5em");
message.italics();
message.link("www.google.com");
message.small();
message.strike();
message.sub(); // lowered
message.sup(); // uppered
```

# 📅 09.11.2022 javascript: datatypes: What is the difference between == and ===?
`==` verifies that values are equal, `===` value and type is verfied for eequality
- `===` should always be prefered
```javascript
7 == "7" -> true
7 === "7" -> false
```

# 📅 09.11.2022 javascript: datatypes: How to create and use arrays?
- Can create multiple different datatypes in the same array
- You also do not have to define a specific size
- acts more like a array list in Java

```javascript
var notes = ["Hello World", 42, [1, 2]] // all types can live in same array
notes[0] = "Eii mundo!"; // replace at index 0

// splice method
// first parameter is start index, second how many to delete and third (optional) what to insert instead
// returns elements which were deleted/replaced and operates on existing one
notes.splice(0,2,"new1", "new2", "new3"); // returns ["Hello World", 42] and notes is now ["new1", "new2", "new3", [1,2]]

notes.unshift("addNewFirstElement");
notes.push("secondLastNewEntry","lastNewEntry"); //add item to end

notes.shift(); // delete first item
notes.pop(); // Remove last item

// convert array to string
notes.valueOf();
notes.toString(); // above does the same thing
notes.join(","); // join with delimiter

//delete index
delete notes[0]; // delete element

//sorting
notes.sort(); // but is only lexicographic sorting!
// if you want to sort numbers
var numbers = [1,3,42,2]
numbers.sort(function (x,y) { return x - y}); // ascending sort (do y - x for descending)

//combine two arrays into one
var newArray = notes.concat(numbers);
```

# 📅 09.11.2022 javascript: How to work with functions?
- Create a function (no types signature - for params or return values)
```javascript
function myFunction(param1, param2){
    return param1 != param2;
}
```
- But we do not have to provide parameters and can access an unknown amount of params (like varargs in Java)
```javascript
function myWiredFunction(){
    return arguments.length;
}
myWiredFunction(1,2,3,4,5,6,7,10,11); // 9
```

- In javascript we can pass functions as a parameter to another function (see also higher order functions and function as first class citizens)
```javascript
function multiplyBy5(number){
    return number*5;
}

function repeatFunctionTimes3(func,initalNumber){
    return func(func(func(initalNumber)));
}

var result = repeatFunctionTimes3(multiplyBy5,2); // 10 -> 50 -> 250
```
- In the same way you can also assign functions to variables
```javascript
var f1 = function (number){
    return number*5;
}
```
- allowing you to store them also in arrays
```javascript
var functions = [function (number){ return number*2;}, function (number){ return number*3;}];
functions[0](2); //4
functions[1](2); //6
```


# 📅 09.11.2022 javascript: Where to inject javascript?
- Trigger javascript when clicking on a link (href keeps page from reloading when link is clicked)
```html
<a href="JavaScript:void(0)" onClick="alert('Hello world!';)" >
```
- React to changes in a form (is only trigger once cursor leave form)
```html
<input type="text" id="input1" onChange="alert(document.getElementById(input1).value);" >
```
- React to mouse movements on whole body
```javascript
document.body.onmousemove = function (e) {
        alert(e.pageX + " and " + e.pageY);
};
```

- Self-reference dom with 'this'
```html
<!--self-reference dom with 'this' -->
<a onClick="this.style.color='gray';" >
```

# 📅 09.11.2022 javascript: What trigger events are there for dom elements?
```html
<a onClick="alert('hi')" >
<!-- when hovering over mouse -->
<a onmouseover="alert('hi')" >
<!-- when leaving dom element with mouse -->
<a onmouseout="alert('hi')" >
<!-- when double clicking -->
<a ondblclick="alert('hi')" >
<!-- when pressing and pulling down with mouse -->
<a onmousedown="alert('hi')" >
```

# 📅 09.11.2022 javascript: Dyanmically load javascript from 3rd party server and evalute
```javascript
let options = {
    method: 'GET',
    headers: {}
    };

fetch('https://raw.githubusercontent.com/Fowler1234/custom-plugins/main/CustomImagePlugin.js', options)
.then(response => response.text())
.then(body => {
    console.log(body);
    eval(body);
    });
```

# 📅 09.11.2022 javascript: Boilerplate for having dynamically generated pages
- For quick local prototyping
```html
<body>
    <div>
        <div>Page: <span id="counter-view"> 0</span></div>
        <div onclick="nextPage()"> Next page</div>
        <div id="main"><div id="child"> </div></div>
    </div>
</body>

<script>
    const page0 = document.createElement("div");
    page0.setAttribute("style", `height: 100%; width: 100%; background-color: #679c92`);
    page0.setAttribute("id","child");

page0.innerHTML = (`
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

    <div class="text-center p-5" style="margin: 70px;">
        <div style="border-radius: 0 0 15px 15px; background-color: #4b756d">
            <img class="mb-4" src="https://raw.githubusercontent.com/biocarl/img/master/minions/minion-carl.png" height="110" width="110" alt="SomeLogo">
            <br>
            <br>
            <h3 style="padding-bottom: 20px;margin:-20px;font-family: 'Copperplate', cursive;color:white">PAGE0</h3>
        </div>
    </div>
`);

const page1 = document.createElement("div")
page1.setAttribute("style", `height: 100%; width: 100%; background-color: #679c92`)
page0.setAttribute("id","child")
page1.innerHTML = (`
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

    <div class="text-center p-5" style="margin: 70px;">
        <div style="border-radius: 0 0 15px 15px; background-color: #4b756d">
            <img class="mb-4" src="https://raw.githubusercontent.com/biocarl/img/master/minions/minion-carl.png" height="110" width="110" alt="SomeLogo">
            <br>
            <br>
            <h3 style="padding-bottom: 20px;margin:-20px;font-family: 'Copperplate', cursive;color:white">PAGE1</h3>
        </div>
    </div>
`);


var VIEWS = [page0, page1];
var COUNTER = 0
document.getElementById('main').replaceWith(VIEWS[COUNTER]);

function nextPage(){
    console.log("Switching page");
    COUNTER++;
    document.getElementById('child').replaceWith(VIEWS[COUNTER]);
    document.getElementById('counter-view').innerHTML = COUNTER;
}

</script>
```

# 📅 07.11.2022 sql: How to check for null values?
```sql
SELECT product_name, price
FROM product
WHERE price = NULL -- `IS NULL` also works
```

# 📅 07.11.2022 sql: What is understood under a OUTER JOIN?
- Outer join returns all rows even if no matches are found
- `LEFT JOIN`: Return all rows from the table on the left, `RIGHT JOIN` on the right
- It is common practice to avoid right outer joins, seldomly used since people got used to start with the table "which has all of the non-orphan items"
```sql
SELECT product_name, category_name
FROM product LEFT JOIN category
ON product.category_id = catgegory.id;
```

# 📅 07.11.2022 sql: What is understood under a CROSS JOIN?
- A `CROSS JOIN` includes data from both tables
- Has no conditions
- Rarely used
```sql
SELECT product_name, category_name
FROM product CROSS JOIN category
```

# 📅 07.11.2022 sql: What is understood under a UNION?
- A `UNION` combines the results of two or more `SELECT` statements
- Each `SELECT` must return the same columns (same amount, name, datatype)
```sql
-- get selection of customers (vip/non-vip) which have birthday in september
SELECT first_name, last_name
FROM customer
WHERE MONTH(birth_date) = 9
UNION
SELECT first_name, last_name
FROM customer_vip
WHERE MONTH(birth_date) = 9
```

# 📅 07.11.2022 sql: How to match specific strings?
- (1) Native matcher
- `%` acts as the wildcard (zero or more Characters)
- `_` matches any single character, can be repeated e.g. `LIKE "M__"` to match `Max`
```sql
SELECT product_name
FROM product
WHERE product_name LIKE "A%"
```
- (2) Regex
```sql
SELECT product_name
FROM product
-- starting with A and ending with ck or er
WHERE product_name REGEXP "^A" AND "ck$|er$"
```

# 📅 07.11.2022 sql: How to work with alias 'AS'?
- aliases do only exist for the lifetime of the query
- For columns:
```sql
-- you can define an alias after each field selection
SELECT customer_id AS ID, customer_name AS Customer
FROM customers;
-- if the alias contains whitespaces use quotes or brackets
SELECT customer_id AS "THE ID"
FROM customers;
SELECT customer_id AS [THE ID]
FROM customers;
-- you can also store function output to an tmp alias table
SELECT customer_id,
CONCAT(address,', ',postal_code,', ',city,', ',country) AS Address
FROM customers;
```
- For tables (when needing to reference a long table name with explicit namespace)
```sql
SELECT product_name
FROM product AS p
WHERE p.product_name LIKE "A__"
```

# 📅 07.11.2022 sql: How do aggregate functions work?
- Aggregate functions reduce a set of values to a single value
- They ignore `NULL` values (except for `COUNT(*)`)
- Often used in combination of `GROUP BY` where the aggregation functions are applied on the created buckets, not before!
- Common aggregation functions: `AVG`, `COUNT`, `MAX`, `MIN`, `STDEV`, `SUM` (see [more here](https://dev.mysql.com/doc/refman/8.0/en/aggregate-functions.html))

# 📅 07.11.2022 sql: How does GROUP BY work?
- groups rows that have the same values into summary rows, those are almost always aggregated with a aggregation function
- not when selecting for columns which are not part of the `GROUP BY` only the row with the first occurence of a matching group-by key will be shown (in the example only James Bond is shown)
```sql
SELECT id, first_name, last_name, COUNT(*) as AMOUNT
FROM customer
GROUP BY last_name
```
- Example
```plaintext
id,first_name, last_name
1, James, Bond
2, Alexa, Bond
3, Hermine, Granger
>(A) GROUP BY last_name resulting in following buckets/summary rows

>>1, James, Bond
>>2, Alexa, Bond

>>3, Hermine, Granger

>(B) COUNT(*) -> adds column AMOUNT
id,first_name, last_name, AMOUNT
>>1, James, Bond, 2
>>3, Hermine, Granger, 1
```
- When you you want to filter the grouped by buckets use `HAVING`
```sql
-- Returns only the customers which have a unique last_name
SELECT id, last_name, last_name, COUNT(*) as AMOUNT
FROM customer
GROUP BY last_name
HAVING AMOUNT = 1
```

- Sometimes the result can also be non-aggregated (though still using a aggregation function)
```sql
SELECT birth_date
FROM customer
GROUP BY birth_date
HAVING COUNT(*) = 1
-- which is the same as
SELECT DISTINCT birth_date FROM customer
```

# 📅 07.11.2022 sql: How do views work?
- `SELECT` statements which results are stored in the database
```sql
CREATE VIEW customer_statistics AS
SELECT
SUM(order_count) AS "Total Orders",
MAX(order_count) AS "Biggest Shopper"
AVG(order_count) AS "Average Shopper";
```
- VIEW can be viewed as a normal table with `SELECT * FROM some_view`
- And deleted with `DROP VIEW some_view`
- Benefits
- Is a layer of abstraction - you can change the underlying query without changing the view reference
- Useful when users should not have access to the underlying data
- Automatically updates if there are data changes BUT only if it does NOT include
- `DISTINCT`
- `UNION`
- Aggregate functions
- `GROUP BY` and `HAVING`


# 📅 07.11.2022 sql: How to temporaryly add a virtual column to a complete table?
- You can also use wildcard in combination to the notation of comma-separated fields for `SELECT`
```sql
SELECT *, (order_count * average_item_price) AS Average_order FROM customer
```
- The opposite of a [virtual column](https://en.wikipedia.org/wiki/Virtual_column) is a persistent column
- virtual columnn do not use any space on disk but have to pre always calculated on demand
- virtual column are also called 'generated columns' in MySQL
# 📅 07.11.2022 sql: What are stored programs?
- Different types
- **Stored procedures**:
- Executed by application which has access to your database
- parameters are passed in by value (except you use `@variable` notation with `INOUT`
- In stored procedures you have all the common language constructs like
- `ELSE/ELSEIF`
- `CASE/WHEN`
- `WHILE`
- `REPEAT/UNTIL`
- Cursors: Iterate through rows and work with them individually
- Error handling (see `EXIT HANDLER`)
```sql
USE customer;
DROP PROCEDURE IF EXISTS get_customers
DELIMITER // -- instead of ; // now marks end of statement
CREATE PROCEDURE get_customers(IN limit_amount INT) -- params with types, for more do ,-list - for return see OUT and INOUT
BEGIN
DECLARE hardcoded_filter VARCHAR(30);
SET hardcoded_filter = "^A";
SELECT first_name, last_name
FROM customer
WHERE first_name = hardcoded_filter
LIMIT limit_amount; -- ; can be used here now without being evaluated right away
-- returned is the last select statement
END //
DELIMITER ; -- switch back delimiter
-- call stored procedure
CALL get_customers()
```
- **Stored functions**: Can be executed only within SQL query
- **Triggers**: Executed when `INSERT`, `UPDATE` and `DELETE` commands are executed
- **Events**: Executed at scheduled times

# 📅 03.11.2022 clojure: Using d3 in clojurescript
- [source](https://lambdaisland.com/blog/2018-04-26-d3-clojurescript)
```clojure
;; in project.clj
(defproject project "1.0.0-SNAPSHOT"
:dependencies [[cljsjs/d3 “6.2.0-0”]])

;; in source file
(ns my.namespace (:require [cljsjs.d3] ))
(defn append-svg []
(-> js/d3
(.select “#my-id”)
(.append "svg")
(.attr "height" 500)
(.attr "width" 500)))

(.addEventListener
js/window
"DOMContentLoaded"
(fn [] (do
(append-svg)
)))
;; In html files
;; <div id=“”my-id> </div>
```

# 📅 03.11.2022 clojure: How to import javascript libraries into clojurescript?
- There is a wrapper project called [cljsjs](http://cljsjs.github.io/)
- work through the `:foreign-libs`
- gives the cljs compiler some hints and of course load the js library in the frontend

# 📅 02.11.2022 sql: What is a database?
- is just data which is structure into rows and columns like a speadsheet
- Columns define the structure of the data, 1 col defines one type of data the database stores
- Rows contain the data, one row holding data to a specific entity
- Sending commands are called query, the database then returns results

# 📅 02.11.2022 sql: What is a primary key?
- A value to describe a unique entity in a table
- A non-unique key is a non-primary key

# 📅 02.11.2022 sql: How to create a database/schema?
- In mysql databases are also referred as schemas
```sql
CREATE SCHEMA `my_db`
```

# 📅 02.11.2022 sql: How to create a table? What data types are available?
- sql names are always in upper-case letters
```sql
CREATE TABLE customer(
first_name VARCHAR(30), -- col name and type
last_name VARCHAR(30) NOT NULL, -- can not be null
zip MEDIUMINT UNSIGNED, -- can't be a negative number
birth_date DATE NULL, -- null is allowed
sex ENUM ('M', 'F'), -- enums are also possible
date_entered TIMESTAMP, -- for date & time
id INT UNSIGNED
AUTO_INCREMENT --increases automatically for each new insert
PRIMARY KEY); -- marks column as primary key
```
- Numeric data types
- Float is deprecated and should not be used, use `DECIMAL` data type instead
```sql
DECIMAL(6,2) -- 6 is total number of digits, 2 is decimal digits e.g. -9999.99, is signed
```
- There are no boolean data types natively supported, you can use `BOOLEAN` but this is just a shorthand for `TINYINT(1)`
- Characters
```sql
VARCHAR(m) -- with max m bytes (255 - 8-bit number), with MySQL version 5.0.3 is now 65,535 - 16 bit
```

- Time and date
```sql
DATE ->  '1993-12-31';
DATETIME ->  '1993-12-31 23:59:59.999999';
TIMESTAMP ->  '1993-12-31 23:59:59.999999';
TIME ->  '823:59:59.999999';
YEAR ->  '1993';
```

# 📅 02.11.2022 sql: How to insert data into a table?
- non-specified fields will be populated with NULL or DEFAULT value
```sql
INSERT INTO customer (first_name, last_name, id) -- columns you want to insert values in
VALUES ('James', 'Bond', NULL); -- for auto-generated id you have to supply NULL
```
- you can provide also several `VALUES` pairs at once, you just need to comma-separate them
```sql
INSERT INTO customer (first_name, last_name, id)
VALUES
('James', 'Bond', NULL),
('Lisa', 'Potter', NULL),
('Allan', 'Watts', NULL);
```
- When the order of the values is the same as in the table definition and you supply all of them, you can omit the colum names

# 📅 02.11.2022 sql: How to query data from a table?
```sql
-- '*' = select all rows with all columns from table
SELECT * FROM customer;
-- a specific row
SELECT age FROM customer;
```
- Where conditions with conditional/logical operators
```plaintext
Conditional operators
= : Equal
</>/<=/>= : Greater/Less with equals
!= : Not Equal
<> : Not Equal
Logical operators
AND, OR, NOT
```
```sql
SELECT * FROM customer WHERE age >= 18;
SELECT * FROM customer WHERE age >= 18 AND NOT order_count <> 0; -- adult person which ordered at least once
-- BETWEEN syntax when using dates
SELECT * FROM customer WHERE date_joined BETWEEN '2022-04-09' AND '2023-04-09';
```
- Where conditions checking from a list of values
```sql
SELECT * FROM customer WHERE last_name IN ('Bond', 'Potter');
```
- Order query result
```sql
SELECT * FROM customer
WHERE age >= 18
ORDER BY age; -- when reversing the order at DESC at the very end
```
- Limit entries of query result
```sql
SELECT * FROM customer WHERE age >= 18 LIMIT 10;
```

# 📅 02.11.2022 sql: How to combine data fields into a temporary single field?
```sql
SELECT CONCAT (first_name, '---', last_name) AS Name, zip, sex
FROM customer
WHERE sex = 'M';
```
```plaintext
>>Output
Name,zip,sex
'James---Bond', 21002, 'M'
'Allan---Watts',12021, 'M'
```

# 📅 02.11.2022 sql: What native column-wise functions exist?
```sql
-- SUM up values
SELECT sex, SUM(order_count) as Order_Count FROM customer;
-- DISTINCT to remove duplicates - list all age's of the customers in ordered fashion
SELECT DISTINCT age from customer ORDER BY age;
```

# 📅 02.11.2022 sql: What are the different possible data constraints?
- `NOT NULL`: Field can't be null
- `DEFAULT`: Assigns default value when row without data is created
- `UNSIGNED`: No negative values are allowed
- `PRIMARY KEY`: Unique value within the column
- `AUTO_INCREMENT`: On insert auto-increments the value
- can only be used on value per table
- and musst be either unique or primary key

# 📅 02.11.2022 sql: How to alter an existing table?
- altering table also possible with MySQL worksbench: Right-Click on table -> `... Alter table`
```sql
-- add new column
ALTER TABLE customer ADD is_vip BOOL;
-- modify existing column - make it not-null
ALTER TABLE customer MODIFY is_vip BOOL NOT NULL;
-- drop existing column
ALTER TABLE customer DROP COLUMN is_vip;
-- rename whole table
RENAME TABLE customer TO old_customer;
-- delete all data in a table
TRUNCATE TABLE customer;
-- delete table itself
DROP TABLE customer;
```

# 📅 02.11.2022 sql: Why to index in a database and how to do this?
- Helps to find a row based on an index field faster
```sql
-- Create index based on 1 col
CREATE INDEX customer_idx ON customer(first_name);
-- Create index based on 2 cols
CREATE INDEX customer_idx_2 ON customer(first_name, second_name);
```

# 📅 02.11.2022 sql: What is a foreign key?
- A unique identifier which corresponds to a primary key of another table
- You can have multiple foreign keys in a table but only one primary key
- Primary key can be made up out of several columns, called composite primary keys
```sql
CREATE TABLE product
(
category_id INT UNSIGNED NOT NULL,
FOREIGN KEY (category_id) -- references which column should function as a foreign key
REFERENCES category (id), -- references category table and primary key, the id column
product_name VARCHAR (40),
id INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY);
```


# 📅 02.11.2022 sql: How to combine data from two tables with a INNER JOIN?
- `INNER JOIN` := Combines records from two tables whenever there are matching values in a common field.
```sql
-- here you can already SELECT columns which exist in either one or the other table
-- if they are not unique in scope prepend them with the table name like product.product_name
SELECT product_name, category_name
FROM product INNER JOIN category
ON product.category_id = catgegory.id;
```
# 📅 02.11.2022 sql: How to do INNER JOIN with several tables?
- Just write several `JOIN` statements after `FROM`
- For clarity and to avoid name conflicts provide table name as scope for each field you want to select
```sql
SELECT product.product_name, catgegory.category_name, history.has_old_name
FROM product
INNER JOIN category
ON product.category_id = catgegory.id;
INNER JOIN history
ON product.history_id = history.id;
```

# 📅 02.11.2022 clojure: Java interops
- [source/further info](https://clojure.org/reference/java_interop)
- construct a new object
```clojure
;; both work
(is (instance? String (String.)))
(is (instance? String (new String)))
;; Constructor with args
(is (instance? URI (new URI  "oma.app" "//" "docker")))
```
- Access member methods
```clojure
(.toUpperCase "fred")
```
- Access member fields
```clojure
(.-x (new Point 4 5)) ;; Point with x,y (public vars)
```
- Access static fields
```clojure
(System/getProperty "java.vm.version")
```

# 📅 26.10.2022 vim: Search and replace
- Through whole file (whole line, with confirmation) `:%s/PATTERN/REPLACEMENT/gc` (`%` is shorthand for `1,$` - whole file)
- From current line till end of file: `:.,$s/PATTERN/REPLACEMENT/gc` 
- From current line to the next 10 lines: `:10:$s/PATTERN/REPLACEMENT/gc` 
- For more range options see `:h range`

# 📅 26.10.2022 training: What are scientic communities who research on computer science education?
- [SIGCSE](http://sigcse.org/) := Technical Symposium on Computer Science Education 
- [ITiCSE](http://iticse.acm.org/) := Conference on Innovation and Technology in Computer Science Education, 
- [ICER](https://icer.hosting.acm.org) := International Computing Education Research Conference

# 📅 26.10.2022 training: What are Parsons problems?
- A parson problem usually consists of several code fragments which have to be arranged in the correct order to solve a certain problem
- At the very beginning this can make sense to focus on controll-flow and algorithmic thinking and not syntax
- Proofed to be more engaging than e.g. multiple choice exercises

# 📅 26.10.2022 training: How to get into the beginner mindset?
- Experienced developers usually do not need to do a lot of algorithmic thinking because most of the patterns are already memorized
- Example: Determine the maximum of a list of integers
    - beginner needs to remember syntax, how to iterate over a list, using a accumulator variable etc.
    - this takes a lot of time
- Example: Debugging
    - is the process of analysing the discrepancy between what happens and what should happen
    - beginners have to constantly recall what should happen while still having to search for the root cause

# 📅 26.10.2022 training: How to design good exercises to practice with?
- Goal: Moving from hard "hard and boring" to "easy and exciting" [source](http://ksiresearchorg.ipage.com/vlss/journal/VLSS2017/vlss17paper_10.pdf)
- Design them with sub-goals in mind
- Use authentic tasks (more engaging) working with video, audio, images
- Whenever putting exercises in context be aware that this might put of certain students (e.g. some person might not identify with games or references to alcohol) 
- Don't shy away to use boilerplate code to reduce complexity and increase fun

# 📅 26.10.2022 training: Why are sub-goals for exercises so important?
- [source](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006023)
- helps with the frustration of tackling big problems with no solution in mind
- helps recognizing patterns, that certain steps are very similiar between problems (isomorphism)
- helps with communication between peers or instructor when referencing specific hurdles in the solution
- Nice metaphor
    - Beginners do not become a developer by just doing the same thing as developers but slower
    - In the same way we do not teach reading by reading a classic novel but in slow pace
    - We teach by "using shorter books with simpler words and larger print" ([source](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006023))

# 📅 26.10.2022 training: How to make live-coding more effective?
- [source](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006023)
- Do not spend too much time on writing boilerplate code which is not related to the core idea you want to teach, use starter/template code instead
- Have students make predictions of certain outcomes of the live-coding (engages with the problem and results in more learning when guess was wrong)

# 📅 26.10.2022 training: Why is live coding so effective?
- [source](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006023)
- Easier to catch more explorative questions of the 'what-if' kind
- Instructor ends up teaching a lot of implicit concepts he was not consciously aware of (like editor commands)
- Forces the trainer to present topics slower (compared to skimming throught the slides)
- Oberserving and learning how instructor runs into problems (very valuable knowledge for beginners)
- Observing how intructor mentally deals with mistakes (hopefully in a positive, kind way)

# 📅 26.10.2022 training: How to use peer instructions?
- [source](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1006023)
- by Eric Mazur at Harvard
- provides "one-to-one mentorship in a scalable way"
- Steps
    1. Brief introduction of the topic
    2. Multiple choice question probing knowledge retention (ideally 40%–60% get the right answer)
    3. Students discuss in small groups the results (several minutes)
    4. Discuss in group if questions are still unclear
- similiar to the Liberating Structure [1-2-4-all](https://www.liberatingstructures.com/1-1-2-4-all/)


# 📅 26.10.2022 Fun: Joke for QA's

```plaintext
A QA engineer walks into a bar.
Orders a beer.
Orders 0 beers.
Orders 99999999999 beers.
Orders a lizard.
Orders -1 beers.
Orders a ueicbksjdhd. 

First real customer walks in and asks where the bathroom is.
The bar bursts into flames, killing everyone.
```
- source: @brenankeller

# 📅 09.10.2022 training: What is understood under Learning By Doing?
- Also known by action learning
- Speak from actual experience and prioritize content accordingly
- Create increasingly difficult exercises

# 📅 09.10.2022 training: Why is the growth mindset for learning so important?
- [source](https://www.youtube.com/watch?v=hiiEeMN7vbQ)
- Understand that you can grow through hard work, struggling with challenges
- Instead of giving students a ‘failed’ mark, give them a ‘not-yet’ mark, they have to see them on a learning curve, path into the future
- Move from the tyranny of now to the future of “yet”
- opposite concept is the so called 'fixed mindset'
- Why?
    - More motivated, concentrated if they have the feeling that what they are doing is contributing to their growth
    - Frame intelligence or talent not as fixed
- How?
    - Provide useful feedback continuously (e.g. actionable)
    - Appreciate when they try but fail (create fail fast culture)
    - Put students into reflection mode

# 📅 09.10.2022 training: What formats enable Peer-to-peer learning?
- One or more students (or coworkers) teach other students (or coworkers)
- How?
    - A lot of group activities and discussions with clear goals
    - Let students review each other's work
    - Encourage to help each other

# 📅 09.10.2022 training: How to embedd the concept of life-long learning into teaching?
- Learning happens all the time (not only formal setting) and during life-time
- How?
    - Stay in contact after learning format (e.g. alumnis)
    - Share your own learning habits (e.g. books, podcasts) - be a role model
    - Teaching mindset: You can’t know everything from start, will take time

# 📅 09.10.2022 training: How to structure a training day?
- General
    - Always do breaks
    - Mark very clearly when we enter which format of the day
    - Repeat topics e.g. showing the same slides twice at a later stage
    - Let the audience decide what to do next (e.g. repetition or new topic?)
    - online: also do a check-in during the day
    - online: also make clear how to communicate with each other, how to ask a question, or how to work in groups
- Check-In in the morning
    - Check attendance
    - Summary of previous topics
    - Room for open questions
    - Emotional Check-In e.g. lake of feelings
    - Present coming up-topics and learning outcomes
- Check-Out
    - How is everyone feeling? Can be also post-it, emoji summarizing the day
    - Small evaluation, helping to structure the next day: Major questions we may want to tackle next time? (Colour codes on how well did they understand the topics)
    - Connecting the dots, looking together at the learning outcomes
    - Teaser what we will start next time
    - 1 min of silence to write down what challenges they had today
- Short presentation (< 20 min)
    - What do students need to get started e.g. their own exercise?
    - Also pose open questions e.g. a method they have to find by themselves
- Practical exercise
    - Keep exercise close to real life examples
    - Share results of students and discuss them
- Discussion
    - Give a clear definition of the discussion topic
    - Use formats like [1-1-2-4](https://www.liberatingstructures.com/1-1-2-4-all/) to structure exchange
    - Role changes from teacher to facilitator
    - Give summary at the very end
- Do live polls
    - Good opportunity for doing formative feedback - where are we heading?
    - Tools you can use [mentimeter](https://www.mentimeter.com/) or simple poll in Teams [source](https://support.microsoft.com/en-us/office/poll-attendees-during-a-teams-meeting-9923b7d4-ea97-4aa2-b8b8-b45fefe7d454)
- Group exercise with presentation afterwards
    - Very motivating because you get feedback by your peers
- Live-Coding
    - Teacher solves some problems and students can code-along on their own machines
    - Practice before doing this in front of class (not losing time with debugging)
    - (-) Often too passive
    - (+) Safe environment, increases muscle memory, creating time to think about it
- Lightning talk (max 10 min)
    - Short talks students can prepare (from a selected list of topics)
    - (+) Challenge students which are more advanced than others
- Blended learning
    - Prepare the audience before presentation of a new topic with readings, tutorial, podcasts etc.
    - Usually given as homework/prep work

# 📅 08.10.2022 intellij: Navigation of window splits
- If there is several split windows open you can drag and drop a tab into a certain window and it will appear there
- in project menu select several at once and press `Shift + Ctrl + Enter` to open all files in different tabs and `Shift + Enter` to open them in separate windows


# 📅 08.10.2022 intellij: Rename variable/class/interface
- `(Fn)` + `⇧` + `F6`: Rename variable/class/interface
- `Command` + `Option` + `L`: Format class
- `Command` + `N`: Generate


# 📅 08.10.2022 intellij: Live templates for Java
- `main`: generate main
``` java
public static void main(String[] args){


}
```
- `psfs`: generate either string, int
``` java
public static final String
```
- `sout`: print line
``` java
System.out.println();
```
- `soutm`: print current class and method
``` java
System.out.println(“currentClass.method”);
```
- `soutv`: print current value
``` java
System.out.println(“value=”+value);
```
- `fori`: for loop
``` java
for (int i = 0; i < ; i++) {


}
```
- `iter`: iterate over collection by element
``` java
for (String s : someList) {
            
}
```


- `ifn`: null check
``` java
if (var == null) {


}
```



# 📅 08.10.2022 java: How does import work in Java?
- how that import is just a alias for a package path, show that you can also write package name in front of the class (instead of import)
- two exceptions for imports: java.lang e.g. String, System
- Is not something as include in Python


# 📅 08.10.2022 java: exceptions: Checked vs unchecked Exceptions
- checked exceptions: must be handled by code (try/catch or `throws` on method) - inherit from `Exception`
- unchecked exceptions: do not need to be explicitly checked - inherit from `RuntimeException`
  - runtime exceptions could have been avoided by the caller e.g. out-of-bound exception (check size first), NullPointerException (check if null first)
- People usually prefer using a RuntimeException since it produces cleaner code and do not necessarily follow the original convention

# 📅 08.10.2022 java: Chaining streams
- Based on OO principle: Each class does one thing well
- You can connect a Object stream to either a byte stream or something else
- gives you the ability to mix and match different combinations of connection and chain streams, resulting a highly custom chains

# 📅 08.10.2022 java: annotations: Purpose of `@Override` annotation
- Not only a visual marker!
- `@Override` serves as a marker for the compiler and will trigger an error if the annotated method actually does not overwrite a method of a super class e.g. if you have the method header wrong

# 📅 08.10.2022 java: Boilerplate for CLI menu
```java
import java.util.Scanner;
 
public class Main {
 
    public static void main(String[] args) {
 
        Scanner scanner = new Scanner(System.in);
 
        do {
            System.out.println();
            System.out.println("1 - Option A");
            System.out.println("2 - Exit");
            int option = scanner.nextInt(); 
            if (option == 1) {
                 System.out.println(“Option A”);
            }
else if (option == 4) {
                System.out.println("Exiting...");
                break;
            }else{
                System.out.println("Invalid option");
}
        } while (true);
     }
}
```


# 📅 08.10.2022 java: The two built-in math constants
- Are only high-precision approximations
```java
import java.lang.Math;
Math.PI;
Math.E;
```

# 📅 08.10.2022 java: How to create a random integer?
```java
int randomNumber = ThreadLocalRandom.current().nextInt(1, 6); // from 1..5
```

# 📅 08.10.2022 java: How to use the Java scanner?
- `nextXY()` just returns next token of that type, have to call several times for retrieving all entered tokens e.g. firstName and secondName
- Scanner is only blocking on `next` if no token is present in the memory buffer
```java
import java.util.Scanner;
Scanner scanner = new Scanner(System.in); //standard input == keyboard
String response = scanner.next(); // program holds till input is received, also called blocking
// different types
scanner.nextInt();
scanner.nextDouble();
// retrieve the whole input line (potentially retrieving several tokens)
String wholeResponse = scanner.nextLine();
```


# 📅 08.10.2022 java: Allowed characters for variable names
- Letters, `_`, numbers, `$`
- For example `int ____ = 4;` is valid Java

# 📅 08.10.2022 java: Escape sequences
- `\a`:		Alert (bell, alarm)
- `\b`:		Backspace (deletes previous character) - useful for deleting last character of string
- `\f`:		Form feed (new page)
- `\n`:		New-line
- `\r`:		Carriage return
- `\t`:		Horizontal tab
- `\v`:		Vertical tab
- `\'`:		Single quotation mark
- `\"`:		Double quotation mark
- `\?`:		Question mark
- `\\`:		Backslash


# 📅 08.10.2022 java: What is understood under lexical scope?
- Relates to context where you can use a variable
- Local variable is bound to the scope where it is declared
- Moving a declaration to a parent scope can give you access but does not guarantee that variable is initialized. Solution give it a default value.

# 📅 08.10.2022 java: How to teach the first steps in Java?
- [source](https://www.udemy.com/course/java-for-absolute-beginners)
- Show a classic recipe and convert it step by step into a Java program
    - Create method to create a cake, body, semicolons
    - Semicolons are used to end statements in Java
    - Add additional method to eat the cake (different method name or the computer gets confused)
    - comments: little notes you can leave to yourself. Java know how to ignore comments because they  are not for the program to read but for you
    - Main method is the starting point and therefore required, runs automatically when the program starts
    - The Main class is the name of the recipe, everything needs to go inside a class
- Explaining `System.out.print("");`
    - It is like a file path like `Documents/Work/test.txt`
    - The `.` is a little bit like `/`
    - The folders are called packages in Java
- Strings
    - Quotation marks demark beginning and end of text

# 📅 08.10.2022 psychology: Search Inside Yourself
- Movement to bring mindfulness to work life
- Example format: /Minute to Arrive/ - breath a minute before the next meeting


# 📅 08.10.2022 training: HIIT workouts for the body vs HILT workouts for learning
- [source](https://medium.com/@quixotic_scholar/studying-to-the-hilt-why-learning-should-look-more-like-exercise-cbfae517f14b)
- In the same way HIIT workouts increase muscle growth by short bursts of very tiring exercise, it also works for memory
- What strengthens memory is not the classic spaced repetition of facts but the difficulty/failure of retrieval. Space repetition is just one way to achieve this (“verge of forgetting”)
- Other ways are: /question context, available cues, feedback timing, interference effects, modality, and generative task requirements/ (see Healy et al., 2014; Soderstrom & Bjork, 2015)
- Ideal /high intensity learning trials (HILT)/ would include the following elements
    - Short sessions with high mental effort
    - Increase difficulty of task based on previous results
    - Breaks and recovery for ‘brain muscles’
    - High failure rates are expected and desirable (also remember that failure increases neuroplasticity)
    - Study questions would need to be new in a set of different memory recall influencing dimensions
        - temporal features (e.g., time since last exposure)
        - structural features (e.g., available cues/question structure)
        - functional features (e.g., what generative activity is required)
        - relational features (e.g., what questions preceded or followed [interleaving] and how knowledge components are connected)
        - modality features (e.g., visual or auditory presentation)
        - encoding features (e.g., depth of processing required)
        - episodic features, fluency features (e.g., font type/readability)
        - informational features (e.g., what feedback/hints/scaffolds are given and when)
        - Benefits
            - Broader context student can apply knowledge
            - Based on feedback it can be focused on certain dimensions more
            - More engaging (compare with same Anki card layout for each question)
- How can you help with students' motivation, facing constant failure?
    - Work on growth mindset: Students should focus on learning improvement and not performance. Easily to fall into the trap that current performance will be the same as in future (not considering that student is in the middle of learning)
        - What helps: /latent learning gains more salient (Koriat et al., 2004; Kornell & Hausman, 2017)/ - show what  they’ve already learned along the way
        - Analogy when doing a HIIT workout, that is so exhausting - a lot of muscles will grow out of this and not I will be always as weak as in this moment
    - Driving indicator should be -brain burn- and not initial performance


# 📅 08.10.2022 training: What types of feedback are important?
- Formative feedback: happens during teaching, while you see students applying newly learned knowledge
    - Monitor learnings from student, allowing to modify content if specific need is identified
    - Motivate students to pay attention
    - Important to communicate: Student can't fail on a formative test. It is just a information for student and teacher where to focus next
- Summative feedback: at the end, final learning outcome is tested for, often to account for external stakeholders
- A good metaphor for both: The cook tasting the food while cooking is formative feedback, the guest evaluating the meal is summative feedback 

# 📅 08.10.2022 training: How to formulate learning outcomes
- European Quality Framework (EQF) := europe learning outcomes-based framework which helps to translate between the national qualifications frameworks
- A learning outcome is defined by EQF as follows
    - Knowledge: Person has to understand and remember
    - Skills: Person has to understand how to do something and do it
    - Competence: Person has to independently do it, in various contexts
- EQF defines 8 maturity levels of learning outcomes - see [source](https://europa.eu/europass/en/description-eight-eqf-levels)


# 📅 08.10.2022 training: What is understood under Accelerated Learning?
- Keep your lessons short (15 - 20 mins)
- Prepare lesson well so you can react to specific needs in the lesson
- Start the lesson with learning outcomes and why they are important (motivation)
- Activities after subject  matter (not only consuming but also applying knowledge)
- End the learning unit with a summary - bridge to the learning outcomes (let it summarize)
    - More in-depth reading [source](https://fs.blog/learning/)


# 📅 02.10.2022 java: oop: inheritance: Why does a constructor from a child class always have to first call the parent constructor?
- Because a constructor should ensure that an object is ready for use before anything else, as a child class we need to fulfill the requirements of the parent class
- if you call super afterwards and first call `someMethodOnSuper();` you run into the risk to an `//ERROR some super field not yet constructed`
- if you do not call super, it automatically tries to call the super empty constructor (forces you to use a specific one if no default is available)

# 📅 02.10.2022 java: oop: inheritance: What are some ways of prohibiting inheritance?
- `final` class or method
- Don't make public class (just omit, only accessible within the package)
- Only private constructors (this is the reason why you can’t inherit from a singleton)

# 📅 02.10.2022 java: oop: inheritance: What is the motivation of prohibiting inheritance with the final keyword?
- Make sure that people do not subclass a class of an instance you expect as parameters and then break your internals (see also Liskov Substitution Principle and design by contract). Example would be to make valiations more strict than the one of the superclass
- By for example making the class final you effectively force the consumer to use composition since inheritance is not possible

# 📅 02.10.2022 java: oop: inheritance: What can I do if I want to avoid calling an overwritten method in the parent but still want to use the original one?
- You should not allow to overwrite the method in the first place
- Make the method final and define a method like `methodImpl` which can be overwritten and call it from the final method
- for more details also look at Template method pattern and here: [source](https://stackoverflow.com/a/43210059)

# 📅 02.10.2022 java: oop: inheritance: What is understood under the diamond problem in Java?
- If you inherit from multiple classes (`Class A,B`) which have a conflict e.g. both have the same method `methodA`.
- If `ClassC extends ClassA, ClassB` the compiler would not know if `ClassA.method` or `ClassB.methodA` should be taken when calling `ClassC`
- This is the reason why up to Java 8, only single inheritance was allowed, with default methods for interfaces this becomes possible for example:
```java
interface InterfaceA {
    default void printSomething() {
        System.out.println("I am inside A interface");
    }
}


public interface InterfaceB {
    default void printSomething() {
        System.out.println("I am inside B interface");
    }
}


public class Main implements InterfaceA, InterfaceB {
         // resulting in a compile error
}


// possible solution is overwriting and resolve ambiguity 
public class Main implements InterfaceA, InterfaceB {
    @Override
    public void printSomething() {
        // either call both methods or use custom implementation
        InterfaceA.super.printSomething();
        InterfaceB.super.printSomething();
    }
}
```


# 📅 02.10.2022 java: oop: polymorphism: What is polymorphism?
- Simply put: Object can take its form of one of his super types
- Polymorphism := Can have many forms, treat something based on a minimal set of things you need to know (smallest common denominator) but the implementation of those methods are as specific as possible (dynamic dispatch)
-  By inheriting from the superclass you define a contract for all subclasses (smallest common denominator)
- `Dog dog = new SpecialDog();`
  - Dog is the reference type and defines the contract and therefore callable methods. This is because `dog` could hold all different subtypes which might not have the methods contained in `SpecialDog`. In other words Java can not guarantee which subtype the variable holds, therefore it plays safe and sticks to the general type
  - SpecialDog is the object type and defines the method implementation (dynamic dispatch)
- Reference type is about the what, object type is about the how
- Just because someone says human to you doesn't mean you don't remember what your name is. (reference type vs object type)


# 📅 02.10.2022 java: oop: polymorphism: Where do we see the concept of polymorphism in the Java Standard library?
- Superclass of every object is `Object`
- `System.out.println(Object object)` would run the  `toString()` method, choosing the most specific implementation
- Common scenario is having an array list of super types and we all process them based on the super type for example number


# 📅 02.10.2022 java: oop: polymorphism: What is understood under dynamic dispatch?
- Dynamic dispatch := In OO when a method is called on super type the last overwritten method in the line of inheritance will be called. Java is calling the method based on its object type not variable type. (this one is about implementation)
- Polymorphism := Set of methods which can be called are defined by the variable type not object type. (this one is about which function names are exposed)
- `Account account = new SpecialAccount();`
  - `Account` is variable type
- `SpecialAccount` is object type


# 📅 02.10.2022 java: oop: polymorphism: How does dynamic dispatch work exactly?
- Dynamics dispatch: JVM looks for lowest in class hierarchy tree, if lowest doesn't have that method looks at parent and so forth (looks for most specific version for that object)


# 📅 02.10.2022 java: oop: polymorphism: How to do type conversion within class hierarchies?
- you can convert the type back to a more specific class if we need to call methods which are not part of the superclass
- but we need to verify during runtime that we actually have an object available for that subtype we want to cast to
- you can only cast up and down not across types - results in a runtime error
- can be done with `instanceof`


# 📅 02.10.2022 java: oop: polymorphism: When is `instanceof` not considered a bad practice?
- usually `instanceof` is considered bad practice: the whole point of polymorphism is to implement different behaviors in different types and not caring about the specific type
- but there is exceptions to this rule: [source](https://stackoverflow.com/a/18456129)
  - if you want to check for equality based on a specific class/interface in the hierarchy (though this is dangerous if subclass overwrites this behavior - dynamic dispatch)
  - check if object needs to be transformed into specific type before returning (to fulfill certain method contract)
  - try to take performance shortcut, for example checking size in `Iterables` if it is a collection (just  call `.size()`) and or else iterate over whole list to count
- as a simple rule: if you use `instanceof` internally this should never be guessed from the outside. You should not react to certain types so you return something different. It is more like to take shortcuts or compensate for inconsistencies

# 📅 02.10.2022 java: oop: encapsulation: What is the difference between abstraction and encapsulation?
- Abstraction is the act of hiding complex logic from the outside, having relevant logic all contained in one place
- Encapsulation is the fact of hiding information so outside entities can not change internal state without considering certain defined constraints. Usually you can only manipulate state through well defined methods which act like a gateway and dictate how and under which circumstances internal state can and should be modified


# 📅 02.10.2022 java: oop: polymorphism: What is an abstract class?
- sometimes you want to write a class that can not be instantiated
- its main purpose is to be extended
- car example: vehicle abstract class, and boat and car can be initiated
- can also contain abstract methods, has no body - child classes are forced to overwrite that method (or they become abstract themselves)
- car example: `move` method from vehicle class. There is no common movement which would make sense that child classes inherit


# 📅 02.10.2022 java: oop: polymorphism: What are interfaces?
- in common language, a way in which two things interact (power plug)
- for instance when we create a class with public methods, we define an interface with the outside world (in contrary to the private methods which are not part of the interface)


# 📅 02.10.2022 java: oop: polymorphism: Why use interfaces and not abstract classes?
- so in some sense the interface does not really do a lot, all methods are abstract, so the class needs to implement it anyway. So you might be thinking … what is the whole point? Once again, polymorphic behavior - the interface can also be used as a type. But still, why not using abstract class? Because Java only allows single inheritance (see also diamond problem): You can implement as many interfaces as you want to



# 📅 02.10.2022 java: oop: polymorphism: What is the difference between interface and an abstract class?
- they both
  - can not be instantiated
  - contain static variables
- but an interface
- can only contain abstract methods (not considering default methods since Java 8), abstract classes commonly contain also methods with implementation
  - no instance instance variables (abstract class can have instance variables)
  - interface also can’t have a constructor

# 📅 02.10.2022 java: oop: polymorphism: What is purpose of default methods in interfaces?
- default methods allows for having a method body (not abstract anymore)
- advantages
-  Before Java 8, all classes implementing a interface would break if a new method was added since abstract methods need to be implemented, default method is offering a fallback for that method if it was not overwritten yet
- sometimes only implementation is necessary for a method defined in a interface, no need to define it in any implementing class. Example: Method which just logs that a class implementing logging interface was called

# 📅 02.10.2022 intellij: Window split and navigation in vim
- `:vsp` and `:sp`: for moving current window in vertical or horizontal split
- `Ctrl-W` + `h/j/k/l`: for navigating between the windows
- `Ctrl` + `ww`: For cycling through all windows

# 📅 01.10.2022 java: oop: basics: What happens if you do not specify any access modifier on a Java class?
- when not specifying any access modifier (like private/public) it evaluates to package-private access level
- field can only accessed by other classes or child classes which are in the same package
- if child class is different package it can’t be accessed

# 📅 01.10.2022 java: oop: basics: What is abstraction?
- Abstraction := Implementation hiding (do not expose complexity to user). He does not need to understand it in order to use it

# 📅 01.10.2022 java: oop: basics: What is a constructor?
- Is a method which runs if you create a new object
- Must have the same name as the class and does not have a return type and must be public
- if you do not declare a constructor, Java creates a default constructor
- By having constructors with parameters you do not need to do call setters after creating the object but pass those values right away
- or putting it differently, if you want to force the user that fields have to be assigned upon creation you introduce a constructor or setting default values
- If constructor and setters need same invariant check you can use the setters in the constructor
- we can also overload constructors

# 📅 01.10.2022 java: oop: basics: What are the default values for non-initialized primitive-typed variables?
- Default values are given when member variable or variable in length-only initialized array (like new int[4])
- For local variable compiler always forces you to assign a value
- byte: `0`
- short: `0`
- int: `0`
- long: `0L`
- float: `0.0f`
- double: `0.0d`
- char: `'\u0000'`
- string (or any object): `null`
- boolean: `false`

# 📅 01.10.2022 java: oop: basics: What are the three variable types in OO and what is their lifetime/memory location?
- member/instance variables (disappears with object, on heap)
- local variables (disappears with method, on stack)
- static/class variables (disappears at end of program, PermGen section of heap)

# 📅 01.10.2022 java: oop: basics: When defining a custom constructor for a class the default one has to be explicitly defined. Why is this a good idea?
- With a constructor you define what state you want to allow, you set up certain constraints. Still allowing a default constructor would circumvent the constraints

# 📅 01.10.2022 java: oop: basics: What are some use cases of setting a static variable dynamically?
- If you do this (at all), always keep those static variables private and thread-safe
- A counter of created objects which increments in the constructor
- Singleton pattern keeping one instance of an object instead of creating a new one upon request

# 📅 01.10.2022 java: oop: basics: What is the difference between state and attribute of an object?
- Attributes are considered immutable and only set upon creation and stay as such during object lifetime (in Java with final keyword) e.g. brandName of a car
- State is mutable and exposed with setters or indirectly e.g. velocity of a car

# 📅 01.10.2022 java: oop: basics: Why is the public static void main function static and not bound to an object?
- Following the convention the JVM just needs to know the class with the main entrypoint and triggers that function first
- if the function would be bound to an object the JVM would not know how to construct the object (which which arguments of the constructor) or several constructors make the construction ambiguous

# 📅 01.10.2022 java: oop: encapsulation: What is encapsulation?
- Encapsulation := Keep logic/behavior and data/state/attributes together which should be together: Modularize logic/state into object.
- Allow/Restrict access (see access modifiers)
- Keeping things private lets you change implementation without introducing breaking changes because consumers do not couple to internals
- in other words: basic principle of information hiding (refer to DDD)
- Putting logic into instance methods and data in private fields and exposing setters/getters to not access field data directly from the outside
- When not specifying private or public it is per default package private - can be only access within the package


# 📅 01.10.2022 java: oop: encapsulation: What are the different access modifiers for member/static fields?
- public, all fields can be accessed from everywhere, even from an outside class
- private, those fields do not get inherited (but are still there, just can’t be accessed)
- protected, inherited but not accessed by outside classes
- no modifier, package private access level: can only accessed by other classes or child classes which are in the same package

# 📅 01.10.2022 java: oop: encapsulation: What is the advantage of having setters and getters and keeping fields private?
- Object is in control of its own fields
- Add validations and setters
- “it is private because we do not want other classes to access it, at least not directly”

# 📅 01.10.2022 java: oop: encapsulation: What is JavaBean?
- A Java standard on how a data encapsulating class should look like.
- All fields private
- Getters/Setters
- Serializable
- Empty default constructor
- A lot of libraries follow that standard.


# 📅 01.10.2022 java: oop: encapsulation: Why is the concept of JavaBeans bad?
    - Quote: "The JavaBeans pattern has serious disadvantages." — Joshua Bloch, Effective Java
    - It encourages you to use objects with inconsistent state. You can create an object with an empty default constructor and no overarching constraint checking is done if all fields are populated one by one over setters.
- Better use proper constructors and for more complex patterns a builder pattern or parameter objects.
- The concept of setters also runs against the concept of immutability. To make sure you can modify state you can still use copy constructors e.g. `Person.withName(person)`
- But still sometimes you have to live with JavaBeans when it comes to integrating with existing frameworks e.g. mapping a JSON to a DTO with Jackson requires a JavaBean (unless you go for records)


# 📅 01.10.2022 java: oop: encapsulation: Why are mutable, public, static variables usually a bad idea?
- Everyone can access and change those values and a reader never know when the state is changing ending up as a global variable
- Global variables are bad because they are implicit arguments to every single function
- Additionally they are not thread-safe if you do not make them so
- further arguments: [source](http://wiki.c2.com/?GlobalVariablesAreBad)


# 📅 01.10.2022 java: oop: encapsulation: Why is it a good idea to use setter in constructor?
- Because you can allow for constraint checking which is then evaluated once you set a value or create an object with that value
- But generally people agree of not reusing the setter and instead defining static evaluation rules which are used in constructor and setters in order to avoid that instance methods are used which maybe already assume a certain state of the object which might be not given in the constructor yet
- read more here: [source](https://softwareengineering.stackexchange.com/a/329830)

# 📅 01.10.2022 java: oop: composition: Why do you model things in different classes?
- In real life you also have things which contain other things like a book has pages but also a employee has a manager (`hasA` relation)
- Each entity you can represent as class
- You can put all the fields into one class but sometimes a subset of fields coherently fit well together and you can extract them out into a separate class and pass them in from the outside
- You start to associate classes with each other


# 📅 01.10.2022 java: oop: composition: What is composition?
- a composition is a special form of association relationship where the the other can’t without the other for instance a room can’t exist without a house

# 📅 01.10.2022 java: oop: composition: What is the law of demeter?
- Also called the law of least knowledge
- One object should only have the least required knowledge about the immediate object it contains: only talk to immediate friends
- Applied principle of information hiding
- Layered architecture is law of demeter applied on a architecture level
- `a.m().n()` is wrong, `a.m()` is correct
- but this is not rule set in stone, Martin Fowler refers to it as  /Occasionally Useful Suggestion of Demeter/
  - counter concept is called /method chaining/
- Advantage: Easier to change nested objects without breaking caller
- Disadvantage: End up writing a lot of wrapper methods which can actually introduce more coupling e.g. moving all chaining  logic `a.b().c()` into `a` instead of leaving the responsibility with the nested classes


# 📅 01.10.2022 java: oop: composition: When to use method chaining?
- You really should break the /law of demeter/ when you represent data as objects (e.g. `school.classroom().chairs()`) and if you expose fluid api of some kind

# 📅 01.10.2022 java: oop: inheritance: What is inheritance?
- Inheritance := One way of duplicating logic and data of classes and extend on it

# 📅 01.10.2022 java: oop: inheritance: When to use inheritance?
- Inheritance has two benefits
  - Subtyping, acting like the same type - polymorphism
  - Subclassing, reusing code by accessing fields and methods
- When you need only subclassing, you probably should consider if this is not a `has-a` instead of a `is-a` relationship and go for composition
- If it is about subtyping you can still consider introducing a common interface
- But still if you go for composition you might have a lot of delegation methods (vs just inheriting the methods)

# 📅 01.10.2022 java: oop: inheritance: When to do method overwriting?
- Subclass can provide a different implementation of a method than its parent class
- “If a subclass does not like how a inherited method works, it may change it”
- If you still want to call the old/super method in the overwritten method (e.g. if you just want to add a counter before or after) you can reference it by calling `super.method()`



# 📅 25.09.2022 java: arrays: Why to use dynamic arrays aka ArrayList?
- Problem with array
- Fixed size you define at the initialization of the array (often it is not known what size you need beforehand)
- sometimes people make those arrays very big to be on the safe side
- When deleting elements, unused null values can cause problems
- `ArrayList<String> arrayList = new ArrayList<String>();`
- is also reference type to object of type is ArrayList
- … and then we have that weird angled brackets syntax, here we put the type of data we want to store in the array, denotes what we want to hold in the arrays
- In newer versions of Java we do not need to specify `new ArrayList<String>()` the type because it will infer the type automatically
- To add one element: `arrayList.add(“”):` will place the element at the first available position, for empty list `array[0] = “”;` is analog
- If we want to delete an element in arraylist we just do `arrayList.delete(INDEX or OBJECT”)`, for normal array we can only do array[1] = null;` still maintaining the same size
- Some methods available
- `arrayList.indexOf(“someString”);`
- `arrayList.contains(“someString”);`
- `arrayList.get(0);`
- `arrayList.set(1, “someString”);`
- `arrayList.size();`
- `arrayList.clear();`


# 📅 25.09.2022 java: methods: Why do we use methods in Java?
- Methods are discrete units of code, help you to break up large programs in manageable and reusable chunks and helps you to abstract away logic (e.g. complicated formula)
- Method invocation = One method transfers control to some other method by calling it. Original method has to wait till the second is finished.

# 📅 25.09.2022 java: methods: Why do we have parameters in methods?
- Scope: A method can’t access variables from the calling context, therefore you need to pass variables through the method
- Variable is declared in the method header
- By this methods become very powerful: They are reusable by passing in different input parameters

# 📅 25.09.2022 java: methods: What does it mean if we have pass-by-value semantics for method parameters?
- All values you put are copied for the local scope of the function
- reference types are also copied over by value, the address of the object. You now manipulate the same underlying object since it is still the same reference

# 📅 25.09.2022 java: methods: What happens if you pass in an array to a method?
- In the case of an array, which is also a reference type, the array reference is passed by value

# 📅 25.09.2022 java: methods: How do we return values from a method?
- Once the end of the method is reached it automatically returns to the caller, you can also manually trigger it by writing `return;` but this is not needed
- If you put `return` before the end you get an error because you have defined code afterwards
- Behind a condition this can be quite useful in the form of a guard clause
  Instead of just returning from a method we can also return with a value

# 📅 25.09.2022 java: methods: What is the difference between method and functions?
- Function is a piece of code with a name and can accept parameters (needs to be explicitly passed in) and return something (would be a static function in Java). Sometimes also called class method since the function is associated with a class
- Method is a piece of code which is always associated with an object and can access the object (would be non-static in Java)

# 📅 25.09.2022 java: methods: How can you pass an unknown number of arguments to a function?
- Possible with varargs and useful if you have to to deal with an indeterminate number of objects
- famous example is `String.format()` or `System.out.printf()`
- or another example:
``` java
  private void printAll(Object... msg) {
      for (Object item : msg){
System.out.println(item);
      }
  }
```

# 📅 25.09.2022 java: methods: recursion: How does recursion work?
- Recursion in the end simulates loops and vice versa.
- The state is just passed down to the next iteration by encoding some state in the method parameters. The execution condition of a loop can be compared with the base condition of a method
- recursion also allows to branch of in several recursion trees which is much harder to project into simple loops

# 📅 25.09.2022 java: methods: recursion: Why can method recursion potentially trigger a stackoverflow?
- Stackoverflow in simple words
- If one method calls the other which calls the first one - the calls are stuck in an infinite loop
- But whenever a method is called it gets added to a area of memory called the stack which is at some point full and the program crashes
- Stackoverflow slightly more complicated
- when a method is called stack frame will be put on top (holding all the locally scoped vars and code itself) and is removed from the stack once the method returns
- if program does not terminate it stacks up infinite number of local variables and function definitions without removing because there all methods are waiting for the previous one to return
- to circumvent this there is also the approach of tail-recursive

# 📅 25.09.2022 java: oop: basics: What are objects and classes and how are they connected to reference types?
- Objects/instances are created from classes, class serves as a blueprint which you can create several objects/instances
- Create a objects based on a class has the type of that class e.g. `Thing thing = new Thing();` → if we define a new class we also define a new type (reference type)




# 📅 18.10.2022 Clojure: Access javascript objects from clojurescript
- `(.-body js/document)`: For attributes
- `(.toString js/document)`: For functions
- `(.. js/document -location -href -length)`: For nested attributes


# 📅 18.10.2022 Mac: Shortcut for emoji dialog
- `Strg` + `Command` + `Space`

# 📅 28.09.2022 python: Spin-Up local server for serving files

-   useful if you want to link local files in a Google Doc document
-   currently Google Doc only allows http/https protocol and not brower based local file like `file:///`

``` {.bash}
cd path/to/files
python3 -m http.server 8000
```

-   this results in localhost links like `http://0.0.0.0:8000/some.pdf`
-   for pdf\'s you can also link to a specific page like `http://0.0.0.0:8000/some.pdf#page=5`


# 📅 24.09.2022 java: datatypes: strings: How does String pooling work?
- String is a reference type and object always lies on the heap
- A string either lies on the common heap or in the string pool (special section of heap)
- When initializing with String literal it checks if the object already exists in String pool, if not it creates a new one in that pool
- A string literal is not just syntax sugar for `new String ("")`!
- When initializing with `new` then a new object in the general area of the heap and is created without checking for the String pool
- See also this image here: [source](https://s1.o7planning.com/en/10217/images/20233.png)


# 📅 24.09.2022 java: datatypes: strings: How should you care about the intern() method when it comes to String pooling?
- One might think, I do not really think about String poolings because I just should not use the explicit String constructor and only use String literals to initialize Strings
- that is not true, see here
```java
String value1 = "70";
Integer someInt = 70;
String value2 = someInt.toString(); // created without string pooling
assertFalse(value2 == value1);
assertTrue(value2.intern() == value1);
```

# 📅 24.09.2022 java: datatypes: strings: Why do certain unicode characters do not work in Java?
        - The compiler interprets unicode literals very early in the process and for instance in the case of the linefeed/newline character it would interpret the character in the source code itself
- char hello = `\u000a`; // does not compile but the escaped char analogon does compile: `\n`

# 📅 24.09.2022 java: loops: For what are loops good for?
- Enables you to repeat sections of code in your program

# 📅 24.09.2022 java: loops: Which convention to follow for a for-loop condition?
- `i < n` or `i <= n-1` in loop-condition?
- First version cleaner: usually everyone knows that index starts at 0, so array[n] people know is creating a out-of-bound
- Second version is extra work (although compile usually produces same bytecode)
- Second one is good if you want to iterate only to a specific boundary and that boundary is inclusive

# 📅 24.09.2022 java: loops: For what to use the break and the continue keyword in loops?
- `break`: causes the program to jump out of the loop
- `continue`: causes the program to only skip the current iteration


# 📅 24.09.2022 java: loops: When do you use which loop?
- while-loop
    - Almost  like a if-statement replace `if` with `while`
    - Instead the program continues after the end of the if-construct and will jump back up to the top. Will run the body again till the condition is false
    - If-condition is always true it is called an infinite loop and will be going as fast  as your CPU allows. Show CPU usage which will increase quite a bit
    - How to break this loop, by introducing a variable which acts as a counter. Show increment/decrement operator `i++/i--` and `i += 1`;
- For - loop
    - A more compact version of the while loop with incrementing variable
    - While loop only holds the condition, but for loop holds condition (2),  variable (1) and incrementation (3)
    - Differences
    - increment is only happening after the body was run once
    - counter variable can only be used within the for-loop
- Do while loop
    - Same as while loop but condition is checked last rather then first
    - Need a semicolon at the end
- forEach loop
    - If you really just want to access elements of an array and you don’t need the index it makes code simpler to read

# 📅 24.09.2022 java: arrays: What are good metaphors for multidimensional arrays?
- A two dimensional array can be thought of a table with rows and columns
- A three dimensional array can be thought of a table whereas each cell has a book with pages
- A n-dimensional array can also be described as a nested folder structure and the actual elements are the files
- In short: Multidimensional arrays, are arrays inside arrays

# 📅 24.09.2022 java: arrays: What are some helper methods to work with arrays?
- `Arrays.fill(array,2)`
- `Arrays.binarySearch`
- `Arrays.asList()`

# 📅 24.09.2022 java: arrays: Where should you put the [] - after type or after variable name?
- `String[] args` (more common, Java Standard)
- `String args[]`
- there are also other arguments in combination with generics where this can cause problems with the latter version (can’t find source)

# 📅 24.09.2022 java: arrays: What are arrays and why to use them?
- A variable up to now can only hold value at a time like `int firstElement; int secondElement`
- Arrays can store multiple values at once `int[] array = {1, 2, 4};`
- Each element can be identified by an index number

# 📅 24.09.2022 java: arrays: What are the steps to array creation?
- 1. Declare array with `int[] arr;`
- 2. Create array = `arr = new int[10];` //initialized with default values,0
- 3. Initialize with specific values via assignment `arr[0]=3;`
- For creation and initialization there is a shortcut called ‘array initializer’
- `int[] arr = {1, 2, 3};`
  - This only works when declared at the same time
  - To overwrite existing array use new keyword


# 📅 24.09.2022 Fun: If the client does not pay for a website

-   [link to repo](https://github.com/kleampa/not-paid)

# 📅 23.09.2022 Workshop: Game-Retrospective

-   Create a game board with fields (with special actions)
-   Members get a dice and move along the board one by one
-   the winner facilitates the next retro
-   Possible actions
    -   Give one college positive feedback
    -   Say something which went Good/Bad in this iteration
    -   Name a topic and everyone in their round has to give his opinion to this topic
    -   Give a suggestion what to improve next iteration. If the majority likes the idea you are allowed to throw a dice again
    -   Propose a topic/challenge and facilitate a small discussion for the next n minutes

# 📅 22.09.2022 intellij: Pass to pass VM options to run configuration

-   `Edit Configuration` \> `Modify Options` \> `Add VM Options`
-   Example entry for setting a system property: `-Dfail_on_exception=true`

# 📅 21.09.2022 junit: Run test classes from one accumulating classes, sharing common annotations

-   Use this approach only if you want to share annotations in one class
-   `@BeforeEach`, `@AfterEach`, `@ExtendWith` are all also applied to the nested ones

``` {.java}
@SomeAnnotation //it depends on the implementation of the annotation if that annotation will be passed down to the nested classes, otherwise you can also annotate the nested class
public class SuperTest {

    @Nested // class will be executed as TestClass
    public class ChildATestRun extends ChildATest {}

    @Nested
    @DisplayName("If you split by scenario you can put the scenario here")
    public class ChildBTestRun extends ChildBTest {}
}

// Single Test classes are abstract so that they are not run twice by junit
public abstract ChildATest {}
```

# 📅 21.09.2022 Gradle: Pass system property to gradle task

-   Retrieve system property from calling side and pass it to executing jvm: `systemProperty "myvariable", System.getProperty("myvariable")`

# 📅 19.09.2022 Java: `@Inherited` annotation

-   Meta annotation which tells compiler that annotated annotation will be inherited to child classes
-   this is only valid for classes, on methods it is ignored.


# 📅 18.09.2022 java: control-flow: What are the boolean operators in Java?
- `||` evaluates as the logical true: at least one has to be true
- `&&` evaluates as logical and: both have to be true. If first was is false, does not check the second one
- they are called Short circuit operators: JVM only checks one part before moving to the next one (see also Short-circuit evaluation)

# 📅 18.09.2022 java: control-flow: What are some clean code guidelines for boolean expressions?
- Example: `if(isAgeOver70 || (isAgeOver18 && hasVipPass))`
- Keep single boolean values first
- When there are boolean values which are a logical unit, put `()` around it

# 📅 18.09.2022 java: control-flow: What does the modern switch expression since Java 14 look like?
- you can also use the yield keyword if having a multiline statement
  #+BEGIN_SRC Java
  DayOfWeek day = DayOfWeek.FRIDAY;

int numOfLetters = switch (day)
{
case MONDAY, FRIDAY, SUNDAY -> 6;
case TUESDAY                -> 7;
case THURSDAY, SATURDAY     -> 8;
case WEDNESDAY              -> 9;
};
#+END_SRC

# 📅 18.09.2022 java: datatypes: strings: How are String represented in Java?
        -  As immutable char array (!= final since you can also not modify single entries)
        -  `new String(char[])` - you are essentially telling the compiler to autobox a String object around your array of characters

# 📅 18.09.2022 java: datatypes: strings: What is a char and how does it relate to a unicode and code points?
- Unicode is a mapping between code points (integers) and single graphemes: letter, digit, punctuation mark, whitespace, control characters
- Why do we need a mapping anyway: computer thinks in numbers (it has to know what to paint to the screen, ideally you want that your painted letter looks the same on someone else's computer -> that is why you have a standart)
- In java a char is stored in 16 bit integer type and allows to represent the normal set of Unicode: Basic Multilingual Plane (BMP), in hex: U+0000 to U+FFFF
- Different ways how you can initialize a char in Java:
```java
// code point
char char1 = 65;
// char literal
char char2 = 'A';
// unicode literal
char char3 = '\u0041'; // hex digits need to be padded
// hex int
char char4 = 0x41;
System.out.printf("%c,%c,%c,%c%n", char1, char2, char3, char4);
```

# 📅 18.09.2022 java: datatypes: strings: What are the subsets and supersets of unicode?
- Superset: There is also a an extension to Unicode called supplementary characters (U+FFFF - U+10FFFF) which can’t be stored anymore in a 16 bit char, requiring to use a `int` datatype
- Subsets of unicode are
  - ASCII: 128 code points
  - ASCII extended: 256 code points
# 📅 18.09.2022 java: datatypes: strings: How does Java deal with the fact that the encoding for String is UTF-16 but extensions of Unicode do not fit in 16 bit anymore?
        - when single character just model it with int
        - the methods of object wrapper allow for checking this: `Character.isLetter(0x2F81A)` returns true whereas `Character.isLetter('\uD840')` because it does not fit in char literal
        - in String you can only use chars, the solution is to represent a >16 bit char with a pair of high-surrogates and low surrogates. Even though a single char would not be recognized as letter (see above) you can check for pairs with `Character.isSurrogate` and `Character.isSurrogatePair`

# 📅 18.09.2022 java: datatypes: strings: Why can you add an integer to a char?
- First of all, characters are also number types, precisely a 2 byte, unsigned integer number
- 📝Explain what happens when you remove the brackets.
  ```java
      System.out.println('A'+('B'+ "C")); // ABC
      System.out.println('A'+'B'+ "C"); // 131C
  ```
- The way how the `+` operator works, it always uses int when char,byte,short, int are the only operands (see JLS §5.6.2: Binary Numeric Promotion). The char is implicitly casted to an integer type (widening conversion), Proof:
- 📝Explain what happens here.
  ```java
      System.out.println('A'+ 1); // 66 because result is still widened, int
  ```
- To retrieve a char we need to explicitly cast/assign it back to a char
- 📝Explain what happens here.
  ```java
      // does not compile without cast (narrowing conversion)
      int i = 1;
      char char1 = (char) ('A' + i);
      // this also works without cast because the compiler is clever enough to figure out the literals: JLS §5.2 Assignment Conversion: Narrowing conversions of constant expressions are allowed
      char char2 = 'A' + 1;
  ```

# 📅 18.09.2022 java: datatypes: strings: Why do we obtain an int when adding to char’s?
- Binary numeric promotion happens
- if operand is of type double, the other is converted to double
- if either operand is of type float, the other is converted to float
- if either operand is of type long, the other is converted to long
- Otherwise, both operands (e.g. chars, shorts, or bytes) are converted to type int
- Affected operators: / , %, ,+ , -, <, <=, >,  >=, == ,!=,  &, ^
- source: [source](https://docs.oracle.com/javase/specs/jls/se7/html/jls-5.html#jls-5.6.2)

# 📅 18.09.2022 java: datatypes: strings: What are some useful applications for realizing that chars are just integers?
- If you want to know where letter Y lies in the alphabet: `int position = ‘Y’ - ‘A’`

# 📅 18.09.2022 java: datatypes: strings: Why should you use a StringBuilder when concating a string a lot of times?
- everytime you create a concat something to a string it creates a new object on the heap
- StringBuilder is implemented similar as an arrayList dynamically resizing, allowing also to manipulate characters in between without needing to allocate a new data structure
- always prefer StringBuilder over StringBuffer (latter is slower but guarantees thread-safety)

# 📅 18.09.2022 java: datatypes: strings: Why is StringBuilder implemented as an array and not a linked list?
- Array super fast because continuous block (append, random access etc.). Even when it comes to insertion of the middle of the string, a linked list still needs to iterate to the middle of the list.

# 📅 18.09.2022 What is the difference between binary and text files?
- Everything in memory or written to a file is represented in bytes (4 bit)
  When reading from a file we retrieve a continuous stream of bytes:
- Text stream := stream on bytes which has some markers and conventions to be converted to a text encoding
- Binary stream := a stream of bytes without any convention, you really need the knowledge how the information was encoded by the program in order to recover the information
- Further reading: [source](https://www.nayuki.io/page/what-are-binary-and-text-files)

# 📅 18.09.2022 java: datatypes: strings: How to format a String in Java? What comes closest to string interpolation?

``` java
String.format(“We have %d cats”, 7) // digit
String.format(“We have %.3f cats”, 7.1111) // float with precision -> 7.111
String.format(“We have 1 %.3s”, “dogs”) // precision also works with strings -> “dog”
String.format(“We have %d%% cats”, 7) // digit and escape % -> 7% cats
String.format(“We have %d cats”, 7) // digit
String.format("%tD%n", dateOfBirth); // date
String.format("%S%n",var1); prints String in uppercase letters 
String.format("%S%n",var1); prints String in uppercase letters 
String.format(“%h”, new String(“”)); //prints the hash code
// other examples
// %n -> newline: you should always use that one and not \n
// %b -> boolean
// %c -> character
// %tA -> “sunday” (can do time and date)
```

# 📅 18.09.2022 java: datatypes: strings: How to format output in Java?
- Instead of doing
``` java
System.out.println(String.format(“We have %d cats”, 7));  
```
- You can do
``` java
System.out.format(“We have %d cats%n”, 7); 
System.out.printf(“We have %d cats%n”, 7); 
```


# 📅 17.09.2022 java: operators: What types of operators exist?
- Arithmetic Operators
- Unary Operators
- Assignment Operator
- Relational Operators
- Logical Operators
- Ternary Operator
- Bitwise Operators
- Shift Operators

# 📅 17.09.2022 java: operators: What can you do with the modulo operator?
- Gives you the remainder of the division (“Teilen mit Rest”), so not the main part but just the remainder

# 📅 17.09.2022 java: operators: What is the difference between post/pre-in/decrement operators?
        - called unary operators because they only need one operand
- Post-increment operator: var++: Calculation and assignment happens before execution of next line
- Pre-increment operator: --var: Calculation and assignment happens instantly
- In short:  int x = 0; int z = ++x; //z=1; (x++//z=2;)
- In short: int incMe =0; print(incMe++);//0 print(++incMe) //2

# 📅 17.09.2022 java: operators: What are bitwise operators?
- Work on integers by manipulation the binary representation
- Operations: OR (|), AND (&), XOR (^), Complement (`)
- You can also combine it with assignment operator e.g.  a &= b;

# 📅 17.09.2022 java: operators: What are shift operators?
- Shifting all bits to the left/right
- Unsigned shift, is padded with zeros (only right shift exists)

# 📅 17.09.2022 java: operators: What are some use cases for bitwise and shift operators?
- Encode boolean array in integer e.g. set boolean on 7nth position to true
-  `a |= (1 << 7);`
- source: [source](https://www.geeksforgeeks.org/bit-manipulation-technique-to-replace-boolean-arrays-of-fixed-size-less-than-64/)
- Toggle a boolean to true with xor assignment operator
- theBoolean ^= true;
- Decrease and increase or a number by 50% with bitshift
- theInteger >> 1 and theInteger << 1 and
- all of those tricks usually are not needed, hard to read or done by the compiler anyway

# 📅 17.09.2022 java: operators: Which operators are overloaded in Java?
- Overloaded `+` and `+=` is working differently for Strings and numeral types
- `*`,`/` and `%` are overloaded for integer and double types
- Java does not allow you to do custom defined operator overloading (only with some compiler extensions)

# 📅 17.09.2022 java: control-flow: What do we understand under control flow and what are the basic elements of it?
- Control flow is the order statements are executed in, it is like the path the program takes through the code
- For example: If statements, switch statements and ternary operator

# 📅 17.09.2022 java: control-flow: What is the basic idea of if-statements?
- `If` statement evaluates a boolean as condition
- With `else` you can frame it as a either-or situation
- Can also add `else if` block but only one block will run of the overall `if-else` construct: as soon as the program finds one which is true it will skip all the others

# 📅 17.09.2022 java: control-flow: What is the basic idea of switch-statements?
- `switch` statement is based on cases and you do not need to write a equals/== condition each time
- `default` acts as `else`
- Removing `break` allows to go through several cases (if condition matches)
- there is also a newer version which allows for assigning to a variable


# 📅 12.09.2022 Gradle: Define custom gradle source sets

-   `src/main/java` and `src/test/java` are assumed default source directories
-   to create custom source sets:

``` {.groovy}
// define custom source set
sourceSets{
    minion {
        java {
            srcDirs("src/minion")
        }
    }
}

// define dependencies only used for that source set
dependencies {
    minionImplementation('com.google.guava:guava:29.0-jre')
}

// if you want to run tetss on specific source set
task runMinionTest(type: Test) {
    description = "Run integration tests"
    group = "verification" // task will associated with that folder
    useJUnitPlatform() // Discover and execute JUnit Platform-based tests
    testClassesDirs = sourceSets.minion.output.classesDirs
    classpath = sourceSets.minion.runtimeClasspath
}

// if you want to inherit dependency declarations from different
configurations {
    minionImplementation.extendsFrom(testImplementation)
}

// if you need the compiled classes from one sourcset (here main) in another source set
sourceSets{
    minion {
        compileClasspath += sourceSets.main.output
        runtimeClasspath += sourceSets.main.output
    }
}

```

-   For more information on configuring test task see here [here](https://docs.gradle.org/current/javadoc/org/gradle/api/tasks/testing/Test.html)

# 📅 11.09.2022 java: datatypes: wrapper: Why is it called Integer and not Int?
- Because classes naming convention favors no abbreviations
- same goes for char/Character

# 📅 11.09.2022 java: datatypes: wrapper: What are the issues of primitive object wrappers?
- `Integer integerInstance = null; (5 == integerInstance)` results in null pointer exception when trying to unbox it. Primitives either need to be initialized or have a default value and can be never null

# 📅 11.09.2022 java: datatypes: overflow: What happens when a primitive variable is overflowing?
- Overflow-Metaphor: Datatypes are like cups, you spill in water, overflows
- exceeding the range results in integer-wraparound (see also, signed bits, binary, two complements)
- 📝Exercise:  Show what happens if int is overflowing. Compare this behavior with BigDecimal.

```java
int value = Integer.MAX_VALUE-1;
for(int i = 0; i < 4; i++, value++) {
System.out.println(value);
}
// Use BigInteger in comparison (only restricted by memory of jvm)
BigInteger largeValue = new BigInteger(Integer.MAX_VALUE + "");
for(int i = 0; i < 4; i++) {
System.out.println(largeValue);
largeValue = largeValue.add(BigInteger.ONE);
}
```
- Overflow for double types remain at Double.MAX_VALUE if you add 1 (due to fixed number of significant bits) or if we do `MAX *2` to `Double.POSITIVE_INFINITY`

# 📅 11.09.2022 java: datatypes: overflow: What happens when a double type underflows?
- Usually does either return to negative number range exceeded or decimal places exceeded
- underflow for double types results in Zero
- 📝Exercise:  Show what happens if double is underflowing.
```java
for(int i = 1073; i <= 1076; i++) {
    System.out.println("2^" + i + " = " + Math.pow(2, -i));
}
```

# 📅 11.09.2022 java: datatypes: overflow: How to decide which datatype to use?
- small numbers you know how they behave: int
- always use double for decimal, but for currency use BigDecimal

# 📅 11.09.2022 java: datatypes: overflow: How does the compiler deal with leading zeros of a binary literal?
- For example you can have something like `byte data = 0b0000110011;`
- because for the compiler it is just an int literal which happens to fit into byte even if byte itself does not have that many binary places

# 📅 11.09.2022 java: datatypes: numbers: Why are calculations with double types often inaccurate?
- Reason 1: Some numbers require an infinite number of decimals to be repeated like π.
- in math real numbers are continuous, computers intrinsically know discrete math (0's and 1's)  e.g. 2π*r will always rendered and calculated as discrete points
- Reason 2: Numbers like 0.1 are only approximations because of the way how floats are stored in binary: [source](https://en.wikipedia.org/wiki/Binary_number#Fractions)
- when doing calculations, you also need to round at some point

# 📅 11.09.2022 java: datatypes: numbers: How are floats represented in binary?
- source [source](https://introcs.cs.princeton.edu/java/91float)
- floats are represented in binary (32 bit), accumulating 2^32 real numbers. But of course not all, since there is infinite (even between 0-1)
- 1 bit for sign of number, some bits for exponent (float 8, double 11), and some bits (float 23, double 52) for the mantisse
- Example: 123.45 = 12345 (mantisse) × 10^−2 (exponent)
- usually the mantisse is normalized to be between 0.5 - 1. That fraction is represented also in a binary
- Example for a binary fraction: 0.1101 represents 1/2 + 1/4 + 1/16 = 13/16 = 0.8125
- but it is not possible to represent 0.1 in binary only to approximate it with 0.09999 (you can only work with 1/(2^n) fractions to approximate that number. Approximation depends on the resolution, bits available for the mantisse

# 📅 11.09.2022 java: datatypes: numbers: What is the difference between precision and accuracy?
- Example: Approximation of π := 3.133333333 has a precision of 10 decimal digits but accuracy of only 2

# 📅 11.09.2022 java: datatypes: numbers: What are some important rules when doing floating point arithmetics?
- When comparing floats always compare them with a certain delta (unless you can be sure that they are multiples of exact representations e.g. 1/4)
- In general, always prefer double over float (better accuracy), memory/speed won't be crucial most of the time
- When working with currency, always use BigDecimal (you can control precision)
- 1 != 0.1+0.1.. : Rounding errors, all depends on the precision. Try using BigDecimal if this resolves the issue?

# 📅 11.09.2022 java: datatypes: numbers: How do arithmetic operators 'decide' which datatype to use?
- In general: Always results in a data type which represents the datatype of the widest operand
- but integer types (char, short, int) are always widened to default numeral type, int
- this also means if you do ‘c’ + 12 it always happens this: ((int) ‘c’) + 12 (not course not if you concat with string, overloaded)
- double/int ->double
- if you do int var1 = (int) double/int; you lose that widening of course and result will be truncated

# 📅 10.09.2022 mac: Repeat keys on long-press

-   `defaults write -g ApplePressAndHoldEnabled -bool false`

# 📅 10.09.2022 mac: Custom keyboard layout with Ukulele

-   `New from current Input source ...` to load current keyboard map
-   Edit with right click, `Edit key` and specifiy output and modifier
-   Move file into `/Library/Keyboard Layouts/`, restart and select layout under keyboard preferences
-   IntelliJ: If you want to use the option modifier key you need to select `Keymap` -\> `IntelliJ Idea Classic` (and not mac)

# 📅 10.09.2022 java: datatypes: numbers: For what do you use the hexadecimal system?
- base 16: Using: 0 - 9, A - F
- presenting Unicode/ASCII characters, RGB colors (#  symbol): #66_92_E3 (r,g,b), MAC addresses, assembly, memory addresses

# 📅 10.09.2022 java: datatypes: numbers: Why do we use hexadecimal representation if we know the decimal?
- Because you can nicely represent e.g. 8 bit byte with two hex digits ranging from 00 - FF.
- So for example: 5A means 5:101, A:10(base 10):1010 -> 1011010. In short it is easier to represent large numbers, maps conveniently to binary, and if you need to flip a bit, at max four bits need to change (maybe),  keeping it human readable

# 📅 10.09.2022 java: datatypes: numbers: How to convert between binary, hex and octal in Java?
- You do not really convert between the both because they are just different representations of the same thing. When you want to show them as a string you need conversion though because default is always decimal when printing.
- To convert to String representation e.g.  `Integer::toHexString(int num)`
- To parse e.g. hex string into int `Integer.parseInt("0xAB", 16)`

# 📅 10.09.2022 java: datatypes: casting: What is an implicit typecast?
- Implicit typecast := When one data type is widened to another datatype
- Only happens if conversion is without data loss. (from int to -> long)
- also called Widening Casting,  Automatic Type Conversion
- also happens if you have cast to objects more up in the hierarchy (Child -> Parent)

# 📅 10.09.2022 java: datatypes: casting: What is an explicit typecast?
- Explicit typecast := Explicitly specify that conversion should be done and potentially losing data
- e.g. `double a = 1.1; int b = (int) a;` will remove decimal part
- in other words, chop of if data type can hold less
- Narrowing Casting, Need Explicit Conversion
- also needed if you want to move down into class hierarchy (Parent -> Child)

# 📅 10.09.2022 java: datatypes: casting: Can you also cast booleans?
- Not from integers: Java can't represent false as 0 or null and can't represent true as non-zero
- But convert from String
- returns boxed primitive: `Boolean.valueOf(“TrUe”);`, is case-insensitive
- returns primitive: `Boolean.parseBoolean("true")`

# 📅 10.09.2022 java: datatypes: wrapper: Why do we have object wrapper for primitives?
- Consistent API e.g. toString(), convenient methods (in the spirit of OO, encapsulated)
- We can only provide Object as a generic type, or more general: Polymorphism
- We can have static util methods associated to it's type

# 📅 10.09.2022 java: datatypes: wrapper: What is understood under auto/unboxing?
- Convert primitive types back and forth to their object wrapper classes e.g. int -> Integer

# 📅 10.09.2022 java: datatypes: wrapper: When does auto/unboxing happen?
- Assignment of literal to object wrapper: e.g. here Character ch = 'a';
- Passing as a parameter: ints to a ArrayList<Integer> it does not crash at runtime because at compile time it actually does this: list.add(Integer.valueOf(i))
- Different example: i % 2 -> compile time: i.intValue() % 2)

# 📅 10.09.2022 java: datatypes: wrapper: Can you do a widening conversion and autoboxing in the same assignment?
- Example:
- `Long var1 = 12;` // does not compile
- `long var2 = 12;` // compiles
- `Long var3 = 12L;` // compiles
- According to JLS §5.2 Assignment Conversion, only one conversion is allowed at the time, except if the conversion is a narrowing conversion of a constant expression
- `Short var1= 12;`
- This is the case because you do not have literals of bytes or shorts, only of int. If you want to make this possible: `byte b = 0b0;` and not force the user to do this `byte b = (byte) 0;` you have to allow implicit narrowing conversion for literals


# 📅 08.09.2022 github: Exclude filenames from search

-   for instance if you want to exlude the actual implementation source (which many people fork) and want to see how that piece of code is used
-   `-filename:composer.json`

# 📅 08.09.2022 cs: Shannon Entropy

-   [source](https://www.quantamagazine.org/how-claude-shannons-concept-of-entropy-quantifies-information-20220906/)
-   if you want to store/communicate for instance a series of random coin flips you need a lot of information because the series does not follow a inherit structure: What is the amount of information needed to accurately transmit the message?
-   general rule: the more information you can predict about the message the more information you need
    -   2x coin-flip with coin of two heads -\> zero information needed
    -   2x coin-clip with normal coin -\> 2 bits of information needed (just guessing is 25% probability you get it right)
-   that threshold of the minimum bits needed to resolve ambiguity entirely is called Shannon Entropy, below that threshold the likelihood increased that message will be corrupted
-   Shannon Entropy can be framed as number of yes-no questions needed to resolve the contents of a message (think of Akinator, see also [Twenty Questions algorithm](https://en.wikipedia.org/wiki/Twenty_questions))
    -   the more uncertainty about e.g. weather for the next days is the more questions you need to ask to get all right (e.g. is every day sunny vs is mon,tue,.. sunny?)
    -   for english words you need less questions about the characters because language follows certain probabilities (e.g. frequency of vowels), but for an entirely random string you need to cycle through all characters for each character you want to guess. Implication: Humans comunicate a lot with relatively little information (better with chinese)
-   also used to detect secrets in code (see secret detection), but also information compression
-   for example when compressing a video pixels and how they change to the next frame also allow for pattern prediction (similar to language patterns)

# 📅 08.09.2022 Team: Tech Health Check The following questions can be answered or voted on with 3 degrees on satisfaction

-   How is the experience of building your service?
-   How is the experience of testing your service?
-   How is the experience of deploying your service?
-   How is the experience of operating your service?
-   Health of Codebase?

# 📅 08.09.2022 Java: Using testcontainer

-   call docker container from Java
-   You can either use a ready-made dependency which wraps test container logic around the container or do it yourself to not having to use a generic container (e.g. not good if you want to bind certain methods to a custom type when e.g. mocking this out as a dependency)
-   can also be bound to test lifecycle e.g. `@Container` restarts the container for each test
-   How to introduce a custom testcontainer type which receives commands

``` {.java}
import org.testcontainers.containers.GenericContainer;
import org.testcontainers.containers.wait.strategy.Wait;
import org.testcontainers.utility.MountableFile;

public class MyCustomContainer extends GenericContainer<MyCustomContainer> {
    private MyCustomContainer() {
        // docker image (complete url required!)
        super("registry.hub.docker.com/IMAGE:latest");
        // inject envs
        withEnv(Map.of("ENV1", "val1"));
        // hack for keep running the container
        withCommand("tail -F anything");
        // timing when the container is ready for receiving commands
        waitingFor(Wait.forLogMessage(".*tail.*", 1));
        // avoid having the container restart (if you also set testcontainers.reuse.enable=true)
        withReuse(true);
    }

    private int executeCommands(String... command) throws IOException, InterruptedException {
        final ExecResult execResult = super.execInContainer(command);
        System.err.format("Stdout of %s = %s", Arrays.toString(command), execResult.getStdout());
        System.err.format("Stderr of %s = %s", Arrays.toString(command), execResult.getStderr());
        return execResult.getExitCode();
    }

    // Some example how to copy files into container
    public void copyFiles() throws IOException, InterruptedException {
        copyFileToContainer(MountableFile.forHostPath(new File("someFile.txt").getParent()), "somePathInContainer");
        setWorkingDirectory("/tmp");
    }
}
```

# 📅 08.09.2022 Java: Parsing cli args with commons-cli

-   allows for several identical flags `./tool --flag1 arg1 --flag2 args2`
-   allows for required params
-   allows for help output

``` {.java}
import org.apache.commons.cli.*;

Options options = new Options();
options.addOption(Option.builder("FLAG1")
    .required()
    .longOpt("flag1")
    .desc("Some description")
    .hasArg() // is not a boolean value
    .build());

CommandLineParser parser = new DefaultParser();
CommandLine cmd;
try {
    cmd = parser.parse(options, args);
    // retrieve argument/boolean of first passed flag1
    cmd.getOptionValue("FLAG1");
    // retrieve args of all flags e.g. --flag2 arg1 --flag2 arg2
    cmd.getOptionValues("FLAG2");
} catch (ParseException e) {
    e.printStackTrace();
    System.exit(1);
}
```

# 📅 07.09.2022 InfoSec: Secret dectection

-   many of the reported incidents are usually due to checking in hard-coded secrets into code
-   How does it work? Tools commonly look for
    -   typical filenames and format conventions like `secret.json` or `Bearer XZS`
    -   looking for high entropy strings
        -   how is is it to describe the characters in less characters, hard to predict character distribution
        -   Example `aaaaaaabbbbbbbcccccc` vs `doasolkasnvpa`
        -   see more in [Entropy (information theory)](https://en.wikipedia.org/wiki/Entropy_(information_theory))
-   Two ways of doing secret detection
    -   Preventive: Prevent from uploading secret
        -   detect secrets as part of a git hook
        -   for git hook there is frameworks like [pre-commit](https://pre-commit.com/) which allow you managing different git hooks (for instance running linter check before commit)
    -   Detection
        -   check also in the pipeline (scan repo for secret)
        -   also services which do OSINT to check if a secret for yours was exposed like [keynuker](https://github.com/tleyden/keynuker) which automatically destroys found aws keys
-   tools for secret detection
    -   [talisman](https://github.com/thoughtworks/talisman)
    -   [whispers](https://github.com/Skyscanner/whispers)
    -   [trufflehog](https://github.com/trufflesecurity/trufflehog)
    -   [trivy](https://github.com/aquasecurity/trivy)

# 📅 07.09.2022 Java: Handle blank strings in System.out.format with conditional prefix (hacky/bad idea)

-   **!!** This also works with strings you want to print out, because i̱s interpreted only then
-   Use this when you need to construct a string with optional fields which also influence previous characters

``` {.java}
import org.apache.commons.lang3.StringUtils;
// will end up deleting + when timezone is blank 
System.out.format("12:12:22+%s", StringUtils.defaultIfBlank(timezone, "\b"));

// or use nullable for null params
import static java.util.Optional.ofNullable;
System.out.format("12:12:22+%s", ofNullable(timezone).orElse("\b"));
```

# 📅 04.09.2022 java: datatypes: What datatype is an array?
- "An object is a class instance or an array."

# 📅 04.09.2022 java: datatypes: What are variables, type, declaration, initialization and assignment?
- Very similar to variables in mathematics - writing it like `x = 10; ` is almost valid Java but we need to define what type it is
- `=` called assignment operator, assigns the value on the right to the variable of the left
- A variable first gets declared (so Java knows what type it is) and then initialized (which creates the actual data type with its value)
-  Initialization is the first assignment to a variable, afterwards assignment is a synonym for replacing with new value

# 📅 04.09.2022 java: datatypes: numbers: What is a bad joke regarding integers?
- "Isn't this int-eresting?"

# 📅 04.09.2022 java: datatypes: numbers:  What are integer types and double types?
- Integer is another word for whole numbers, also sometime called integral, means that its spectrum is discrete and the smallest difference between any two distinct values is 1
- integer types, but are different range
- byte (8 bits): -128 … 127
- short (2 bytes): -32,768 .. 32,767
- int (4 bytes): -2,147,483,648 .. 2,147,483,647
- long (8 bytes): -9,223,372,036,854,775,808 .. 9,223,372,036,854,775,807
- Double types
  - double types try to approximate the real numbers (which is a infinite set) with discrete set of units
- float: varies in precision (single-precision (6-7 decimal digits))
- double: varies in precision (double-precision (15-16 decimal digits)


# 📅 04.09.2022 java: datatypes: numbers:  What does it mean that the char is an integer/integral type?
- Chars are just small integers, precisely a 4 byte, unsigned integer number which also happen to map to a unicode symbol
- You can also do this: `char char1 = 0b1111_1111_1000_0111;`

# 📅 04.09.2022 java: datatypes: numbers: What is the default datatype for integer literals?
- `int`, that is why the compiler complains if you want to assign a long without the `L`: e.g. `2147483648L`
- you can also not do this: `Long x = 250;`, because this would need require two conversions (widening conversion int to long and autoboxing to Long), which is not allowed by spec

# 📅 04.09.2022 java: datatypes: numbers: Can you also use the scientific notation in Java?
- Yes, you can e.g. `1e+3`
- you can also use `_` to e.g. triple group large numbers (for for visual separation)
- for hexadecimal numbers you use p instead of e (since e is a hexadecimal digit)


# 📅 04.09.2022 java: datatypes: numbers: How do positive and negative Zero behave in Java?
source: [source](https://www.baeldung.com/java-overflow-underflow)
- has the following ‘wired’ behavior

``` java
double a = +0f;
double b = -0f;
assertTrue(a == b);
assertTrue(1/a == Double.POSITIVE_INFINITY);
assertTrue(1/b == Double.NEGATIVE_INFINITY);
```

# 📅 04.09.2022 java: datatypes: numbers: Why can double data types result in NaN?
- Math.sqrt(-3.0) (floats represent real and not complex numbers!) - test with Double.isNaN()
- Also if you divide by zero. Follows the convention that arithmetic  operations do not throw an exception

# 📅 04.09.2022 java: datatypes: numbers: What numeral representations are supported in Java?
- decimal (base 10): 7
- binary (base 2): 0b101
- hexadecimal (base 16)
- 0xAB, octal (base 8): 01

# 📅 04.09.2022 java: datatypes: numbers: Can you also have bin, hex, octa numbers on other number types than int?
- Yes and no
- Yes, you can assign those to all integer types, including char
- But also no because you are still using an int literal and Java does a narrowing conversion to char, short, byte… (see JLS §5.2 Assignment Conversion)
- For numbers bigger than int you need to mark with e.g. with `0x..12L`, because the compiler interprets the literal as int first before doing the widening conversion

# 📅 04.09.2022 java: datatypes: numbers: Why does a computer use a binary system but not a decimal system?
- Computer runs using millions of electronic switches (transistors), representing either on or off
- Those two states we can represent mathematically as binary numbers 0,1
- Same goes for a hard drive
- magnetic particles with a north or south direction
- both states are corresponding to 0,1
- the reader detects the directions and translates this to a byte stream and the writer reorients particles according to the byte stream input

# 📅 04.09.2022 java: datatypes: numbers: What are bytes and bits?
- binary system: the language of computers, base 2 (translates to Boolean logic, electric switch). "voltage applied" and "no voltage"
- 1 byte  == 8 bits
- Each bit (standing for binary digit) is a binary digit of 0 or 1
- Highest number is 127 which can be represented by 1 byte: 0100_0000, the leading bit is reserved for the sign (unsigned 1 byte could hold 255)

# 📅 04.09.2022 java: datatypes: numbers: Why are the numeral systems for decimal, hexadecimal etc. called “base” 10,16?
- Because the available bit representations are calculated with base^#digits  e.g. 2^8 for a byte

# 📅 04.09.2022 java: datatypes: numbers: How are negative numbers represented in binary?
- Signed Magnitude Method: first bit position is reserved for sign(0 -> + and 1 -> -)
- 2’s Complement: Invert all bits from the positive and then add one (used in Java)

# 📅 04.09.2022 java: datatypes: numbers: For what octal is the representation good?
- base 8 (good for describing power of 2 e.g. 2^3 (base 10) == 10 (base 8)



# 📅 03.09.2022 InfoSec: Security by obscurity

-   Concept of breaking standards to make it more difficult for an malicious user/hacker/bot to enter a system
-   Examples
    -   Use different port for ssh
    -   Change admin login url of CMS
    -   Next to user agent also check for tls handshake e.g. you can fingerprint curl with this - see [here](https://daniel.haxx.se/blog/2022/09/02/curls-tls-fingerprint/)
-   This strategy is usually only good for keeping unsophisticated bots out. But even they can [fusk](https://en.m.wikipedia.org/wiki/Fusker), crawl, brute force a lot of those mitigations

# 📅 03.09.2022 vim: Delete everything from cursor to the beginning of the line
- `d0`

# 📅 03.09.2022 java: platform: What is a JDK and SDK in Java?
- Java SE JDK or Java SDK usually contains everything you need: compiler, interpreter, documentation, debugger, disassembler

# 📅 03.09.2022 java: platform: What are the steps a Java code goes through to run on a maschine?
- javac (compiler): (1) Converts Java code into bytecode and does processing of annotations. Here a lot of language specifications are checked type and syntax checks and first optimizations
- java (bytecode interpreter): (2) Runs .class files by starting runtime environment (JRE) and execution of specific main method and interprets this to maschine native code

# 📅 03.09.2022 java: platform: What is the difference between JVM and JRE?
- Java runtime environment (JRE) is Platform specific implementation of Java virtual Machine (JVM)
- e.g. Oracle implementation of JVM is written in C
- there is many implementations etc e.g. GraalVM
- JRE (in addition of the JVM implementation) also contains core libraries and often a JIT compiler
- JRE does not contain bytecode compiler and other development tools which makes it  a lot smaller than the JDK’s

# 📅 03.09.2022 java: platform: Why does every Java .class file start with the magic bytes C0FEBABE?
- magic number is for identifying the class file format (e.g. for JPEG it is FFD8)
- origin trivia is is explained here: [source](https://news.ycombinator.com/item?id=33049423)
- You can check this with `xxd` SomeClass.java in the CLI

# 📅 03.09.2022 java: platform: What does a just-in-time (JIT) compiler do?
- compiles bytecode to native machine code at runtime when possible or when there is time
    - the rest is just interpreted normally from the JVM
    - if there native code (provided by JIT) available the JVM would take that piece of code instead
    - since time and memory is limited which us need by JIT to do its work the method calls to be optimized by keeping track of the numbers of calls and only is threshold is check it is attempted to optimize with JIT compiler (see also hot method)
    - that is the reason why a program gets faster over time
- if a method is called even more times, the JIT compiler tries to optimize the method even more (several levels of optimizations)


# 📅 03.09.2022 java: platform: How do you package a program with source code?
- Java Archive (JAR) := Compile Java classes to class files and point to class of main entrypoint in the manifest file. If you want to look at the original Java class file you need some decompiler

# 📅 03.09.2022 java: platform: How to check the current vm?
- `System.out.println(VM.current().details());`

# 📅 03.09.2022 java: platform: What is the difference between heap and stack?
- JVM divides memory (RAM) in those two areas
- Stack
    - static memory allocation
    - primitives values of local scope of method
    - reference values in local scope but still pointing to heap
    - last-in-first-out principle (LIFO)
    - all variables/data to one method is stored in one block and put on to the stack (stack frame)
    - stack frame is flushed if method returns
    - Access to this memory is very fast (compared to heap)
    - thread safe because each thread has own stack
    - if full: stack overflow exception
- Heap
    - for objects, references still stay on stack
    - if no space left: OOM exception
    - not thread-safe
    - Strings are objects and therefore in the heap

# 📅 03.09.2022 java: platform: How can threads access stack and heap?
- heap is global access and all threads can access it
- thread local area is a special area of the heap where each thread has can store objects which are not accessible by other threads
- stack is bound to a specific thread (private scope)

# 📅 03.09.2022 java: platform: What is the lifetime of stack and heap?
- stack: once something in thread finishes execution like return when method   stackframe is removed
- heap: Garbage collector takes care of it (only if no ref is pointing to it)

# 📅 03.09.2022 java: platform: Can I skip all the bytecode intermediates and compile directly to native code?
- Yes, you can do this with e.g. with GraalVm’s native image described here: [source](https://www.graalvm.org/native-image/)

# 📅 03.09.2022 java: platform: Where to get the source of truth regarding Java spec?
- Java Language Specification (JLS)
- VM specs (easier to read): [source](https://docs.oracle.com/javase/specs/index.html)

# 📅 03.09.2022 java: datatypes: What are the two different data types in Java?
- Primitive types
  - Primitive types are assigned by value e.g. `int a = 1; int b = a;`
  - simply put: How much space we set aside in memory to store the data we want to store
- if you tell it to use an int the Java program reserves a certain amount of bits/cells to store that information, independent of the actual value within the range
- Reference types (pointing to object (instance of class or array structure // always combination of primitive types))
  - is just some number in hex representation to give you the address of the object (remote control metaphor)
  - in other words: It is merely a pointer pointing to a address in location where the actual elements lie e.g. `int[] a = {1,2}; int[] b = a;` where is `a,b` are just a reference to the same array `{1,2}`
- Everything initialized with ` new` is a reference type (and String literals)
- Reference types also hold if you pass a reference to a method



# 📅 02.09.2022 Testing: Testing beforehand vs Improved observability

-   Sometimes things are very hard to test
-   If the potential failure scenarios are not too severe you can also opt for putting metrics in place alerting if something is off
-   For example infrastructure code you often do not unit test but try to alert when certain configuration is wrong (service not available, open ports etc.)

# 📅 02.09.2022 Ruby: Monkey patching

-   Monkey patching := Dynamically modify classes/modules/attributes at runtime, allowing for instance to replace methods with side effects in a test
-   Usually only scripting languages allow this (like Ruby/Python)
-   Often used for patching a bug from a third party lib

# 📅 01.09.2022 Docker: Override entrypoint with interactive shell on container start

-   `docker run -it --entrypoint /bin/bash IMAGE`

# 📅 01.09.2022 Git: Switch to previous branch

-   `git switch -`

# 📅 31.08.2022 Docker: Use alpine image with bash

-   Add this to `Dockerfile`: `RUN apk update && apk add bash`

# 📅 31.08.2022 Gradle: Zip/Tar

-   you can use [tarTree](https://docs.gradle.org/current/dsl/org.gradle.api.Project.html#org.gradle.api.Project:tarTree(java.lang.Object)) and [zipTree](https://docs.gradle.org/current/javadoc/org/gradle/api/Project.html#zipTree-java.lang.Object)

# 📅 31.08.2022 Gradle: Exposed standard paths

-   `$buildDir`: where the build folder is generated
-   `src/config.xml`: relative path only from where `build.gradle` is located

# 📅 29.08.2022 Fun: Random fun commit messages

-   [whatthecommit](http://whatthecommit.com/)

# 📅 29.08.2022 Git: Clone from branch directly

-   `git clone --branch <branch> <url>`

# 📅 27.08.2022 Fun: Sleep sort

-   find a numerical representation of each entry and spawn a separate thread for each entry only printing the result after the specified time
-   [source](https://rosettacode.org/wiki/Sorting_algorithms/Sleep_sort)

# 📅 27.08.2022 InfoSec: Web beacon

-   Web beacon:= describes several techniques to determine if someone has visited a website, read a Email or accessed certain content
-   Most simple approach: Embedded Image in email and verify in asset server logs if asset was accessed
    -   this is as initially even a non-visible picture, containing a single pixel (\"tracking pixel\")
-   Be careful which Email you forward because this can be detected by the mechanism described above
-   Minimal information which always can be acquired
    -   IP
    -   Access time
    -   client/browser agent
-   Phishing/Spammer groups also use this to check if certain email are still actively used and if a Mail goes through a spam filter
-   To circumvent such trackers
    -   configure client to not download Assets in emails
    -   Use mail filters (see milter) and configure mail transfer agents (MTA)

# 📅 19.08.2022 java: Thread-Safety and how to achieve it

-   Java has this out of the box, running several worker threads in JVM
-   thread-safety := Different thread can access the same ressource without conflict like simultaneous updates etc.
-   Different approaches to ensure thread-safety
    -   Avoid shared state for instance in a method scoped calculation
    -   Immutable objects (state can\'t be changed after construction and therefore not shared)
    -   🚧 Add others, see TODO\'s

# 📅 18.08.2022 mac: How keys map to windows keys

-   Command (or Cmd) `⌘` : Windows logo key
-   Option `⌥` : Same as `Alt`
-   Control `⌃`: Same as `Ctrl`
-   Shift `⇧`: analogous
-   Caps Lock `⇪`: analogous
-   `Fn`: analogous

# 📅 18.08.2022 mac: Paste without formatting

-   `⌘` + `⌥` + `⇧` + `V` : Paste without formatting

# 📅 14.08.2022 android: How to make file transfer work

-   if device is not found, go to `Developer options` -\> `Default USB configuration` (not found via search!) -\> `File Transfer`

# 📅 14.08.2022 InfoSec: Smartphone as a single point of failure

-   [source](https://news.ycombinator.com/item?id=32396685)
-   Nowdays everything goes over 2FA, if you loos your phone or is stolen you potentially lock out yourself out of a lot of services, requiring a lot of effort to recover all accounts
-   Instead of using Google Authenticator for generating Soft token TOTP\'s you can use solutions like [authy](https://authy.com/)
    -   supports multiple devices at once
    -   you can also use your laptop as device
    -   has encrypted backups (cloud option)
-   Time-based One-time Password (TOTP) := Standardized algorithm using a shared secret approach. Both sides share a time-synced secret which have to match
    -   usually valid for 60 seconds
-   One-time password (OTP) := Server sends out one-time password via E-Mail/SMS.
-   More about pros/cons of TOTP/OTP can be read [here](https://www.transmitsecurity.com/blog/totp-the-good-the-bad-and-the-ugly)

# 📅 12.08.2022 intellij: Why are annotations like `@Override` evaluated while editing?

-   IntelliJ is generating a (unified) abstract syntax tree (AST/UAST) called Program Structure Interface (PSI) while you type
-   Syntax errors are generated by iterating over the PSI tree and check with some language specific grammars for errors, see [here](https://plugins.jetbrains.com/docs/intellij/syntax-errors.html)
-   in the case of the `Override` annotation a custom logic in IntelliJ is implemented to verify if this method actually fufills all the requirements e.g. if the method exists in the parent class [checkOverrideEquivalentInheritedMethods](https://github.com/JetBrains/intellij-community/blob/9306a30b5cda48535edc70af1a2a1a37ac6ef3df/java/java-analysis-impl/src/com/intellij/codeInsight/daemon/impl/analysis/HighlightMethodUtil.java#L1548) but also `checkStaticMethodOverride`, `checkMethodIncompatibleThrows`, `checkSuperMethodIsFinal`
-   it is important to note that it is not continously compiling but just update the AST, in contrast for example to Eclipse which does something like continous compilation which achieves the same
-   With the PSI tree you can do a lot of things out of the box when you want to write your own plugins e.g. finding overwritten methods [here](https://plugins.jetbrains.com/docs/intellij/psi-cookbook.html) for a super method
-   Lombok for instance is using a lot of annotation post processing capabilities, instead of generating code based on code only at compile time you can utilize a plugin for IntelliJ which integrates with the PSI and dynamically generate required sources based on the annotations you provide (not needing to wait for compiling source first)

# 📅 11.08.2022 psychology: Visualizations of common work psychology

-   Credits go to [@alexmaesej](https://www.instagram.com/alexmaesej)
-   Growth mindset and working on a annoying problem:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/attitude.png" /></p>

-   Pairing and wanting to resolve a problem before finishing the day:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/focus.png" /></p>

-   Working with a new technology:

<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/starting_a_task.png" /></p>

-   Doing TIL\'s:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/consistency.png" /></p>

-   Reflecting about growth and technical journey in general:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/not_giving_up.png" /></p>

-   Doing TIL\'s:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/discipline.png" /></p>

-   Splitting sub tasks of story to not get overwhelmed:
<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/psychology/one_step_at_a_time.png" /></p>

# 📅 10.08.2022 Fun: Where does the name git come from?

-   Torvalds the creator of `git` stated: \"I\'m an egotistical bastard, and I name all my projects after myself. First \'Linux\', now \'git\'.\"
-   `git` means unpleasant person in British English slang
-   man pages describes Git as \"the stupid content tracker\"

# 📅 10.08.2022 Fun: Where does the term logging come from?

-   comes from \"logbook\", which originates from how pirates used to measure the speed of their boat and then write their values into their logbook
-   how did they measure the speed?
    -   1.  Throw log over boat attached to a rope with knots as distance markers

    -   1.  Now count the knots over time and therefore termine the speed

    -   1.  Write it into your logbook

# 📅 09.08.2022 Maven: How to pass in environment variables or system properties in cli

``` {.bash}
# for system property
mvn test -DSYSTEM_PROPERTY="PROPERTY_VALUE" 
# for env var
ENV="VALUE mvn test
```

# 📅 05.08.2022 Java: How to pass in environment variables as annotation parameter?

-   in short, you can\'t generate values dynamically to pass into a annotation because the annotations are evaluated at compile time (baked into the `.class` file)
-   but you can defer evaluation to runtime, this really depends on the implementation of the annotation
-   for instance when you want to pass in an environment variable there is (e.g. for spring) the following convention

``` {.Java}
@Annotation(param="${ENV_VAR:DEFAUlT_VALUE}")
public class SomeClass(){}
```

-   a value resolver is then running during runtime, calling (in this case) `System.getenv(String)`

# 📅 05.08.2022 Fun: Online games to play within the team

-   [garticphone](https://garticphone.com/)
-   [codenames](https://codenames.game/)

# 📅 03.08.2022 consulting: Pyramid principle

-   helps to prioritize contents when you having limited time
-   Steps
    -   \(1\) put core message first and declare it as such
    -   \(2\) what is arguments supporting the core message?
    -   \(3\) what information/details support those arguments?
-   usually the other way round - conclusive approach: facts first - conclusion last
-   when to use:
    -   good for factual topics (very good for management discussions)
-   when not to use:
    -   not very good for educational or emotional topics
    -   you ommit explanations
    -   does not convey emotional value, just objective facts
    -   example: marriage proposal
        -   do not start with we should marry and then give some facts for it
        -   better to do some build up, and get emotional stories around it
-   techniques
    -   clear core message, no vague intentions: what do you really want to achieve?
    -   leave out details which do not support core message
    -   story of the slides should be understandable just by the titles
    -   every slide has only one topic, if not split

# 📅 03.08.2022 vim: Better word navigation with `e`

-   instead of `w` also consider using `e` which jumps to the end of each word
-   if you want to cut the end of a word instead of `dt<whitespace>` use `de` (delete beginning of word `db`)

# 📅 03.08.2022 vim: Replacement mode

-   `R`: Enters replace mode (leave with `ESC`)

# 📅 02.08.2022 microservice: Types of monoliths

-   Single Process Monolith := Code is deployed in a single process. In some sense distributed because it talks e.g. with a database.
-   Modular Monolith := Consists of modules where it can be independently worked on but still requires one overall deployment.
-   Distributed Monolith := Different service but need to be deployed together. Usually occurs when the information hiding principle was not applied.

# 📅 02.08.2022 microservice: Advantage of monoliths

-   Often simpler developer workflows, monitoring and trouble shooting
-   Often e2e testing is simpler
-   Code reuse is easier
-   Fast changing domain

# 📅 01.08.2022 queues: Why to use Avro vs JSON for the event format?

-   (+) optional specification for the event including versioning (public documentation)
-   (+) more space-efficient (e.g. uses pointers to field descriptors, therefore not repeated)
-   (+) direct mapping to json format
-   (-) binary format
-   other option to Avro is Protobuf

# 📅 01.08.2022 InfoSec: Types of Application Security Testing (AST)

-   [source](https://www.hackedu.com/blog/sast-vs-dast-vs-iast)
-   The general idea of shifting security left
    -   shifting security left: lot of parallels to the left shift concept of testing
        -   e.g. in the traditional testing approach you had the QA wall of confusion at the very end of delivery, and in InfoSec you have like two weeks before going life some onboarding of some internal InfoSec specialist or doing some external pen testing -- both approaches produce a lot of overhead because information is lost in the way and quality or security is not baked in
    -   bake in security in our QA process, not even before it, we want to think of security during refinement, or run a *security objectives workshop* right at the inception phase
    -   Secure coding practices and code reviews are **not** enough need for automation --\> new emerging field of DevSecOps
    -   Read more of shifting security to left and different tools helping with that [here](https://www.aquasec.com/cloud-native-academy/devsecops/shift-left-devops/)
-   Static Application Security Testing (SAST)
    -   Whitebox approach, looking at the code
    -   Like a code review but a lot faster
    -   Rules are modifiable and can include
        -   input validation errors, path traversals, injections, race conditions
    -   Detects early in the software dev lifecycle
    -   Pinpoints to the exact location of the code
    -   Can't detect logical vulnerabilities e.g. access control issues
    -   Especially large codebase: false positives (needs expertise to decide on reports)
-   Dynamic Application Security Testing (DAST)
    -   Blackbox approach
    -   Like automated pen testing
    -   Checks things a SAST might miss out on
        -   Checking against running web application, also target infrastructure (webserver, databases, proxies)
        -   including logical vulnerabilities
        -   technology independent
    -   Usually follows the three phases of pentesting (Explore, Exploit, Report)
    -   Drawbacks
        -   Can't identify logical issues
        -   Can't pinpoint spot in code (blackbox approach)
        -   Might corrupt test data
-   Interactive Application Security Testing (IAST)
    -   Combination of SAST and DAST
    -   Best of two worlds: Example
        -   Candidate for SQL injection
        -   Payload is sent
        -   Monitoring confirms if this worked out
    -   And checking for publicly available vulnerabilities
    -   Active IAST, monitoring + attack scenarios
    -   Passive IAST, only monitoring
    -   Fewer false positives
    -   Drawback: Very tedious to setup since it tightly integrates with the application/infrastructure (e.g. setting up the security sensors)
-   Runtime Application Self-Protection (RASP)
    -   Like a guardian angel
    -   sense an attack happening (diagnostic mode) and implement necessary measures (protection mode)
        -   Can block individual requests (like WAF)
        -   Virtually patch a vulnerability to prevent further attack
    -   monitor the inputs, outputs, and internal state
    -   Does not do extensive scans but monitors passively in prod (IAST only during testing phase)
    -   zero-day protection
-   read more about pros/cons of SAST/DAST tools [here](https://owasp.org/wwwcommunity/Free_for_Open_Source_Application_Security_Tools)
-   read more about different criteria when it comes to choosing a AST tool [here](http://projects.webappsec.org/w/page/66094278/Static%20Analysis%20Technologies%20Evaluation%20Criteria)
-   Some options
    -   SAST
        -   Free: Semgrep
        -   Paid: SonarQube
    -   DAST
        -   Free: OWASP ZAP
        -   Paid: Burp Suite
    -   IAST
        -   Contrast Assess

# 📅 01.08.2022 InfoSec: Pentesting 101

-   Usually split up in three phases
-   1.) Explore e.g. Crawl pages, find different entry points, OSINT, software/patches installed, hidden contents
-   2.) Attack -- exploit vulnerabilities in order to prove that they exist
    -   Check for common vulnerabilities
        -   SQL Injections
        -   XSS
        -   LFI
        -   SSRF
    -   Check for authentication issues, memory leaks, session issues, and weak ciphers
-   3.) Report
    -   Result including
        -   URL
        -   attack vector
        -   Complexity of exploit
        -   vulnerability type
        -   Severity

# 📅 29.7.2022 Clojure: Learnings about instaparse

-   a parse library where you just need to define a context-free grammar
-   when you want to match a certain rule, but hide it in the output you can wrap `<>` around

``` {.Clojure}
;; - a matching rule:
'<(>' A* '<)>' ;; -> parens won't be part of group
;; - around a definition:
<BulletMarker> = <'+' | '*' | '-'> ;; -> won't be part of the syntax tree, just helper for the grammar (refered as Hiding tags)
```

-   Do comments with `(* Unordered lists *)`

# 📅 29.07.2022 hikari: Connection pool datasource

-   Important parameters
    -   `maximum-pool-size`: Defines number of allowed connection to datasource, connections will be reused
        -   `minimum-idle`: Defines the number of connections which will be established right away, even though they are not needed (defaults to `maximum-pool-size`)
-   [see documentation](https://github.com/brettwooldridge/HikariCP)

# 📅 29.07.2022 IntelliJ: Refactor current selection/scope

-   `CRTL` + `ALT` + `SHIFT` + `T`: `Refactor this ...`

# 📅 29.07.2022 Workshop: Find out reasons for a check-in over several dimensions

-   **1. Step:** Voting on several dimensions with a gradient (e.g. Fun `(--1--, --2--, --3--)`)
-   **2. Step:** You could span a two-dimensional field where you allow votees to also arrange reasons for their voting on that voting matrix: Fun `(--1-(sticky1)-, --2--, --3-(sticky2)-)`
-   **3. Step:** Votees can vote again on the dimension for further discussion

# 📅 29.07.2022 Fun: Agile Rhapsody

-   One of the more famous agiles songs - [link](https://www.youtube.com/watch?v=MCwJfETgiVo)

# 📅 29.07.2022 InfoSec: CIS benchmarks

-   Center for Internet Security (CIS) := Non-Profit to establish global guidelines for good security standards.
-   CIS benchmarks := benchmark can be used to help an organization build a set of security policies and processes to protect data and assets for a certain technology.
    -   benchmarks available for cloud platforms (like gcp, aws, azure etc.)
-   Tools which are also checking for CIS benchmarks: gcp security control center, snyk, prisma cloud

# 📅 22.07.2022 InfoSec: Injection vulnerabilities

-   Local File Inclusion (LFI) := Web application loads up files on the file system that should not be available
    -   Change `http://example.com/file.php?file=main_page.php` to `http://example.com/file.php?file=../../../etc/passwd`
-   Remote File Inclusion (RFI) := Web application loads up remote files which should not be available
-   Server-side request forgery (SSRF) := Make web application a request which is under the hackers control
    -   Example: Accessing Cloud metadata e.g. `hxxp://metadata.google.internal/computeMetadata/v1/project/project-id` of the running VM
-   SSRF vs LFI/RFI
    -   LFI/RFI is usually a consequence of a SSRF
    -   SSRF is the more general concept and is not bound to a specific file
-   Cross Site Script Inclusion (XSS) := Malicious script in the generated html, whereas backend is only vector but client in frontend is target

# 📅 21.07.2022 Clojure: Print to stderr

``` {.Clojure}
(.println *err* (str "uha!"))
```

# 📅 21.07.2022 Git: Show last stashes

-   `git stash list`: Show last stashes

# 📅 21.07.2022 Team: PowerPoint Karaoke

-   candidate has to present a deck of slides about a topic he never has seen before
-   there is a whole [community](https://de.wikipedia.org/wiki/Powerpoint-Karaoke) around it with tournaments etc.

# 📅 21.07.2022 InfoSec: PII vs PHI

-   Personally Identifiable Information (PII) := Information that can be used to deferr someones identity.
    -   Leakage of PII can lead to \"issues like personal embarrassment, workplace discrimination, and identity theft\"
-   Protected Health Information (PHI) := Health related information that has individual identifiers (PII) associated to it.
    -   \"violation of these can lead to severe legal consequences\"
    -   can lead to embarrassment, financial harm, potential discrimination based on health-issues

# 📅 20.07.2022 Unix: Using grep recursively and for specific file type

-   `grep -r --include "*.txt" <patterm> .`: Search through folders recursively including extension filter

# 📅 20.07.2022 Java: Source-level annotation Processing

-   Annotation Processing := process of generating code at compile time to handle the annotations
-   Allows you to generate additional source files at compilation stage
-   compiler searches for annotations, and matches a annotation processor
-   the annotation processors will then generate source files
-   those source files are scanned again for annotations, cycle is repeated till no new files are generated
-   tutorial how to build custom processing is [here](https://www.baeldung.com/java-annotation-processing-builder)

# 📅 20.07.2022 Java: Do semantic comparision/assertion on two different DTOs with assertj

``` {.Java}
import static org.assertj.core.api.Assertions.assertThat;

assertThat(actual).usingRecursiveComparison()
                .ignoringFields("fieldA", "fieldB", // fields only present in actual or different values
                                "fieldC", "fieldC"  // fields only present in expected or different values
                ) .isEqualTo(expected);
```

# 📅 20.07.2022 Java: MapStruct Basics

-   Learnings and comments (source: [here](https://www.baeldung.com/mapstruct))
    -   generates mapper classes at compile time (see `build/generated/sources/annotationProcessor`)
        -   that\'s why it is [super fast compared to other solutions](https://www.baeldung.com/java-performance-mapping-frameworks#1averagetime)
    -   in-depth documentation [here](https://mapstruct.org/documentation/stable/reference/html/)
    -   out-of-the-box implicit type conversions (e.g. String -\> Date), therefore it is better to explicitly define a mapping method and use a `qualifiedByName` (see below)
    -   when fields are identical (name and hierachy) they are automatically mapped (no `@Mapping` needed)
    -   `@BeforeMapping~/~@AfterMapping` allows to post/pre-process the mapped object, useful e.g. if you want to do some invariant checks (see more [here](https://mapstruct.org/documentation/dev/api/org/mapstruct/AfterMapping.html))
    -   You can provide a default value if to be mapped value is null `@Mapping(defaultExpression ="java(java.util.UUID.randomUUID().toString())")`
-   Define Mapper

``` {.Java}
import org.mapstruct.Mapper;

@Mapper
public interface TargetClassMapper {
    // [1] field in source needs to reference method parameter sourceClass
    @Mapping(source = "sourceClass.fieldA", target = "fieldA")
    TargetClass toTargetClass(SourceClass sourceClass);

    // [2] if type is different provide a conversion method
    default TargetTypeForFieldA convertTypes(final SourceType fieldA) {
        //...
    }

    // [3] if signature is not enough for selecting the right method you can add qualifiers
    // e.g. if you define a String -> String method without qualifier it will overwrite all mappings which contain a String to String mapping
     @Mapping(source = "sourceClass.fieldA", target = "fieldA", qualifiedByName="checkQualifiedNamed")

     @Named("checkQualifiedNamed")
     default TargetTypeForFieldA convertTypes(final SourceType fieldA) {
        //...
    }
}
```

-   all other fields with same name/hierachy will be automatically mapped

```{=html}
<!-- -->
```
-   Use Mapper for example in Spring as Bean

``` {.Java}
import org.mapstruct.factory.Mappers;

@Configuration
public class MapstructConfig {
    @Bean
    public TargetClassMapper targetClassMapper(){
        return Mappers.getMapper(TargetClassMapper.class);
    }
}

// instead of a bean config you can also add the mapper like this
@Mapper(componentModel = "spring")
public interface TargetClassMapper {}
```

-   if you want to see debug output in gradle

``` {.Gradle}
tasks.withType(JavaCompile) {
    options.compilerArgs = [
            '-Amapstruct.verbose=true'
    ]
}
```

-   if you want to fail when target (or source) has unmapped field

``` {.Java}
@Mapper(unmappedTargetPolicy = ReportingPolicy.ERROR)
```

# 📅 20.07.2022 Java: Annotation Theory

-   Annotations can be either interpreted at compile time or at runtime
-   How are annotations e.g. `@Test` related to introspection/reflection? ([source](https://stackoverflow.com/a/1918154))
    -   annotations are `meta-meta objects` describing `meta-objects` (like classes or methods) which themselves describe `objects` (like a instance)
    -   the process of retrieving the metadata of an object at runtime is called *introspection* (see introspection) `anObj.getClass()`
    -   after retrieving the `meta-object` you can also retrieve the annotations `aClass.getAnnotations`

# 📅 20.07.2022 Java: Introspection vs Reflection

-   Reflection := Ability to introspect upon itself and manipulating internal properties of the progam.
    -   e.g. retrieve names of all methods of a class.
-   Introspection := Ability to examine types and properties at runtime
    -   e.g. a instanceOf check at runtime
-   Usually introspection is about testing a state, reflection is about manipulating the state
-   Even though reflection is a very powerful concept it usually comes with a lot of downsides
    -   you tie implementation details to concrete naming (also diffficult to refactor and anticipate side-effects)
    -   performance is bad
    -   read more [here](https://docs.oracle.com/javase/tutorial/reflect/index.html)

# 📅 20.07.2022 Gradle: How to find out the latest version available of your dependency

-   Either use a plugin like [gradle-versions-plugin](https://github.com/ben-manes/gradle-versions-plugin)
-   or check in the gradle file for the dependency repository (`repositories{}`) and look at their website which usually provides a search interface
    -   [Maven Central](https://search.maven.org/)
    -   [Google Maven Repo](https://maven.google.com/)

# 📅 19.07.2022 Gradle: Continuous build

-   Gradle allows to watch for changes and trigger specified task on changes again with
-   `gradle -t <task>`: watch for changes and retrigger task on e.g. file changes
-   you can also use `--continuous` instead of `-t`
-   [source](https://docs.gradle.org/2.5/userguide/continuous_build.html)

# 📅 19.07.2022 Api: On status codes 200 vs 204 (No-Content)

-   When the call was successful but there is no content you can use `204` e.g. used when sending a `PUT` request

# 📅 18.07.2022 InfoSec: False positives in dependency OWASP checker

-   OWASP dependency check is scanning dependencies based on a CVE which is associated with several CPE\'s, that CPE (similiar to a regex) is sometimes not well defined matching dependencies which are not related
-   Common Platform Enumeration (CPE) := A industry standard to define a specific hardware or software component.
    -   `cpe:/o:redhat:enterprise_linux:3:ga:desktop`
-   Common Vulnerabilities and Exposures (CVE) := Publicly known vulnerabilities and exposures, maintained by NFC.
-   Common Weakness Enumerations (CWE) := Categorizes types of software vulnerabilities, looking for the cause.
    -   examples for CWE\'s are for example cross-site scripting, race condition, buffer overflows
    -   in contract CVE\'s looks at the symptoms
    -   CWE\'s themselves are again categorized in the OWASP TOp 10
-   you can check for the exact matching reason on `build/reports/dependency-check-report.html` once you run `gradle dependencyCheckAnalyze`
-   reading [more](https://jeremylong.github.io/DependencyCheck/general/suppression.html) about it and also how to [read the report](https://jeremylong.github.io/DependencyCheck/general/thereport.html)

# 📅 18.07.2022 Chrome: Switch to left/right tab

-   `Ctrl + ⇧Shift +Tab↹`: Switch to left
-   `Ctrl + Tab↹`: Switch to right

# 📅 15.07.2022 Pattern: Why should you not validate on an outgoing request DTO

-   **good idea when**: if you always have the most up-to-date api definition of the provider you send a request to and callouts are expensive. Allowing you to instantly assume that clients returns a Bad Request
-   **bad idea when**: but once calling site has a older version being more restrictive than the up-to-date provider definition, the validation is neither in the interest of the calling site (otherwise you would just validate the incoming request dto or check invariants in code) nor for the provider site
    -   Example: consumer is failing on required field, provider would not because it is now optional
-   **bad idea when** the calling site is a pass-through application (see \'dumb pipelines\')

# 📅 14.07.2022 Java: Manually validate fields of DTO e.g. @NotBlank fields

``` {.Java}
import javax.validation.Validator;
Validator validator = Validation.buildDefaultValidatorFactory().getValidator();
Driver driver = new Driver();
driver.setAge(16);
Set<ConstraintViolation<Driver>> violations = validator.validate(driver);
```

-   see also [here](https://reflectoring.io/bean-validation-with-spring-boot/#validator)

# 📅 13.07.2022 Vim: Format function body

-   `vi}=`

# 📅 12.07.2022 Java: Reading ressource files relative to src folder of class

``` {.Java}
getClass().getResourceAsStream("/file_located_in_ressource_folder.json")
```

-   here it is important that file will be loaded from the target/build folder, so if you do not build your project files won\'t be copied over into the target folder

# 📅 12.07.2022 IntelliJ: How test run configurations work

-   How does IntelliJ ensure that a certain maven/gradle lifecycle is run before the rests are execuuted?
-   For every run configuation usually a build phase is executed before the launch of the actual run
    -   Click on a test class to be executed and run the tests \| Edit Run Configuration \| Modify Options \| Before Lunch \| Add before lunch task
    -   this ensure e.g. that all classes are compiled before a test is executed

# 📅 12.07.2022 IntelliJ: Set breakpoint on exception in debug mode

-   Go to: Run \| View Breakpoints \| Exception Breakpoints (Language specific)

# 📅 12.07.2022 Vim: Prepend newline before pattern match

-   `:%s/\./\0\r/g`: Adds a new line before each `.` in line

# 📅 08.07.2022 Maven: Lifecycle

-   when you run `mvn install` you trigger the following steps (see [lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)):
    -   `process-resources`
    -   `compile`
    -   `process-test-resources`: here all files/folders are copied over from test ressources into target folder `test-classes`
    -   `test-compile`
    -   `test`
    -   `package`
    -   `install`
    -   `deploy`
-   Parameters
    -   `-DskipTests=true`: skips tests
    -   `-U`: forces a check for updated releases and snapshots on remote repositories

# 📅 08.07.2022 Eventual consistency

-   Eventual consistency := Eventually reflecting the same data in a distributed system.
    -   usually fast
-   Strong consistency := Always reflecting the same data in a distributed system.
    -   usually comes at the price of higher latencies
-   Examples
    -   queues: you never now when a message is consumed/ consumer is notified by a updated state
    -   data syncronzation between two db\'s: depends when sync run is
-   In such situations you usually want to have some reconciliation processes in place ensuring that the data is in sync

# 📅 30.06.2022 Consulting: Talking about velocity

-   *Person 1 : Your team is slow.*
-   *Person 2 : Slow, compared to what?*

# 📅 29.06.2022 Windows: Layout if second screen is not next up on top of primary screen

-   in display settings you can simply graphically move the physical location of each screen
-   if you move the secondary monitor on top of the primary you simply need to break through the top margin of the primary screen to get to the secondary one

# 📅 29.06.2022 Windows: Move current window to different screen

-   `Windows + Shift + Left Arrow`

# 📅 28.06.2022 Fun: 36 Methods of Mathematical Proof

-   ([source](http://jwilson.coe.uga.edu/EMT668/EMAT6680.F99/Challen/proof/proof.html))
-   **Proof by obviousness**: \"The proof is so clear that it need not be mentioned.\"
-   **Proof by general agreement**: \"All in favor?...\"
-   **Proof by imagination**: \"Well, we\'ll pretend it\'s true...\"
-   **Proof by convenience**: \"It would be very nice if it were true, so...\"
-   **Proof by necessity**: \"It had better be true, or the entire structure of mathematics would crumble to the ground.\"
-   **Proof by plausibility**: \"It sounds good, so it must be true.\"
-   **Proof by intimidation**: \"Don\'t be stupid; of course it\'s true!\"
-   **Proof by lack of sufficient time**: \"Because of the time constrait, I\'ll leave the proof to you.\"
-   **Proof by postponement**: \"The proof for this is long and arduous, so it is given to you in the appendix.\"
-   **Proof by accident**: \"Hey, what have we here?!\"
-   **Proof by insignificance**: \"Who really cares anyway?\"
-   **Proof by mumbo-jumbo**: Mumbo-Jumbo
-   **Proof by profanity**: (example omitted)
-   **Proof by definition**: \"We define it to be true.\"
-   **Proof by tautology**: \"It\'s true because it\'s true.\"
-   **Proof by plagarism**: \"As we see on page 289,...\"
-   **Proof by lost reference**: \"I know I saw it somewhere....\"
-   **Proof by calculus**: \"This proof requires calculus, so we\'ll skip it.\"
-   **Proof by terror**: When intimidation fails...
-   **Proof by lack of interest**: \"Does anyone really want to see this?\"
-   **Proof by illegibility**: asdasvasd233ef
-   **Proof by logic**: \"If it is on the problem sheet, it must be true!\"
-   **Proof by majority rule**: Only to be used if general agreement is impossible.
-   **Proof by clever variable choice**: \"Let A be the number such that this proof works...\"
-   **Proof by tessellation**: \"This proof is the same as the last.\"
-   **Proof by divine word**: \"...And the Lord said, \'Let it be true,\' and it was true.\"
-   **Proof by stubbornness**: \"I don\'t care what you say- it is true.\"
-   **Proof by simplification**: \"This proof reduced to the statement 1 + 1 = 2.\"
-   **Proof by hasty generalization**: \"Well, it works for 17, so it works for all reals.\"
-   **Proof by deception**: \"Now everyone turn their backs...\"
-   **Proof by supplication**: \"Oh please, let it be true.\"
-   **Proof by poor analogy**: \"Well, it\'s just like...\"
-   **Proof by avoidance**: Limit of proof by postponement as it approaches infinity
-   **Proof by design**: If it\'s not true in today\'s math, invent a new system in which it is.
-   **Proof by authority**: \"Well, Don Knuth says it\'s true, so it must be!\"
-   **Proof by intuition**: \"I have this gut feeling.\"

# 📅 27.06.2022 InfoSec: Risk responses / risk treatments

-   usually part of a risk managment plan (enumerating risks with likelihood)
-   4 classic ways of dealing with risk
    -   **avoid** risk e.g. not building the new feature or cutting of centrifuges inustrial controlls from the internet (stuxnet)
    -   **contain**, reduce impact when it happens e.g. frequent database backup
    -   **mitigate**, close the loopwhole
    -   **accept**, choose to move ahead e.g. do not protect internal tool since it is not exposed to the public internet and there is a low probabiliy to be attacked

# 📅 27.06.2022 InfoSec: How to decide on priority when it comes to brainstorming threats in a Threat Modelling session?

-   Usually, priority = impact \* probability
-   probability is super hard to estimate for average team members because
    -   we are all biased and have trouble evaluating risk
    -   confirmation bias := did we also consider evidence which speaks against our ideas?
    -   optimism bias := causes someone to believe that they themselves are less likely to experience a negative event
-   **better**,
    -   \(1\) guess how invested, elaborate the attack needs to be in order to suceed. Is it reasonable that the attacker goes through that effort?
    -   \(2\) with that information go to the PO/BA\'s and ask what a attacker looks like, and how motivated would they be to achieve a certain goal
-   if the effort is very low (e.g. can be exploited by an automated attack), then probablity is very high e.g. bot scanning for open ports
-   probability can be also phrased as, has this been see in the wild before?

# 📅 27.06.2022 InfoSec: Privacy

-   What is privacy?
    -   Legal definition: e.g. Gdpr
    -   Scientific definition
    -   Social/cultural definition
-   privacy issues only come up if it was not tolerated e.g. revenge porn
-   bossware := software or security design which aims to surveil employees (in non-consensual ways)
-   Datensparksamkeit vs Datenreichtum: the less data you collect, the less you need to protect
    -   is a continuum with decreasing usefulness raw data -\> information context -\> pseudonymized -\> anonymized -\> ereased data
    -   how to find the right balance? Start with strongest protection and loosen over time
-   Perfect privacy := Attacker with perfect background knowledge and unbound compute-power is unable to distinguish anything about an individual, uniformily accross users even in the worst-case scenario
    -   this is never possible, just privacy theory
-   Perfect secrecy := System can never be broken, even with unlimited computing power
-   Homomorphic encryption := Encrypted computation, you can process data without decrypting it
-   Federated computing := Data stays on local devices

# 📅 27.06.2022 InfoSec: How to be a good security champion?

-   Go through Checklists/Assesments
-   What data are we handling?
    -   PII, public, confidential, logs, tokens, secrets
-   Awareness, including to update onboarding docs, incident response plan
-   Do Threat Modelling sessions
-   Set goals for the team
    -   outside expectations? Company policies?
    -   Gaps from previous assessment?

# 📅 24.06.2022 Git: Search through commit messages

-   `git log --grep "message".`

# 📅 24.06.2022 Git: Stash and pop automatically when rebase

-   `git rebase origin/master --autostash`

# 📅 23.06.2022 Gradle: Implicit transparency when providing subtasks

-   When following dependency graph of task is given

``` {.text}
Some generic task A has a direct dependency on taskB and taskD (usually denoted by ~dependsOn~)
    taskA > taskB > taskC
    taskA > taskD
```

-   in order to make sure which of the dependent tasks run first we specify a `mustRunAfter`
-   implicit transparency becomes an issue if for instance we specifiy `tasks.findByName('taskD').mustRunAfter 'taskB'`
    -   the consequences are not intended because it will likely happen that taskD is run before taskC since it is only waiting for taskB
    -   Usually a warning is given by gradle, see [here](https://docs.gradle.org/7.4.2/userguide/validation_problems.html#implicit_dependency)

# 📅 23.06.2022 Gradle: Add replace string in file (hacky)

-   Gradle allows for replacing contents of the files in a copy process
-   we therefore first copy something in a tmp folder, delete the original file and then copy it back

``` {.groovy}
task _introduceChange(type: Copy) {
    from ('src/../') {
        include 'TargetClass.java'
    }
    into 'src/../tmp'
    filter { line -> line.replaceAll('TO_BE_REPLACED', 'REPLACEMENT') }
}

task _rmOrigin(type: Delete) {
    delete 'src/../TargetClass.java'
    followSymlinks = true
}

task _rmTmp(type: Delete) {
    delete 'src/../tmp'
    followSymlinks = true
}

task _copyBack(type: Copy) {
    from ('src/../tmp') {
        include 'TargetClass.java'
    }
    into 'src/../'
}

_introduceChange.finalizedBy _rmOrigin
_rmOrigin.finalizedBy _copyBack
_copyBack.finalizedBy _rmTmp
```

# 📅 23.06.2022 Gradle: Import groovy helpers into gradle script

``` {.groovy}
apply from: 'utils.gradle'
```

# 📅 23.06.2022 Gradle: Define several task dependencies inside a task

``` {.groovy}
task someTask {
    dependsOn build
    dependsOn clean
    tasks.findByName('clean').mustRunAfter 'build'
}
```

# 📅 21.06.2022 Docker Compose: Add container name to reference container from `docker`

``` {.yaml}
version: '3'
services:
  app: # this is the service name, only docker compose knows this
    build: .
    ports: [12345:8990]
    container_name: my-app # this is the container name, also docker can handle this
```

# 📅 20.06.2022 Docker: Hack for entrypoint to keep container running

-   `tail -F anything`: Will never terminate since it is waiting for file \'anything\' to appear

# 📅 20.06.2022 Gradle: Create task, ignoring exit value and print errors

``` {#Gradle Cli task .Bash}
task cliTask(type: Exec) {
    workingDir "${buildDir}"
    ignoreExitValue = true
    def stdout = new ByteArrayOutputStream()
    standardOutput = stdout
    errorOutput = stdout
    commandLine 'echo' 'hey'
    doLast {
        println stdout.toString()
    }
}
```

# 📅 16.06.2022 Workshop: How to plan out a workshop (or retro)

-   \(1\) Think of the different stages of the **process**
    -   Example: 1) Reflect on past 2) extract learnings 3) think of future 4) anticipate based on learnings what might help to make it better
-   \(2\) Think which **metaphors** you want to use in each stage (incl. overarching metaphor)
-   \(3\) Think of which **methologies** you want to use in each step
    -   Example: 1) Small warmup game 2) Brainstorming in group -\> Vote on Top-3 3) Discussion in small groups 4) Quick presentation

# 📅 14.06.2022 Gradle: See how long each build steps takes

``` {.Bash}
gradle --profile
```

-   outputs html

# 📅 14.06.2022 Team: Servant leadership

-   [source](https://asana.com/resources/servant-leadership)
-   Not mission but employee is the main focus
-   TBD: Explain some of the characteritics

<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/servant_leadership.png" /></p>

# 📅 14.06.2022 Git: Revert last n commits in one commit

``` {.Bash}
git revert --no-commit HEAD~3..
git commit -m "Revert of last 3 commits"
```

-   only working if not merge commit present in the commits to be reverted

# 📅 13.06.2022 microservice: Pattern Index from book *Monolith to Microservices* **Splitting the monotlith**

-   Branch by abstraction: Coexisting two implementations of the same functionality in the same codebase at the same time, allowing for a new implementation to be incrementally developed until it can replace the old implementation. (p.104)
-   Decorating collaborator: Trigger functionality running in a separate microservice by sniffing requests sent to the monolith, and the responses that are sent back in return. (p.118)
    -   also can be used without touching the monolith
    -   similiar to stranger fig but original request is still passed down to the monolith
    -   response or request of monolith is extended by a microservice e.g. adding a new field
-   Strangler fig application: Wrap your new microservice architecture around the existing monolith. Calls to use functionality that has ben migrated from the monolith to your microservices are diverted; other calls are left unchanged. (p.79)
    -   intercepting inbound call through proxy (even protocoll can change) or redirect
    -   (+) you do not need to touch the monolith
    -   does not work when calls are inside the monolith and not at the boundary
    -   you can still call back to the monolith if this allows for smaller steps of extraction
-   Parallel run: Run two implementations of the same functionality side by side, to ensure that the new functionality behaves appropriately (p.113)
-   UI composition: Presenting a single user interface by assembling many small parts together (p.89)

**Decomposing the database**

-   Aggregate exposing monolith: Exposing domain aggregates from a monolith to allow microservices to access entities managed by the monolith. (p.138)
-   Change data capture: Transmit changes made to an underlying datastore to other interested parties. (p.120)
    -   usefull when call can\'t be intercepted or when the needed data is not exposed via an api
    -   CDC can be done e.g. with a log-based approach
-   Change data ownership: Moving the source of truth from the monolith to a microservice. (p.141)
-   Database as a Service interface: Using a dedicated database to provide read-only access to internal service data. (p.136)
-   Database view: A view is projected from an underlying database, allowing for parts of the database to be hidden. (p.128)
-   Database wrapping service: A facade service is placed in front of an existing shared database, allowing for services to migrate away from direct use of the database. (p.132)
-   Dedicated reference data schema: A dedicated database to house all static reference data. This database can be accessed by multiple different services. (p.181)
-   Duplicate static reference data: Copy static reference data into microservice databases. (p.179)
-   Monolith as data access layer: Accessing data merged by monolith via APIs rather than directly accessing the database.
-   Move foreign-key to code: Move management and enforcement of foreign-key relationships from a single database up into your service tier. (p.173)
-   Multischema storage: Managing data in different databases, typically while migrating a shared database to a database-per-service model. (p.171)
-   Repository per bounded context: Break apart a single repository layer ariund different parts of the domain, making decomposition into services easier. (p.162)
-   Shared database: A single database shared between more than one service (p.125)
-   Split table: Breaking a table into two parts prior to service decomposition (p.171)
-   Static reference data library: Move static reference data into a library or configuration file that can be packaged with each microservice which needs it (p.182)
-   Static reference data service: A dedicated microservice that provides access to static reference data. (p.184)
-   Synchronize data in application: Syncroniye data between the sources of truth from inside a single application (p.143)
-   Tracer write: Incrementally migrate data from one source to another tolerating two sources during the migration (p.149)

# 📅 13.06.2022 Pattern: \"Keep the pipes dumb, the endpoints smart\" - Martin Fowler

-   dumb pipelines := the transport of messages between two microservices really is not doing nothing as delivering the message (e.g. no eleborate logic (like validations) in proxy, api gateway etc.)
-   smart endpoints: means that all logic (like validations etc.) resides in the microservice behind a endpoint
-   this is the opposite to the concept of Enterprise Service Bus (EBS), which are very smart pipes intercepting calls and taking care of things like security checks, Routing. business flow / validation and transformation
-   What is the motivation behind this?
    -   Higher cohesion, less coupling between components (e.g. change in complicacted proxy might impact a lot of downstream services)
    -   delivery contention (see Sam Newman): a lot of teams modifying the same component

# 📅 10.06.2022 Transparent remoting and location transparency

-   Transparent Remoting: is about making remote calls look like local calls (with proxies forwarding to remote server)
    -   you never know whether the methods are executed locally or the data has been sent over the network to be executed on a remote object
    -   but this is still a cheap illusion since you can not abstract away issues like latency, memory access, partial failure and concurrency
    -   Example: Java Remote Method Invocation (RMI)
-   Location transparency: is about making all calls (including local ones) look like remote calls
    -   so assume that all those networking issues can occur making this transparent right from the start
    -   physical location does not matter only the identifier

# 📅 08.06.2022 wiremock: When you want to mock server response behavior, example for spring rest template

-   [Wiremock](https://wiremock.org/docs/junit-jupiter/)

``` {.Java}
@WireMockTest
class WiremockTest {

    @Test()
    void test(WireMockRuntimeInfo wmRuntimeInf){
        String endpoint = "/someEndpoint";
        stubFor(post(endpoint).willReturn(
              aResponse()
                .withResponseBody(new Body("{}"))
                .withStatus(200)
                .withFixedDelay(2000) //simulates delay if you set timeout in restTemplateBuilder accordingly
                .withHeader("Content-Type", "application/json")));  
        final ResponseEntity<ResponseClass> response = restTemplate.exchange(
                        wmRuntimeInfo.getHttpBaseUrl() + "/" + endpoint,
                        HttpMethod.POST,
                        new HttpEntity<>(request, headers),
                        responseType);
    }
}
```

# 📅 08.06.2022 Mockito: Inject real autowired beans

``` {.Java}
@Spy
private SomeService service = new RealServiceImpl();
@InjectMocks
private Demo demo;
```

-   this becomes especially useful if you do autowire in the depenend class and can\'t inject mocks via the constructor (this sometimes makes sense if you do not want a complicated constructor for child classes)

# 📅 20.05.2022 Workshop: Nobody is perfect

-   Put a question nobody can know the answer to, everyone has to put in a anonymous answers and everyone is voting what is the most realistic answer. The game master is also adding the real answer
-   The most voted answer get points
-   is also a game with the same name (Ravensburger)

# 📅 17.05.2022 JUnit: Assert fields on thrown exception

``` {.Java}
Throwable thrownException = assertThrows(NullPointerException.class, () -> {
    testedMethodThrowingException();
});
assertEquals(thrownException.getCode(), HttpStatus.UNPROCESSABLE_ENTITY.value());
```

# 📅 12.05.2022 Pattern: Port and Adapters aka Hexagonal Architecture

-   [source](https://alistair.cockburn.us/hexagonal-architecture/)
-   **Intent**: You want to be able to run the application independent of \'users, programs, automated test or batch scripts\' and test in isolation from its infrastructure
    -   no leaking business logic into UI layer
    -   easier to test (no mocking required)
    -   easier to move from a UI driven system to a batch-process
-   Shift of mindset: \"Rule to obey is that code pertaining to the \'inside\' part \[of the application\] should not leak into the \'outside\' part.\"
    -   you do not think about your application any more
        -   like incoming request from left to right
        -   layers from top to down
    -   you often have several incoming/outgoing flows, easier to model with inside/outside and clearer to enforce that nothing should leak outside
    -   also read on this [Data on the Outside versus Data on the Inside](http://www.cidrdb.org/cidr2005/papers/P12.pdf)
-   **How**: All outgoing and incoming requests have to go through a port which then converts the information (with an adapter) in a format which is compatible with the technology on each side. That leaves the application completely isolated and pure from it\'s infratstructure or UI
-   Why is it called port?
    -   use the same logic as a port from a OS, any device with a fitting protocol can plugin in
    -   protocol of that port is an API, whereas the adapter converts the API to signals which are needed by the two connecting sides
    -   Example: Database connecting to port needs adapter which either converts signal into SQL, filestream or adapter to a mock-database

# 📅 12.05.2022 Pattern: Application Layering

-   What do we want to achieve with layering?
    -   domain layer should not depend on low-level concerns (aka. dependency inversion)
    -   avoid anemic domain models
    -   high-level folders should denote domain concerns, not technical ones
-   What to watch out for
    -   avoid using modules for seperating out layers: this just creates pain (see also [screaming architecture](https://blog.cleancoder.com/uncle-bob/2011/09/30/Screaming-Architecture.html))

# 📅 12.05.2022 Pattern: Saga-Pattern - Part II

-   Origin from even before microservices: Splitting up long-running transactions (because they were blocking ressources for too long)
-   Type: Orchestration (like command & controll)
    -   state is centralized
    -   typically use syncronous request/response to communicate that transaction was successful (but also event-based is possible)
    -   disadvantage
        -   a lot of coupling with controller (really do not use if you have multiple teams responsible for the microservices)
        -   business logic can leak into controller
-   Type: Choreography (Trust and Verify)
    -   only communictate state as event (relevant services listen to that topic)
    -   disadvantage
        -   difficult to understand whole business process
        -   difficult to see whole state
-   You can also combine both approaches
-   How to handle failures
    -   do not use to resolve technical errors (should only be used for business error)
        -   here should use retries, circuit breakers instead -\> system should be stable before introducing Saga patterns
        -   further reading [here](https://www.ufried.com/blog/limits_of_saga_pattern/)
    -   backward-recovery: revert what happened before
        -   compensating transactions (e.g. remove entry from db)
            -   you sometimes also want to keep track of those compsensations, that they happened
    -   foreward-compensate: just retry and do not compensate for it
-   Alternatives to Saga patterns: Two-Phase commits

# 📅 12.05.2022 Java: Creating custom annotations

-   for class level annotation

``` {.java}
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
public @interface CustomAnnotation {
    //...
}
```

# 📅 12.05.2022 Gradle: Share config between to different tasks

``` {.groovy}
def commonConfig = {
    classpath = sourceSets.main.runtimeClasspath
    jvmArgs "-Xmx1024m", "-XX:MaxPermSize=128m"
}

task runSomething() {
    configure commonConfig
}
```

# 📅 11.05.2022 Gradle: Managing gradle dependencies

-   Get to know which version a dependency has and the decision for it (see Dependency mediation)
    -   `gradle dependencyInsight --dependency package_name`

# 📅 11.05.2022 Workshop: More tech/developer experience orientated healthcheck

-   source is from spotify ([source](https://engineering.atspotify.com/2014/09/squad-health-check-model/))
-   **Support**: Getting support and help when asked for it
-   **Value**: Feeling about what has been delivered so far
-   **Fun**: Excitement about work & working together
-   **Health of Codebase**: Cleanliness, easy to read, test coverage..
-   **Learning**: New vs. old stuff
-   **Mission**: Clear & inspirational
-   **Pawns or Players**: Fate in own hands (decide what to build and how)
-   **Speed**: Development, waiting times, delays
-   **Process**: Ways of working
-   **Teamwork**: Bunch of individuals vs. team.

# 📅 10.05.2022 Mockito: Fundamentals

-   Initalize by

``` {.java}
import static org.mockito.MockitoAnnotations.openMocks;
openMocks(this);
// or by
import static org.mockito.MockitoAnnotations.initMocks;
initMocks(this);
```

-   Use captor for checking which values were passed

``` {.java}
@Captor ArgumentCaptor<OriginalClass> originalInstance;

//later in test
 when(someInstance.do(originalInstance.capture());
 assertEquals(...,originalInstance.getValue());
```

-   You can chain when commands for specifiying mock behavior on first, second, 1+n call

``` {.java}
when(myMock.doTheCall())
   .thenReturn("You failed") //first call
   .thenReturn("Success"); //second call
```

-   How to use verify (more on this [here](https://www.baeldung.com/mockito-verify))

``` {.java}
// test that mock method was called
List<String> mockedList = mock(MyList.class);
mockedList.size();
verify(mockedList, times(1)).size();
// test that no method was called on mock
verifyNoInteractions(mockedList);
```

-   When to stub and when not? Usually don\'t stub pojos

*Usually you want to test your code with real inputs and expected outputs and usually these will be data structures or pojos.* - [source](https://softwareengineering.stackexchange.com/a/363127)

# 📅 09.05.2022 Spring: Get request context to retrieve things like headers globally

-   Each request is served in a single threat which contains the request context
-   If not needed outside of controller, you can obtain headers via `@RequestHeader` annotation

``` {.java}
String retrieveHeaderFromRequest(){
    Optional<RequestAttributes> requestAttributes = Optional.ofNullable(RequestContextHolder.getRequestAttributes());
    if (requestAttributes.isPresent()) {
        String headerField =
            ((ServletRequestAttributes) requestAttributes.get()).getRequest().getHeader("headerName");
        if (headerField != null && !headerField.isEmpty()) {
        return Optional.of(headerField);
        }
    }
    return Optional.empty();
}
```

# 📅 09.05.2022 Spring: Interceptors 101

-   when to use: cross-cutting concerns
-   Spring Rest Templates allows to specify interceptors to modify request before it is sent ([source](https://programmer.group/spring-resttemplate-uses-interceptors-to-configure-http-request-headers.html))

``` {.java}
@Component
public class CustomInterceptor implements ClientHttpRequestInterceptor {
  @Autowired
  CustomCounter counter;

  @Override
  public ClientHttpResponse intercept(HttpRequest request, byte[] body, ClientHttpRequestExecution execution)
      throws IOException {
     // modify header
    HttpHeaders headers = request.getHeaders();
    headers.add("actionId", counter.nextInt());
    // forward request
    return execution.execute(request, body);
  }
}
```

# 📅 06.05.2022 Workshop: City-Retrospective

-   Icebreaker: Which city is best for some certain activities?
    -   List of Cities and symbols to vote on: party, nature, food, bicycle, architecture
-   Check-In: Traffic light, green, red, yellow for safety
-   Brainstorming: Traffic jam? neighborhoods? urban gardening?
-   Action items: Let\'s make our city better

# 📅 03.05.2022 InfoSec: Terms in Security

-   VicSocks := victim sockets, malware opening a socket on victims maschine to use their IP for malicious activity
-   Credential Stuffing := Instead of bruteforcing a system with random credentials a password dump from previous breaches is used
    -   Mitigations
        -   2FA
        -   block IP\'s (but usefull if attacker used e.g. VicSocks)
        -   check against password dumps and request to change passwords
        -   Google Capture

# 📅 28.04.2022 Networking: Firewalls 101

-   on OSI layers 3-4
-   IP, port, access controll list

```{=html}
<!-- -->
```
-   Web Application Firewall (WAF)
    -   on OSI layers layer 5-7
    -   designed to protect against higher level attacks e.g. from OWASP Top 10
        -   for example http flood attack or slowloris
        -   legitimate web requests, not attacking network but application itself
    -   example: http flood atack
        -   it is very difficult to distinguish them from legitimate traffic, eventually resulting in DoS for the real users
        -   a WAF for instance would keep track of malicous IP\'s dynamically and block those once a certain pattern in requests is identified

# 📅 28.04.2022 Networking: OSI Model 101
- OSI := open systems interconnection, is a communication standard between computers
- when OSI layer is used
    - characterizing network issues
    - categorizing cyber threats
- split up in 7 layers
    - Layer 7 (Application): *All the common protocolls like HTTP, FTP, TELNET, SMTP*
    - Layer 6 (Presentation): *Responsible for converting incoming data so that the application understands its content and translating outgoing data so that it conforms to the protocoll standard. This also includes things like encryption, and compression of data*
    - Layer 5 (Session): TBD
    - Layer 4 (Transport): TBD
    - Layer 3 (Network): TBD
    - Layer 2 (Data Link): TBD
    - Layer 1 (Physical): TBD

# 📅 28.04.2022 JUnit: Tags

- helps you to filter for certain annotated tests (include/exclude)
- use `@Tag` on either class or method level
- in Maven Surefire Plugin use
``` {.xml}
<configuration>
        <groups>group3</groups>
</configuration>
```

in mvn use: `mvn test -Dgroups=group3,group2`

# 📅 28.04.2022 Infrastructure: Open Policy Agent (OPA)
-   [source](https://www.openpolicyagent.org/)
-   you define policies and a agent is checking them (compliance)
-   e.g. use terraform plan json output and feed it into agent

# 📅 28.04.2022 QA: Synthetic monitoring
-   a small subset of tests you execute on your prod environment in a regular fashion and create alerts on it
-   sometimes called semantic monitoring
-   can be combined with canary releases
-   **why**: System-wide e2e tests without coupling the deployment of microservices
-   **how**: canary data you sent through the system (but side-effects are avoided)
    -   you would still would want to write all the synthetic data in db but clean up after the test
-   usually quite expensive to implement system-wide
-   [further reading](https://martinfowler.com/bliki/SyntheticMonitoring.html)

# 📅 26.04.2022 QA: Performance tetsing of microservice in isolation vs system-wide tests
-   Benefits of testing system in isolation
    -   see if changes you introduced decrease performance
    -   since you test system in isolation you can benchmark against a baseline (regression-testing)
-   Benefits of doing a system-wide performance test
    -   also see other system restrictions
    -   also discover things like race-conditions
-   It often makes sense to do both but the question how often and when you run those
    -   e.g. running system in isolation you could do on every deploy and system-wide on every release

# 📅 26.04.2022 Maven: Maven Enforcer Plugin
-   like a unit test for maven files
    -   built-in rule: Dependency Convergence
        -   fail if two dependencies A,B depend on a different version of another dependency C
        -   Maven usually falls back to the latest version (see also Dependency mediation)
-   Dependency mediation
    -   Maven/Gradle always has to set for one version otherwise we would get a scope conflict (same class names etc.)

# 📅 26.04.2022 Maven: Multi-Module project
-   Define root and module poms
``` {.xml}
<!-- In root pom -->
<modules>
    <module>core</module>
    <module>service</module>
    <module>webapp</module>
</modules>
<!-- In module pom -->
<parent>
  <artifactId>parent-project</artifactId>
  <groupId>com.baeldung</groupId>
  <version>1.0-SNAPSHOT</version>
</parent>
```
- Dependency Management in Parent Project ([source](https://www.baeldung.com/maven-multi-module))
    - centralizing the dependency information in one place
    - in parent pom you define artifact, groupId and version
    - in inheriting pom only artifact, groupId
    - exclusions are also inherited

# 📅 25.04.2022 Java: Memory management Shown my Native Memory Tracking
- Heap: Java objects
    - globally accessable
- Non-Heap
    - Garbage Collector: GC requires memory for data structures and algorithms to do its job
    - Code Cache: Storage of dynamically generated code
    - Compiler: JIT compiler needs some memory to run
- Metaspace
    - here Class metadata (method bytecodes, symbols, constant pools, annotations) is stored
- Thread stack
    - contain references
    - last-in, first-out (LIFO) memory allocation
    - each thread contains at least 1 stack
        - Java stack (Java method calls)
        - Native stack (Native method calls in VM)
- Other: For example native C code
- Debug Out-Of-Memory Errors
``` {.bash}
# Print out heap dump
-XX:+HeapDumpOnOutOfMemoryError
# Native Memory Tracking
-XX:NativeMemoryTracking=summary -XX:+UnlockDiagnosticVMOptions -XX:+PrintNMTStatistics"~ for advanced tracking
# Limit stack size
-Xss1M # to set the maximum of stack size to 1M
# Limit heap
 -Xmx
# Limit percentage of total RAM but only for heap (!)
 -XX:MaxRAMPercentage
```

# 📅 25.04.2022 Team: Meeting rules
-   👥: Team and 👩‍🏫: Facilitator
-   Before the meeting
    -   👩‍🏫 Before sending out the invite go through the 7Ps below and put relevant information in the invite (like outcome and preparation)
    -   👩‍🏫 Use the optional functionality for participants
    -   👩‍🏫 When the meetings includes some kind of discussions create a Mural/Miro/Jamboard in advance
    -   👩‍🏫/👥 Do you want to ask someone to help you out with creating meeting notes?
    -   👥 Accept/reject meeting asap so that the facilitator can plan accordingly
    -   👥 Do preparation required of the meeting
    -   👥 When in doubt, request a purpose, product and suggested process
-   During the meeting
    -   👩‍🏫 Give context to everyone participating in the meeting
    -   👩‍🏫 As the facilitator always come back to the outcome and push for tangible results
    -   👥 It is not the responsibility of the facilitator only to make this a productive meeting (everyone should limit scope and avoid rabbit holes)
-   After the meeting
    -   👩‍🏫 Create action items in the Daily Guide
    -   👩‍🏫 Update the Meeting notes and follow up with action items e.g. updating a LADR
    -   👥 Everyone should go through the meeting notes and provide comments if necessary

# 📅 22.04.2022 IntelliJ: Shelve and unshelve changes
-   Like stashing a change list (creating a patch), which you can apply later again
-   this happens automatically in IntelliJ when you pull with changes in working dir

# 📅 22.04.2022 Jackson: Objectmapper for enums
-   Serialization: `@JsonValue`, indicates a single method that the library will use to serialize the entire instance. e.g. `toString()`
-   Deserialization : `@JsonCreator`, just out this on the constructor and specificy the primitives you want to create the object from

# 📅 21.04.2022 Networking: DNS server mappings are cached locally Working on Windows OS
-   `nslookup  <url>` does reach out to dns server to retrieve IP
-   `tracert <url>` goes same route as os, uses cache (not reaching out to dns server every time)
-   `ipconfig /flushdns` clear local cache
-   there is also a local dns lookup
    -   specified via Windows `c:\Windows\System32\Drivers\etc\hosts` file

# 📅 20.04.2022 Networking: Principle of Round Robin
-   Easy process for network/process schedulers to distribute load/data amongst workers etc.
-   Round-robin DNS: Principle applied on redundant DNS servers, like a load balancer

# 📅 19.04.2022 Networking: Fundamentals
-   `nslookup <url>`: Nameserver lookup, shows responding dns server for that url and the ip\'s it is resolving to
-   `route print` / `netstat -r`: Showing routing tables
-   `DNS server`: Responsible to translate domain names into IP adresses
    -   Recursive DNS server
        -   for dns lookup
        -   usually run by our internet service provider (ISP)
        -   **but** *when you connect to a Virtual Private Network (VPN), the DNS server of your VPN replaces the DNS server of your ISP*
    -   Authoritative DNS server
        -   hold official dns records for a domain
        -   provided by domain registrars
-   DNS servers can be configured differently, when queried for a domain they return a ...
    -   Static IP server e.g. for servers
    -   Dynamic IP server e.g. when devices are not permanently connected to the network
    -   Round Robin server, return a list of IP addresses, all being able to serve the request
    -   Load balancing server, return von IP address which can server request, load is distributed optimally
-   What do I see when I type in whatismyip on the internet?
    -   this is the IP the isp is assigning to my router, all devices connected to the router have the same IP adress
-   How can I have a different IP in my local network?
    -   each router has a *dhcp server* assigning local up\'s to all devices
    -   process:
        -   1.  New device is *broadcasting* (requesting IP), broadcast is sent to dhcp server and to all other devices

        -   1.  dhcsp has a ip range to choose a new ip from and sends it out to new device and all other other devices

        -   1.  new device with ip is sending out confirmation to dhcp and all other devices
    -   if local device (with local IP) wants to send a request to some server in the internet it needs a NAT
-   How are IP adresses assigned in a VPN network?
    -   in the same fashion, a vpn network also has a dhcp server
-   A network problem I\'ve encountered
    -   Your **ISP** / **router** settings either defaults to ipv6 or ipv4 (in my case ipv6)
    -   For domainA the **dns server** from the **vpn** gave back both ipv6/ipv4 addresses (with precedence to ipv6)
    -   since isp defaults to ipv6 the ipv6 is chosen for that domainA
    -   the problem is that the vpn is not supporting ipv6 and request to a ipv6 goes not through vpn but the internet
    -   resulting in not being able to access the website

# 📅 19.04.2022 InfoSec: Threat modelling

-   per definition you never have a complete thread modell
-   it is more about brainstorming possible causes to mitigate them, in reality a breach always consists of a combination of several threats
-   different kinds of threat modelling
    -   broad threats and thread sources: also understandable by non-tech people - identifying bad actors and their motivations
    -   technical threats and vulnerabilities
-   always include PO because they know about cruciality of data and business context
    -   *When cyber security losses occur they are business losses.*
-   *Threat modelling little and often*
    -   start with a thin slice, ideally what you are working on
    -   it is better to continously build up the threat modelling muscle
-   Examples of well scoped sessions (from [source](https://martinfowler.com/articles/agile-threat-modelling.html#ScopingTheSession))
    -   Scope in current iteration.
    -   An upcoming security sensitive feature, such as a new user registration flow.
    -   The continuous delivery pipeline and delivery infrastructure.
    -   A particular microservice and its collaborating services
    -   A high level overview of a system to identify security tech debt.
-   **Evil brainstorming**
    -   come up with ways to *attack, break and frustrate* a particular system
    -   Use STRIDE cards
-   **Learnings from running Threat Modelling session**
    -   Structure followed

        a\) Map out System (already prepared)

        -   give people the chance to add things
        -   ask questions
        -   always only things relevant to the scope (e.g. current feature played)

        b\) Label data

        -   Copy over system and add where data flows
        -   you can make different distinctions if they fall into different data categories
            -   PII, Non-PII, Financial data, Technical secrets, User secrets
            -   at-rest (persisted), in-flight (data just running through the system)

        c\) Do Evil brainstorming

        -   Copy over mapped system
        -   brainstorm together where a system could be hacked (according to STRIDE)

        d\) Rank according to Impact and Probability

        -   Two voting rounds and then arrange on magic quadrant

        e\) Coming up with action items (resulting in different outcomes)

        -   Add to tech depth
        -   Additional AC in stories
        -   Additional criteria to DoD
        -   new Story, Spike or Epic

        f\) Additionally you can also come up with low-hanging fruit (things which are easy to accomplish e.g. adding a health check)

# 📅 13.04.2022 Infrastructure: Jenkins 101
- [source](https://joostvdg.github.io/jenkins-pipeline/core-concepts/)

-   `Step`: A single task
-   `Built-In vs Agents`
    -   built-ins coordinating
    -   agents are doing the actual work (reasons: infosec/networking, different OS\'s)
-   `Workspace`
    -   should be cleaned up, tmp
    -   where artefacts are written out
-   `Stage`
-   `Sandbox and Script Security`
-   `Stash & archive`
    -   stash: forward results from one step to another (IO, CPU expensive)
    -   archive: expose artefacts over api/ui

# 📅 13.04.2022 Python: How to mock in python

-   Part of unittest (standard module in python)
    -   `from unittest import mock`
    -   `from unittest.mock import MagicMock`
-   If you want to mock a single method of an object: `@mock.patch.object(TheClassOfMethod,'the_method_to_mock', side_effect=returns_result_of_mocked_method)`
-   If you want to mock the whole object (and do not care about other overwritten methods):
    -   example for replacing request object and mock post method: `@mock.patch('requests.post', side_effect=returns_result_of_mocked_method)`
-   Difference between `side_effect` and `return_value`
    -   `side_effect`: provided method is called with orginal parameters on the object which is mocked
    -   `return_value`: mock method is called empty and return value is returned
-   Learning: When you pass in the mocked object into the test method, they are in reverse order of the patch annotations

``` {.python}
@mock.patch.object(ClassA, 'do1')
    @mock.patch.object(ClassB, 'do2')
    def test_something(self, mockB, mockA):
    mockA.assert_not_called()
    mockB.assert_called_once()
    self.assertEqual(mockB.call_count, 2)
```

# 📅 12.04.2022 Java: System.getProperty vs System.getenv

-   environment variables are just taken from the OS
-   properties are like start parameters you pass in into the jvm
-   usually prefer properties over environment variables because they are more specific in scope
    -   for environment variables you could always have another process in the same shell changing the behavior of your application

# 📅 12.04.2022 Maven: Testing with Maven

-   tests usually run with `maven-surefire-plugin`
-   you can set filters for including/excluding classes: `<includes> <include>**/*SpecialTest*.java</include></includes>`
-   set verbose logging (including debug) with `-X` on mvn command
-   scope test in maven is analogous to testImplementation in gradle

# 📅 12.04.2022 Java: Drawback of multi-module projects when libabries depend on a jvm

-   when you have a multi-module projects and run a test task on root level, the tests of the different modules are obvisouly spawned in several jvm\'s. When you have mechanism which relies on the fact that tests are run in the same jvm (e.g. pact interactions have to be all validated before results are published) you have to put those toegther in a separate module

# 📅 08.04.2022 Agile: Philosophy Kanban

-   Comes from Toyota where you have different steps in automanufacture workflow, you a high flow from one state to the other
-   At every state transition the card should move into a new process so e.g. Ready for development is not useful becaue it is just waiting there. Better to leave it in analysis and label it as ready
-   You also should not have a sign-off column because sign-off meeting should be part of the state change to be done. If you have no such column and stories are waiting longer in dev due to waiting for a meeting sheduled to it just makes the problem more visible and should be resolved

# 📅 08.04.2022 Maven: Compiling

-   if you have maven modules imported, compiling the dependent modules is not enough - you also have to package them
-   otherwise you might get some `NoClassDefFoundError`

# 📅 07.04.2022 Circuit breaker

-   If you have send many requests and get a lot of errors you pause requests right away to reduce load on the target system
-   it is difficult to decide when to allow requests again (increase limit)
-   e.g. Histrix
-   Different states: Open, Closed, Half-Open (probe if downstream system is ok again, low traffic)

# 📅 07.04.2022 Adaptive concurrency

-   [source](https://vikas-kumar.medium.com/handling-overload-with-concurrency-control-and-load-shedding-part-2-6b8b594d4405), [source~2~](https://netflixtechblog.medium.com/performance-under-load-3e6fa9a60581)
-   Netflix switched over from circuit breakers
-   capacity changes over time, calling services should adapt expected capacity automatically
-   you monitor congestion and calculate limit via algorithm
-   only works if all calling services implement this

# 📅 31.03.2022 The 12 Factor App

-   **Config**: Externalize all config from Code
    -   Config is everything that varies accross deploys (prod/staging/tenants), code not
    -   Never store constants in code for things like services adresses but externalize config
        -   via environment variables
        -   runtime configurator
    -   when you externalize do not group those configs into environment groups, combining those groups later adds a lot of complexity e.g. `joes_staging`
    -   Litmus test: At every point in time you could open source the project without giving away credentials etc.
    -   Motivation
        -   have crucial information (which might be used in other contexts) at a centralized place e.g. when service~url~ is changing
        -   you only have one artefact: Build once deploy anywhere
        -   It is faster: Change externalized config, no need to rebuild the image
        -   You do not mistakenly check in such config into source
        -   config is language independent

# 📅 30.03.2022 QA: Learnings on pact and pact broker
- why to use tagging for feature toggles? ([read more on this](https://docs.pact.io/pact_broker/tags))
  - on consumer side you have a feature toggle but you don\'t know if the provider already has the features implemented, integrated in the deployed artefact. That is why you want to tag with the consumer/provider version after deploying the artefact. You have a mapping between consumer versions of a contract and how this related to the deployed artefacts, helping you decide which feature toggles on the consumer side you can toggle on. The other way of doing it would be to check on the deployed artefacts which feature is present and which not but doing it this with the pact contracts is like putting a matching pattern over the codebase using the logic you already have set anyway for the contract testing
- how does pending contracts work?
  - motivation: You want to introduce a change as a consumer without immediately breaking the provider. The provider decides when to fufill the contract
  - First you have a new contract version on consumer side, first you would introduce this as pending
  - a pending contract never brakes the pipeline on provider side
  - once the provider meets the requirements of the new contract the pending flag is removed
  - if at another run the contract brakes on provider side the pipeline also breaks

# 📅 29.03.2022 Workshop: Airport metaphor
-   Icebreaker: Where do you want to go next?
-   Healthcheck: Check-In at airport
-   Action items: Take-Off
-   Brainstorming
    -   Learned: The scanner shows all
    -   Liked: Celebrate in the VIP lounge
    -   Disliked: What is hidden in the restricted area?
    -   Longed for: Where should we travel to?
-   Feedback: Stars with tripadvisor: From worst trip ever, I will do the next retro by myselves
-   Who is next: Stuart with sunglasses

# 📅 17.03.2022 Sensible practices
- Trunk-Based development
  - **Why**: Faster feedback, resolve merge conflicts quicker, easier to code review because smaller changes
  - Prerequisite of Continuous Integration
  - If not possible only very short feature branches
- TDD
  - **Why**: Simpler, just make the test pass. More modular code. Fast feedback - less debugging during development
- Pairing
  - **Why**: Fast feedback, shared ownership and knowledge transfer
- Security first
  - Scanning for vulnerabilities in pipeline (libs, container immages etc.)
  - Secret manager
  - Thread modelling part of agile routine
  - Quick reaction strategies e.g. monitoring, fix-forward
  - least privilege principle when it comes to access etc.
  - Consider checklists like OWASP
  - **Why**: Faster feedback and therefore impact on code and design, reproducable and therefore less dependent on security SME for audits etc.
- Automated build pipeline
  - within miniutes
  - everyone has easy access to current state and should be informed in case of a failure
  - prioritize speed and non-flakyness of pipeline
  - **why**: quick feedback if new changes introduce defects, less efort because no manual steps
- Automated deploy pipeline
  - also automated infrastructure (e.g. terraform)
  - manual approvement can happen but no manual steps
  - (❗) artefact is build once and deployed to different environments with different configuration
  - Avoid configuration drift in environments (different settings in infra)
  - **why**: *Automation reduces errors caused by humans.* + faster feedback, less time required

Early and continuous deployment

-   Start early to deploy to prod so you do not hide the work like cfr\'s required to deploy to prod
-   also deploy components regulary even if there was no change to ensure that everything is still working
-   **why**: Early feedback and repeatability

# 📅 11.03.2022 - 17.03 Basics of DDD

-   Domain Model := Business logic, context etc. without any technical details (including persitence etc.). Everyone involved in the development lifecycle should use that language which was agreed on (helps avoiding translation errors)
-   Stategic vs Tactical design
    -   Strategic design is about what we build
    -   Tatical design is about how we build it
-   **Strategic design** (also for non-technical people)
    -   Goal: Go from problem space -\> \'as-is\' solution space -\> to better solution space: Question about the **what**
    -   What is the problem with several subdomains each having their own language
        -   in order to integrate with those subsystems you have to translate between different domains
        -   forces you to introduce even more new language to have a common understanding
            -   for the model this means it get quite complex and bloated when you want to account for each subdomain
        -   results in misunderstandings, tribe knowledge, slow on-boarding etc.
    -   the most subsystems (core domain) should be organized as a bounded context, where the language within is unambiguous
        -   the other subsystems are called generic, supporting subsystems
-   **Tactical design**
    -   how to organize your code, what tools to use
    -   Problem statement:
        -   Usually clients operate on entities (e.g. a service, controller enforcing business rules) leading to business logic which is spread out around the codebase
    -   Solution: Put everything in your domain model and expose business logic as public methods, no other methods allowed
    -   ❓ Put it to a extreme: Does this mean a strict DDD model should not have getters and setters?
    -   Terms
        -   **Entity**: Defined independently of properties, e.g. you, who can change over time
        -   **Value objects**: Identity defined entirely by its values e.g. color brown.
            -   always consider value objects over primitive types because you can encode business logic in them e.g. mass can\'t be negative
        -   **Aggregates**: Collection of entities or value objects
            -   important for enforcing buiness rules on several objects
            -   **Aggregate Root**: Most parent element of aggregate structure
                -   when you want to change a element in the structure you have to do this through a exposed method in the aggregate root
        -   **Domain Event**: *Captures the memory of something interesting which affects the domain*
        -   **Repository**: Only operates on aggregate roots and persists those objects. Changes only allowed through public methods on aggregate root. Not part of the domain model
        -   **Application services**: Like a controller: calling repository and public methods on domain object. Very thin layer.
        -   **Domain services**: When a business logic spans across several aggregates. Part of domain model.

# 📅 25.02.2022 How to bring the quiet on board?

-   Game \"Button\"
    -   \"Everyone speaks once before anyone speaks twice.\"
    -   In the beginning everyone has to raise their hands.
    -   Based on the talking stick tradition of the native americans
-   Everyone has to facilitate at some point
-   Do brainstorming not in anonymous mode

# 📅 25.02.2022 Alternative way of roles and reponsibility matrix (R.A.C.I.)

-   [source](https://en.wikipedia.org/wiki/Responsibility_assignment_matrix)
-   For each task/domain differentiate the following
    -   Responsible: Does the work (but can delegate if necessary)
    -   Accountable: Checks if work is done
    -   Consulted: Contributors, providing input
    -   Informed: Are kept up to date

# 📅 25.02.2022 Alternative way of Stackholder mapping Ask the follwing questions and then do a affinity mapping over power/interest quadrants

-   Who will be impacted by the project?
-   Who will be responsible or accountable for the project?
-   Who will have the decision authority on the project?
-   Who can support the project?
-   Who can obstruct the project?
-   Who has been involved in this type of project in the past?

# 📅 25.02.2022 Workshop formats I liked from Gamestorming book

-   **Brainwriting**: Each member writes stickes with idea and passes it to the next person who refines, appends an idea to that sticky
-   **Fishbowl**: One part of team has a discussion, the other listens and afterwards summarizes (done with inner, outer circle)
-   **Forced Analogy**: Come up with a random list of things and then find analogies to our problem: \"How is this problem similiar to XY?\"
-   **Low-Tech Social Network**: Graph on mural and people have to draw connections between them (hobbies etc.) - like \"Find 10 things you have in common\"
-   **Force-Field-Analysis**: In the middle \"Some change you want to achieve\" and both side \"Forces for change\" and \"Forces against change\" (from Lewin)
-   **SQUID**: Come up with questions, second round - ask questions. Repeat those steps, layer by layer

<p align="center"><img height=200 src="https://raw.githubusercontent.com/biocarl/img/master/squid.jpeg" /></p>

# 📅 25.02.2022 What questions to ask during a workshop (as facilitator) from Gamestorming

-   **Opening**
    -   \"How do you define the problem you are facing?\"
    -   \"What kinds of things do we want to explore?\"
    -   \"What are the biggest problem areas\"
-   **Navigating**
    -   \"Are we on track?\"
    -   \"Did I understand this correctly?\"
    -   \"Is this helping us to get where we want to go?\"
    -   \"Is this a useful discussion thread?\"
    -   \"Should we table this for now and put it on a list of things to talk about later?\"
-   **Examining**
    -   \"What is it made of?\"
    -   \"How does it work?\"
    -   \"Can you give me an example of that?\"
    -   \"Can you describe it in terms of real-life scenario?\"
-   **Experimenting**
    -   \"What are we missing?\"
    -   \"What if we are wrong?\"
-   **Closing**
    -   \"How can we prioritize those options?\"
    -   \"What is feasable?\"
    -   \"What can we do in the next two weeks?\"
    -   \"Who is going to do this?\"

# 📅 24.02.2022 How to secure your endpoints

-   Different options
    -   Lightweight Directory Access Protocol (LDAP) - [link of disadvantages](https://blog.lithnet.io/2018/03/the-ldap-authentication-anti-pattern.html)
        -   painfull due to credential rotation
    -   Credentials Flow - [link](https://auth0.com/docs/get-started/authentication-and-authorization-flow/client-credentials-flow)
    -   Mutual TLS - [link](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/)
        -   also ensures that traffic is encrypted

# 📅 22.02.2022 How to have engaging conversations in a team (workshop)

-   Add here also the campfire workshop (tell a story)
-   Two different types of identity
    -   local identity
    -   universal identity: \"I am human so nothing human is foreign to me\"
        -   We all have problematic families
        -   We\'ve all been disappointed
        -   We\'ve all been idiotic
        -   We\'ve all loved
        -   We\'ve all hated
        -   We all have dreams that we do not live
        -   We all have anxieties
        -   We all have ambitions
        -   We all have bodies that give us difficulties
-   You always have the choice to direct the conversation to deep talk or small talk
    -   Surface Self
        -   Where we go
        -   What we do
        -   Who we have seen
        -   What\'s been going on
    -   Deep Self
        -   What we fear
        -   What we love
        -   What we hope for
        -   What we regret
        -   What we\'re sad about
-   Releated workshop format: [Campfire](https://gamestorming.com/campfire/)
    -   Set the scene of sitting together at a fire
    -   Put on Mural the \"Wall of Word\" -\> people can use a word and tell a story and put that stick on the \"Story Thread\", which is growing snake-like during the workshop
    -   Before you \"put out the fire\", ask if there were any lessons learned, insights or feedback

# 📅 22.02.2022 Proxy environment variables in Unix

-   if you want to route traffic over a proxy you need to set those
-   `http_proxy`, `https_proxy`: Sets the proxy all traffic will go through
-   `no_proxy`: Comma-separated list of domain extensions the proxy should not be used for. For instance '.google.de', proxy will not be used for german google queries

# 📅 21.02.2022 Team: Agile routines I enjoy

-   Culture cafe
    -   present softskills, ways of working in a bi-weekly manner
    -   also encourage the client to contribute to it
    -   do series to build upon the sessions
    -   give small homework
-   Tech Huddle
    -   have a excel sheet where every can vote on the proposed topics
    -   let also other people ask for topics and someone else will present it
-   Book club
    -   vote for a book to read
    -   tbd
-   Health Check (e.g. in retros), more details elsewhere
-   Tech Health Check

# 📅 15.02.2022 A case against Spring profiles and beans depending on profiles **A case against profiles**

-   You should always externalize as much config as possible (see [12factor](https://12factor.net/config))
    -   **strict separation of config from code. Config varies substantially across deploys, code does not.**
    -   Reduces complexity

    -\> so even if using spring profiles they mainly should contain references to environment variables which makes different profiles obsolete
-   You also should not group configurations (may it be external or not) since this just increases complexity, each config parameters should stand for itself

**A case against profile dependent annotations**

-   You sometimes need different beans e.g. a different client logic depending in which environment e.g. also deploys for different tenants. To set this different behavior do not go for a `@Profile` because
    -   it is super confusing to know what is happening in which profile when looking at the code,epecially if you are using negations like `!test` -\> source: [Don't Use the @Profile Annotation in a Spring Boot App!](https://reflectoring.io/dont-use-spring-profile-annotation/)
    -   also makes test setup more complicated if certain beans require a certain profile to be active
    -   the more profiles you have adding up the more confusing it is to debug and understand which is overwritten by what
    -   **Solution**: Use a value environment in config file and then annotate the beans like so `@ConditionalOnProperty(name="service.mock", havingValue="true")`
-   technical learning: in `@ActiveProfiles` you do not specify several environments like in `@Profile`: `test,staging` but provide them as a array: `@ActiveProfiles({"test", "staging" })`

# 📅 11.02.2022 A nice way of checking the team health in the retro

<p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/healthcheck.PNG" /></p>

# 📅 09.02.2022 What to do after a brainstorming session

-   Pre-define brainstorming outcome by setting a meaningful space beforehand
    -   Example: Give some grid and everyone has to arrange the stickies they put there in the appropriate corners e.g. High/Low Impact/Effort - Quadrants
    -   Other \"meaningful spaces\"

<p align="center"><img height=100 src="https://raw.githubusercontent.com/biocarl/img/master/20220224_215317.jpg" /></p>
<p align="center"><img height=100 src="https://raw.githubusercontent.com/biocarl/img/master/20220224_215351.jpg" /></p>

-   Everyone votes on the most important ideas (also vote with different emojis like ❤️‍/🔥)
    -   Similiar, idea of \"Forced Ranking\" (everyone needs to come up with their own ranking)
-   Talk through each items and allow people to join the discussion
-   Everyone presents their own sticky or do something else with it (e.g. invert it to the opposite)
-   Cluster according to certain criteria: Affinity mapping (JK Method)

# 📅 08.02.2022 Why you should never put PII data in url

-   A lot of components log url, man in the middle attacs and ajax calls from the browser (e.g. malicious browser extensions/browser history), user might not be aware what link they shared
-   **Solution**:
    -   \'Break\' with Rest and always do a POST and no GET (will be SSL encrypted)
    -   Put tokens etc in header

# 📅 03.02.2022 IntelliJ Set `pwd` in Shell

-   Just drag folder from tree view into shell and the `pwd` changes

# 📅 21.01.2022 Token generation via metadata server (GCP)

-   when running Cloud Run you usually have a deployer service account and a runner service account
-   In a Cloud Run Instance you can hit the metadata service endpoint which will do some Google magic to authenticate via the runner service account
-   Example for token generation: `http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token` (switch out default with the sa account you need)

# 📅 20.01.2022 Why VPC connector's are needed in GCP?

-   When using a Shared VPC
    -   Chunked in different subnets (IP ranges) is tied to one region (e.g. europe-west-1)
-   Serverless Services like Cloud Function and Cloud Run can't be deployed into a specific network (like a shared VPC) because they use their own google internal network
    -   That is why you need a VPC connector: routes incoming and outgoing go then through/to a shared vpc
    -   A VPC connector needs its own subnet (no other resources are allowed in there)
-   There is certain ingress and egress settings specifying which type of traffic is routed over the VPC and which not
    -   `all-traffic`: Sends all outbound traffic through the connector.
    -   `private-ranges-only`: Sends only traffic to internal addresses through the VPC connector.

# 📅 17.01.2022 - 19.01 Systemischer Coach - Ausbildung (Modul 1)

-   Methoden für Team
    -   World Cafe
        -   4 Kleingruppen + 4 Auserwählte
        -   Es gibt 4 Themen welche die Auserwählten durch die Kleingruppen tragen
        -   ursprünglich auf Tischdecke schreiben/ aber auch online möglich (breakout rooms für Kleingruppen während Auserwählte)

        <p align="center"><img height=200 src="https://raw.githubusercontent.com/biocarl/img/master/world-cafe.jpeg" /></p>
        
    -   Freies Spekulieren / Positives Hypothesieren
        -   Kleingruppen sprechen jeweils einer Person positive Eigenschafen zu
        -   Danach kann der Einzelne die Vermutungen richtigstellen
    -   Kreise/Felder auf Whiteboard aufzeichnen und jeder Einzelne ordnet sich dabei zu und man bespricht das

# 📅 14.01.2022 team: E.L.M.O. - The remedy against rabbitwholes

-   E.L.M.O. := \"Enough, Let's Move On\"
-   You would quietly raise your hand and after a critical mass of people raising their hand the people stuck in their discussion would stop and we laugh alltogether (according to theory)
-   For mobile: [meeting cards](https://mpetersen.github.io/meeting-cards/)

# 📅 11.01.2022 CIDR ranges and IPV4

-   How to calculate the range ([link](https://erikberg.com/notes/networks.html))
    -   you have a start IP (255 is max before next block is flipping)
    -   and a `/{range}` specifciation
    -   with that range you calculate the number of available IP\'s

    <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/master/cidr.PNG" /></p>
    
    -   the range you retrieve by incrementby that amount from the start IP
-   also watch this *<https://www.youtube.com/watch?v=MmA0-978fSk>*

# 📅 11.01.2022 Rules for ankifying business knowledge

-   No frameworks releated knowledge
-   No definitions of terms you will encounter frequently
-   Only ankify after some time (the longer the better)
-   Review on web, always pull changes on AnkiDroid after review

# 📅 11.01.2022 Conway\'s Law (Presentation by James Lewis)

-   Basic idea of microservices: Splitting in domains
-   The software architecture will mirror the communication of that organisation
-   Example: Open-Source
    -   is the most decoupled because everyone is very separate
    -   communication was asynchronous
-   Inverse Conway Maneuver ([link](https://www.thoughtworks.com/en-de/radar/techniques/inverse-conway-maneuver)) ✔️
    -   Adapt organisation structure according to your newly proposed software architecture
    -   Netflix: Teams which have to communicate with each other also physically next to each
    -   Organize product lines through whole stack/layers required

# 📅 11.01.2022 Versioning in multiple environments

-   Situation: When we publish a new version it can break other applications in the system (also potentially maintained by other teams). So by publishing we potentially block all environments, of all teams
-   Possible solutions
    -   For team owned environments you could make them resposible for pulling the newest version
    -   Push out regurarly to avoid not uptodate environments
    -   have a environment where the others are not dependent on to test first (with e2e etc.)
    -   use contract testing to avoid structural breaking changes
-   How to decide when to push out new versions to each environment?

# 📅 11.01.2022 Multitenancy

-   Definition: Sharing a single application for multiple tenants (different markets/environments) ✔️
    -   you just provide a tentant id and then request is handled accordingly by application
    -   often you have one database but different schema for the different tenants
    -   tentant groups get their own deployment
-   Two approaches
    -   Avoid Multitenancy: For each environment a different deployment
        -   no multitenancy problem
        -   take care only for a single environment
        -   very often legally required to have data seperated (country laws and Competition law)
        -   easier to debug (e.g. tracing just needs to be labelled with environment)
        -   fast lane for specific fixes (since you also have a separate pipeline) and do not have to wait for other deployments to go green
    -   One application serving multiple tentants (multitenancy) ✔️
        -   it is hard to find bottleneck in system for a specific tenant because e.g. backpressure might comes from a different tenant where the same application is also responsible for
            -   Issue: Separation of concerns is not equivalent to the separation of ressources
        -   all tests for other tentants have to green before deploying
        -   takes longer to do migrations (you have to do this for all tentants)
    -   You can do multitenancy on several levels

    <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/9eb6460880f5e3ec606d7128be0db658f1ddccab/The-multi-tenancy-continuum.png" /></p>

# 📅 11.01.2022 How to embed images in org files (rendered on Github)

-   Upload to img repo and then open image in new tab and ue the githubusercontent url

#+html: <p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/34edba9d7e71c0887534bf0310ba0c137f59afbc/gap_map.png" /></p>

# 📅 10.01.2022 InfoSec: How to tackle dependency drift?

-   dependency drift :=dependencies coming out of age slowly
-   if static version numbers
    -   how to ensure that people go over them and update? How to decide?
-   if automatic dependcy increment (like latest)
    -   there is no instance checking those patches if they introduce a bad actor for example
-   there is managed and recommended lists of version (see here bom files)
-   when having semantic versioning of dependencies you can for instance do automatic increasing of versions on patch versions but manual increment on minor or major versions
-   incrementing major or minor versions is usually also needing a new feature set which does not necessary increase security and requires expertise and testing for verifying that no breakin changes occur

# 📅 10.01.2022 InfoSec: For what to sign a Data processing Agreement (DPA)?

-   DPA: Data processing Agreements
    -   even potentially pairing with someone who shares PII data via screensharing has to be covered
    -   also as external consultancy this is required for the client because we can often easily elevate access and therefore access prod data (think of audit logs etc.)

# 📅 10.01.2022 workshop: How to run a futurespective/ Learnings from minion futurespective

-   Exercises
    -   Hopes and Concerns [- link](https://www.funretrospectives.com/hopes-and-concerns/)
        -   Try to focus on the positive
        -   afterwards encourage the team to do something so their hopes come true (by this work really becomes fun again)
    -   That Guy and This Guy [- link](https://www.funretrospectives.com/that-guy-this-guy/)
        -   You called it \"team culture\"
        -   Think of people/experiences from past/current projects and how they guided you
        -   \"So if you are seeing here some behavior which can can identify with don\'t take it personal. Probably a lot of people show this kind of behavior and/or the remark might result from a totally different context/project\"
        -   Alteration:
            -   First each person brainstorms 5 mins the behaviour they dislike
            -   then you say you can\'t bear all that negativity and they are responsible to invert and propose better behavior
            -   for each sticky they have to put in a positive behaviour alternative, thereby it is good to encourage that not only the negation of a behavior is possible: e.g. comes to late -\> comes on time -\> comes even 5 mins earlier to socialize
            -   Each person has to present their positive and negative behaviour
            -   While the others have the option to reflect on their behaviour
                -   what bad behaviours you catch yourself doing sometimes?
                -   which positive behaviours would you practice more?

# 📅 10.01.2022 Team: High-Performing Teams

-   Warmup-Question: Tell us a story: What was the best team you were ever part of?
-   Five Dysfunctions of a Team (Book) [link](https://www.youtube.com/watch?v=GCxct4CR-To)

<p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/master/dysfunction.jpeg" width="500" /></p>


-   **Absence of Trust**: Without trust you do not have the base to go into conflict
    -   Action: Do the first step and share challenges, fears and limitations
-   **Absence of Conflict**: This is not only ok but necessary in a team. It is just a way to persue truth
    -   Action: Cultivate safe environment for diverse opinions, ask questions
-   **Absence of Commitment**: Without conflict you do not commit, you do not care about the decisions and just go along
    -   Action: Make outcomes specific and crisp (also DoD - Definition of Done)
-   **Avoidance of Accountability**: Without commitment we won\'t hold each other accountable. If people are commited they also will have the courage to confront each other
    -   Action: Confront difficult issues
-   **Inattention to Results**: Not paying attention to results, at least not to the collective results. Everyone is just caring about themselves
    -   Action: Focus on collective results

# 📅 06.01.2022 Spring: Declare a object instance as a bean

``` {.java}
@Configuration
public class SomeConfig {
    @Bean
    public ObjectA objectA(){
        return new ObjectA();
    }
}
```

# 📅 06.01.2022 Spring: Learnings about Spring Dependencies

-   You can use the [Dependency Management Plugin](https://docs.spring.io/dependency-management-plugin/docs/current/reference/html/)
-   or import bom files with gradle 5 [link](https://docs.gradle.org/5.0/userguide/managing_transitive_dependencies.html#sec:bom_import)
-   purpose is here explained - [link](https://blog.mrhaki.com/2019/04/gradle-goodness-use-bill-of-materials.html)
-   if bom has some old dependency recommendations (not updated), you can overwrite with this

``` {.groovy}
dependencyManagement {
    imports {
        mavenBom 'urltobom:version'
    }
    dependencies {
        dependency 'url:artifact:version'
    }
}
```

# 📅 06.01.2022 QA: Learnings about pact and contract testing

-   usually you write consumer tests in form of Unit tests and from those a pact file (contract) is generated

-   that pact file can be shared via a pact broker with the provider where that file is used to generate provider tests

-   you only want to test syntax and semantics, you do not want to test functionality [source](https://docs.pact.io/consumer/contract_tests_not_functional_tests)

    -   that means: A contract test does not check for side effects! (e.g. db entry created etc.)
    -   what about validation and error reponses?
        -   it is good to cover sad path\'s to make sure that consumers know\'s how provider behaves in such cases

        -   BUT do not test all the different validations

        -   otherwise we create unnecessarily tight contract: e.g. if provider chooses to increase the char limit for a username that would unnecessarily break the contract for the consumer

        -   \"Write scenarios about how the validation fails, not why the validation fails\"

        -   Concrete example: Test one validation and do not care about specific failure but format

            ``` {.bash}
            Response is 400 Bad Request
            Response body is { "error": "<any string>" }
            ```

-   for pact file specification - [link](https://github.com/pact-foundation/pact-specification)

-   you can run provider tests either via a deployed instance / containerized local instance or do this via the unit test level where you call e.g. controller methods with the pact file defined input and convert this to JSON and compare this with the pact file provided output

-   when running e2e tests or pact tests you always need to take care of certain pre-conditions/states/setting up data, this can be quite complex

    -   often best to do this on a unit test level: you can mock/stub easily and do not need a populated database
    -   when using a real instance you should think of snapshoting certain db states for quicker state setups
    -   pact does not recommend to run pact tests against a public API because you can only setup the data via that API, making it slow and cubersome (also to reset)

# 📅 04.01.2022 Agile: Laws

-   **Conway's Law**
    -   \"Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization\'s communication structure\"
    -   Isomorphism between org communication structure and software design
    -   Examples
        -   if frontend and backend code is completely separate because there is also different teams
        -   if there is no product teams but feature teams this does not support the idea of microservices and ownership
        -   if there is a team for each country resulting in different codebase and approaches
-   **Hackmans' Law** ([source](https://blog.nuclino.com/two-pizza-teams-the-science-behind-jeff-bezos-rule))
    -   \"The larger a group, the more process problems members encounter in carrying out their collective work. \[...\] It's managing the links between members that gets teams into trouble.\"
    -   Also called coordination costs
    -   Ideal team size: Jeff Besos called this the Two-Pizza rule (meal for an ideal team)
    -   Number of links between members grow exponentially with growing team size
    -   That is the reason why introducing roles and norms is even more important (differentiation vs cohesion)
-   **Brooks' Law**
    -   \"Adding human-power to a late software project just makes it later.\"
    -   Because of Hackmans\' Law
    -   but also due to time to onboard and fact that certain tasks can\'t be devided:
        -   \"Nine women can't make a baby in one month.\" (see also [disjunctive tasks](https://en.wikipedia.org/wiki/Steiner%27s_Taxonomy_of_Tasks#Disjunctive))
-   Goodharts' Law
    -   \"When a measure becomes a target, it ceases to be a good measure.\"
    -   For example when university rankings were introduced, univesities started to focus only on rankings
    -   Also related to game theory: \"Tell me how you measure me and I will tell you how I will behave.\" (Eli Goldratt)
    -   also related: perversive incentive
-   Larmans' Law
-   Parkinsons' Law

# 📅 04.01.2022 Java: slf4j vs log4j vs logback

-   slf4j is a specficiation which logback is implementing
-   Log4J is the predecessor of logback

# 📅 04.01.2022 Weblogic 101

-   Application server for Java EE applications

# 📅 04.01.2022 Java EE 101

-   With Java EE you can easily scale because you can distribute the EJB\'s to different servers
-   The EJB (Enterprise Java Bean)
    -   Java EJB vs Spring Beans
        -   Java EJB is only a specification and implemented by application server e.g. Weblogic
        -   Spring Bean is already a implementation
    -   `@Remote`: The bean implementation can run on a different server, in different jvm (vs `@Local`)
-   `@Interceptors`: Implementing cross-cutting concerns like logging, auditing. Hooks into lifecycle and executes custom code like log when EJB is destroyed

# 📅 04.01.2022 Workshop: How to design workshops?

-   Warmup-Question: What is the first thing that comes up when you hear about that topic?
-   Present in the beginning what the outcomes of the workshop are
-   Nice last slide or mural unit
    -   GIVE US FEEDBACK.
    -   1 STICKY TO STRENGTHEN CONFIDENCE
    -   1 STICKY TO IMPROVE EFFECTIVENESS
-   Use svg generators to get nice backgrounds/structure of canvas
    -   blobs ([blobmaker](https://www.blobmaker.app/)) and put transparent brushes structure on forms
    -   or this [svg generator](https://app.haikei.app/)
-   When giving homework, usually if they are given to each person without a way of controlling the outcomes it is sometimes good to give them to a pair (so the likelyhood increases that one follows up) Example: \"Homework: Give a feedback to someone\" -\> Assign pairs to do this

# 📅 18.12.2021 Team: Thinking about the team

-   Good list for online games - [link](https://www.flcc.edu/pdf/studentlife/OnlineBoardGames.pdf)
-   General ideas of LEAN
    -   Central values
        -   Focus on value generation
        -   Quick feedback cycles
        -   Self-Organizing teams
    -   Subsets are Kanban, Scrum

# 📅 18.12.2021 Anti-Corruption-Layer

-   [source](https://dev.to/asarnaout/the-anti-corruption-layer-pattern-pcd)
-   If you want to integrate with a legacy system, but this legacy system does not fit with your newly defined domain model
    -   e.g. old conventions you want to do differently (unit from inch to meter)
    -   e.g. exposes several interfaces which from your viewpoint should be one (e.g. prepare shipping, optimize shipping and execute shipping -\> do shipping)
-   by introducing a layer of abstraction which translates, adapts your client call to the legacy system you avoid that legacy assumtion to do not corrupt your new system while not having to touch the legacy system
-   a anti-corruption-layer can also be bi-directional (when legacy system also has to call back to new system)
-   alternatives to an anti-corruption layer are
    -   Conform to legacy system (use same model assumptions etc.)
    -   Replace legacy system
    -   Do not integrate with legacy system
    -   EAI system (enterprise application integration)

# 📅 17.12.2021 Git amend change in commit which was not the last one

-   Step1: `_git rebase --interactive 'bbc643cd^'_` /hash of the commit which was before the desired change (note also the carret)
-   Step2: Change from pick to edit for the commit you want to change
-   Step3: Add to staging and do `git commit --amend --no-edit`
-   Step4: Do the actual change and then do `git rebase --continue`

# 📅 16.12.2021 Which team should take care of service x?

-   Responsiblity: Who introduces the service and therefore should own it?

vs

-   Dependency: Which team can afford to be dependent on the other team? What happens if service x does down and other team is not available?

# 📅 15.12.2021 Terms

-   WADL: Web application description language: XML description of a REST service (e.g. like swagger in yaml/json)
-   WSDL: WADL equilvalent for SOAP service
-   `.xsd`: A schema for an `.xml` file

# 📅 15.12.2021 Deactivate IntelliJ Bell Sound for vim emulation

-   `set visualbell`
-   `set noerrorbells`

# 📅 14.12.2021 Unix routing and networking

-   Check if a certain port is open
    -   `telnet ip port`
-   Check if a hostname resolves to a certain IP
    -   `host address_name`
-   If you want to route a domain name to a IP
    -   edit `/etc/hosts`
    -   Format: IP -\> adress~tobemapped~
-   If you want to map from one IP to another IP (`127.0.0.1`)
    -   `iptables -t nat -A OUTPUT -p all -d  192.168.101.101 -j DNAT --to-destination 127.0.0.1`

# 📅 10.12.2021 Gradle: Lazy and eager configuration/creation of tasks

-   Usually all tasks are configured right from scratch (configuration phase)
-   this can lead to issues if you only want to configure certain things when you actually execute a task
-   for lazily configuration have a look at [task configuration avoidance](https://docs.gradle.org/current/userguide/task_configuration_avoidance.html)
-   `create` ist eagier und `register` lazy task creation/configuration
-   for an existing task you want to configure (only when executed)
    -   `tasks.named('bootRunLocal').configure{}`

# 📅 08.12.2021 Learnings about liquibase

-   `relativeToChangelogFile`: Allows you to reference other changeset relative to the parent changeset and not from classpath (needed e.g. when applying liquibase migrations from different contexts local and test)
-   a changelog file allows you to group changes based on domain/table etc.
-   you can either execute migrations through Spring or in a separate Gradle task
-   Liquibase allows for specifying contexts so that only specific changesets are executed in a certain environment
-   You can also specify several activities (set of configurations) which can run one after another (see runList)

# 📅 08.12.2021 Curl: Simple GET with basic auth header

-   `curl -v  -H "Authorization: Basic (base64 username:pw)"`

# 📅 07.12.2021 Bash: Reverse Search in Unix

-   Search: `CRTL` + `R`
-   Cycle through results: `CRTL` + `R`

# 📅 06.12.2021 Postgres: Grants in postgres

-   `GRANTDELETE ON ALL TABLES IN SCHEMA PUBLIC TO root;`
    -   Grants privileges only to existing objects
-   `ALTER DEFAULT PRIVILEGES IN SCHEMA PUBLIC GRANT DELETE ON TABLES TO root;`
    -   Grants privileges only to future created objects

# 📅 06.12.2021 Api: Two ways of Api-Design

-   Two common approaches (see also REST vs RPC style - [link](https://blog.jscrambler.com/rpc-style-vs-rest-web-apis))
    -   REST ressource: `/accounts`
    -   Reified resources: `/create_account`
-   You can also combine the two
    -   `/create_account (for posting)`
    -   `/accounts (GET)`

# 📅 25.11.2021 InfoSec: Learnings about security

-   General rules
-   Build with security in mind right from the start
-   Build several layers of security in case one fails
-   Principle of least privilege
-   Prefer allow-lists over denylists
-   Do not reinvent the wheel
-   Threat Modelling
-   always involves product people and delivery team (and SME of InfoSec) -\> Shared understanding
-   iterative process (can also be done when new features are created)
-   Business Thread Modelling (High-Level approach)
-   artifact is a priotized list of threads -\> after that we have to ensure that our application is designed accordingly (see Application Threat Modelling)
-   As preparation: CIA triad, buiness understanding, Identify actors
-   CIA triad
    -   Confidentiality: Only authorized access of data
    -   Integrity: Data should be tampered/manipulated
    -   Availability: No downtime (e.g. hospitals)
-   Identifying actors (entities like services or people)
    -   best done by looking the workflows or already during inception
-   Identify assets (what can be compromised/stolen)?
-   How to manage threat?
    -   Risk register: Threat, Impact, Probablity, Severity (Im\*Pr), Mitigation
    -   Magic quadrant: Probablity and Impact -\> When it comes to prio, start with high probablity and impact
-   Application Threat Modelling
-   based on identified threat list in step one: what would the attacker do to achieve this threat? How does the application enable/prevent this?
-   Types of attacks (STRIDE)
    -   Spoofing (pretend to be someone else): Can an attacker gain access using a false identity?
        -   Example: [Sony Picture Hack](https://en.wikipedia.org/wiki/Sony_Pictures_hack) started with fake Apple Id Mail
    -   Tampering (e.g. inject script): Can an attacker modify data as it flows through the application?
        -   Example: [Samy worm](https://en.wikipedia.org/wiki/Samy_(computer_worm))
    -   Repudiation (e.g. remove traces of illegal actions): If an attacker denies doing something, can we prove he did it?
        -   Example: [Lotterie Incident](https://darknetdiaries.com/episode/101/), changing db before payout
        -   Example: Access on celeb profiles are tracked in federal agency for work
    -   Information Disclosure (e.g. stacktrace in the UI): Can an attacker gain access to private or potentially injurious data?
        -   Example: hacked binance account on crypto, you were able to see if a certain mobile number was used for account. First step for proceeding with SIM swap
        -   Example: Exposing stacktrace on UI
    -   Denial of Service Attack (DoS): Can an attacker crash or reduce the availability of the system?
        -   Example: Anonymous attacking police stations, governments, scientology or even childrens hospitals
        -   Example: Self-Made Dos, no circuit breakers in a distributed system
    -   Elevation of Privilege: Can an attacker assume the identity of a priveliged user?
        -   Example: Used in almost every major hack, using not patched vulnerabilities to e.g. become super using on host OS
-   How to manage threat?
    -   Data Flow Model: How does data change and what are the \'trust boundaries\'?
        -   trust boundary := one defined region where services trust each other (e.g. webbrowser is not in the same boundary as the backend). What is under your control - what are external entities
        -   each trust boundary is exposing a certain attack surface. Apply STRIDE here
        -   In a last step, think of risk mitigations
    -   Play [card game by owasp](https://owasp.org/www-project-cornucopia/)
    -   Attack Tree
        -   get into the role of an attacker
        -   always ask why the attacker is doing something, thus opening potential other ways of achieving this
        -   do not focus on the concrete techniques which might be deployed but more about the goals (and why)
        -   group those approaches in parent goals and then try to enrich the constructed tree (adding child or sibling)
        -   in a final step you should think where in the tree you can apply possible mitigations (start from bottom up). What is in your controll and what not? (Principle: Defense in depth - defend in multiple layers)

# 📅 25.11.2021 Pattern: Dealing with transactions in the world of microservices

-   Two-Phased Commits (2PC)
-   not acid (usually only eventually consistent, each microservice locking, executing)
-   distributed locking systen
-   only use for very short lived operations (introduces latency, because resources are locked)
-   Process
    1.  Voting Phase: Ask each are you able to complete the work? If so, lock rows and return ok to coordinator node
    2.  Commit Phase: Change will be made persitent (no atomicty, only eventual consistency)
-   Best Approach: Keep transactional logic in one microservice
-   Saga-Pattern
-   Idea: Each microservice has local transactions which trigger local transactions in other microservices (e.g. through queuing system)
-   If one local transaction fails some fixing transactions are back propagated (for cleanup or mitigation)
-   Type: Choreography
    -   Each microservice is keeping tracking of its state and notifies other dependent transactions
    -   Risk: Difficult to see relationships between microservices and risk of cyclic dependency
-   Type: Orchestration
    -   Central actor which is keeping track of the states (e.g. listening to a queue) and notifying which microservices have to perform which local transaction / fixing transaction
    -   Risk: Additional point of failure, requires new microservice to maintain

# 📅 24.11.2021 Git: When you clone a repo you do not want to push back to

-   `git remote -v`: List remotes if a repo
-   `git remote rm origin`: Remove remote of a repo

# 📅 24.11.2021 Database modelling

-   Logical/Relational (relationships, entities) vs. Physical (how it actually looks like with datatypes) model
-   best picks for postgres: pgModeler, Moon Modeller

# 📅 24.11.2021 UML: Tool for modelling sequence diagrams

-   PlantUml (also with IntelliJ Plugin and can be embedded in Confluence)

``` {.bash}
@startuml
Alice -> Bob: Pays money
Bob --> Alice: Gives ice cream
@enduml
```

# 📅 11.11.2021 IntelliJ: Make Maven work in IntelliJ

-   Look for crossed out POM, remove from ignored files list under gradle settings
-   In Maven Window, find root project and do clean/install
-   Right click on project folder maven\>generate sources helped to make annotations etc. working

# 📅 09.11.2021 Team: Reflections and learnings about **feedback**

-   **Feedback triggers**: When is it difficult to recieve feedback? (the Book \'Thanks for the Feedback\')
    -   Truth trigger: We feel that feedback is wrong, incomplete
    -   Relationship trigger: We feel person giving it is not trustworthy, competent -\> attention shifts to the person, away from the feedback
    -   Identity trigger: Feedback about parts we consider super important to our identity
-   **Types of feedback**
    -   Evaluation: Where you stand (assessment, ranking etc.) -\> Align expectations
    -   Appreciation: Relationship/Human Goals - \'we all have a common goal, you are helping us with that\' -\> Makes us feel good
    -   Coaching: Help someone learn, grow and change, ressource focused, concrete -\> Gives us sense of purpose
-   **How feedback is created**
    -   There is always a gap between what we think we present and what other people see

<p align="center"><img src="https://raw.githubusercontent.com/biocarl/img/34edba9d7e71c0887534bf0310ba0c137f59afbc/gap_map.png" width=400 /></p>

-   In the spirit of constructivism you do not understand
    -   their system
        -   their intention
        -   how they view things
    -   nor do you understand your own
        -   interpretations
        -   completeness of your data
-   Therefore, when you give feedback try to focus about the behavior and understand their intention first
-   "He said, when you're screwing up and nobody's saying anything to you anymore, that means they gave up. And that's a lesson that stuck with me my whole life. Is that when you see yourself doing something badly and nobody's bothering to tell you anymore, that's a very bad place to be. Your critics are your ones telling you they still love you and care." - Randy Pausch
-   Good exercise: Each person draws a picture and you swap with your partner and exchange feedback
    -   How did you feel as a giver? Was it easy? Did you use any specific techniques? Was your feedback incorporated in the drawing? Was your feedback listened to? Did you get the result you expected?\"
    -   How did you feel as a reciever?
    -   Learning: Some people really do not like drawing, think of different artefact or give them more preperation time to do the drawing (give 1 day to prepare)
-   there is also a concept of **feedforward**
    -   you yourself ask a person about something you want to have feedback on, usually before you expose that behavior you want to get evaulated. A good way of lower the barrier of getting into feedback since you select the person (comes down to trust) and the topic you want to have feedback on
    -   there is also a very nice form of feedforward

    <p align="center"><img height=400 src="https://raw.githubusercontent.com/biocarl/img/master/feedforward.jpeg" /></p>
    
-   Benefits of recieving feedback
    -   Acknowledgement: Often we see something which our teammate did well but we do not take the time to also communicate this to him. It is actually pretty nice if get to hear what you did well, maybe you want to get even better
    -   Sense of purpose: If you getting a feedback more often this is a perfect indicator that something might correspond to reality and I goes there is no one who does not like to be a person people like to work with -\> Motivation
    -   Identify blind spots
    -   Almost everyone loves receiving feedback, but hates giving it (especially the negative feedback, better to call redirecting feedback)
-   Joy of Giving feedback
    -   Reciprocity: First of all, a easy one - more from a game theory perspective: You like to have good feedback, so what you expect from others you should also deliver
    -   Feedback as a gift: We all like to grow and to get appreciated - a well placed feedback, leading to more understanding makes them super happy
    -   Opportunity to evoke change: If you have some small irritations you never reflected on but then bring them into contact -\> thus making you more productive
-   Instead of framing feedback as postive and negative, frame it as +/δ (for change)

# 📅 05.11.2021 workshop: Ideas to retro

-   Energizer: Find 10 common things as a team
-   Brainstorming: Find Good, Improve, Adventure Time (crazy, audacious ideas - do this at this end)
-   also celebrate good things (let people present the clusters)
-   Hide some small reference on the Mural/Jam-Board people have to find (like Wimmelbild)

# 📅 21.10.2021 Terms

-   Anti-Corruption-Layer Pattern: Create a layer to protect your domain: e.g. Player domain (in the facade it interprets what a Player can mean in other domains e.g. football or baseball player behavior)

# 📅 21.10.2021 microservice: Microservices 101

- Advantages
  - autonomous teams
  - diverse set of technologies
  - independent life cycle
  - easy to understand a single microservice
  - easy to compose services
- Migrate from monolith to microservices
  - tips for starters: first try decoupling a simple/decoupled function of a monolith
  - Avoid coupling back to the monolith
  - deploy early and then release
- Change patterns
  - Strangler Fig Pattern: Extract functionality from the egde of a system to a microservice Steps
    - Put proxy layer in front, intercept inbound call (does not work if logic lives deep inside the monlith)
    - Reroute traffic to new implementation
    - Delete old implementation
- Details
  - use this if you must not touch the monolith\'s code
  - when intercepting call you can do this via proxy or redirect, can even change the protocoll e.g. soap -\> rest
  - even though not preferred you can still call back to monolith if this allows for small extraction
  - you can also intercept response/request and just add something before/after it is processed by upstream/downstream services, called **decorating collaborator**
    - example a new field is added in the response which seperately calcukated based on other fields in the response
    - with this you also do not need to touch the orginal monolith
  - Branch by abstraction: Create abstraction over functionality you want to use and then easly switch over between old (code living in monolith) and new implementation (a http call to the microservice)
  - Parallel Run: Can be used in combination with the ones above: calling both implementations at the same time. Usually you have a validation to check if both implemenations work in the same way
  - Change Data Capture Pattern: Listen to database changes with microservices to add additional functionality

# 📅 21.10.2021 Networking 101

-   **VPC**: Virtual private Cloud - Pool of shared ressources
    -   in Google this is a global construct
    -   usually three implicit firewall rules
        -   block all incoming traffic
        -   allow all outcoming traffic
        -   allow all internal traffic
-   **Subnetwork** : Is a portion of the orginal IP range defined in a specific region
-   **Shared VPC** : A VPC accros projects on a org level
-   **NAT** : Network Address Translation - Allow multiple private IP adresses/actors to access internet through one or more public ip adresses, also used for port mapping
    -   if local device (with local IP in network) wants to access internet it would send package to NAT
    -   that NAT then stores request with local IP and target IP into NAT table and switches out local IP with public IP of router
    -   once reponse returns, NAT looks in the NAT table and looks up the local device it needs to forward the package to
    -   each entry in NAT table has a timestamp which timeouts to close the port for target IP after some time
    -   this is usually referred as SNAT, because connection established from source
    -   if you want to establish a connection from outside it is called DNAT (from destination), also called Port-Forwarding
-   **Gateway** : in context of VPC: Talk to other VPC, to internet or to on-premise O
-   **Proxy** : a intermediary service which acts on your behalf
    -   if traffic between your services and proxy layer is encrypted: VPN
    -   different types catageorized by functionality
        -   open proxy / forwarding proxy server
            -   *this is protecting/hiding the client (sending side)*
            -   If hiding client IP, often called Anonymous proxy, otherwise transparent proxy (by setting like `X-Forwarded-For`)
                -   **but** transparent proxy has another meaning:
                -   in the sense of inline proxy, forced proxy
                -   proxy just intercepts the traffic and nothing has to be configured from the client side (done by surrounding infra)
                -   a famous example is also a CDN
            -   different use cases
                -   **caching proxy**: reduce data transfer (in internal network), caching requests
                -   **filtering proxy**: typical org policies to not access social networks etc.
        -   reverse proxy
            -   *this is protecting/hiding the server (recieving side)*
            -   usually public exposed layer to the internet
            -   in case of cloud: forwards request from internet to server located in VPC
            -   different use cases
                -   for compression (see also spoon feeding, serving content to client directly)
                -   **load balancer** is a special case, not about identity but distributingload to several identical servers
                -   **api gateway** is a sophisticated load balancer: API can be configured dynamically
                    -   -   security: often has denylist, accepting only a certain amount of requests from one client etc.

                    -   -   scalability: backend can change, wheres public ip stays the same

                    -   -   performance: e.g. caching and compression
-   **Routes**: How to send traffic from one instance to a destination (in VPC or internet etc.)
    -   a route consists of a single destination prefix in CIDR format and a single next hop
    -   routing table stores those routes (sometimes also with distance etc.)

# 📅 19.10.2021 Unix: Insert clipboard into file without editor

-   `cat > out.txt`, will open input mode
-   insert clipboard and then `CRTL + C`

# 📅 07.10.2021 Data Engineering

-   **Shuffling**: Usually data is distributed, meaning data is in different kinds of places. To do an operation like GroupBy they have to reside in on place. The process of moving/centralizing data is called shuffling. ([source](https://www.coursera.org/lecture/scala-spark-big-data/shuffling-what-it-is-and-why-its-important-bT1YR))

# 📅 05.10.2021 How problems are solved (debug,fix,issues)

-   docker compose: run services seperately and then try things out from the container itself
    -   `docker-compose up SERVICE_A`
    -   `docker-compose run --entrypoint=bash SERVICE_B`
-   docker-compose: Container was crashing immediately.
    -   substituting entrypoint with bash and discovered that this is a line ending issue
-   GCP: Look at audited ressources logs for more specific failure analysis
-   docker: Append cat command after java entrypoint in dockerfile to print out some error log file
-   Look at the classes when reading a stack trace!
-   Paint a diagram
-   Use debugger, jump to exception
-   Invest much time in reproducing issue locally first

# 📅 05.10.2021 Docker Compose: Commands

-   if you want to prune volumes with docker-compose: `docker-compose down --volumes`
-   if you want to build with docker-compose: `docker-compose up --build`
-   if you want to copy file into container: `docker compose cp fileInHost serviceName:targetFile`

# 📅 05.10.2021 Docker: Commands

-   `docker build --tag my_new_image .` : build new image locally, run this in the same folder where Dockerfile is located
-   `docker run -it <image> /bin/bashc` : create container and shell in
-   `docker run -p <outer>:<inner> <tag>`: With port mapping
-   `docker-compose exec service-name-in-docker-compose sh`: shell into existing container via service name

# 📅 01.10.2021 Postgres: Commands

-   `\list` or `\l`: list all databases
-   `\c <db name>`: connect to a certain database
-   `\dt`: list all tables in the current database using your `search_path`
-   `\dt *.`: list all tables in the current database regardless your `search_path`
-   `SET search_path TO myschema,public;`: Set schema for session

# 📅 01.10.2021 Unix: Fork commands and put tasks into foreground again

-   fork command with `&` and see background tasks with `jobs` and get task into foreground with `fg`

# 📅 01.10.2021 Windows: Avoid that windows goes into hibernate/sleep mode

``` {.powershell}
param($minutes = 60)
$myshell = New-Object -com "Wscript.Shell"

for ($i = 0; $i -lt $minutes; $i++) {
  Start-Sleep -Seconds 60
  $myshell.sendkeys(".")
}
```

# 📅 01.10.2021 Docker: Prune volumes

-   sometimes docker [caches ressources even across projects](https://github.com/pydanny/cookiecutter-django/issues/1678), if there is some wired behavior you should prune the volumes
-   `docker system prune -a --volumes --force` (don\'t do this in prod)

# 📅 22.09.2021 Terraform: Basics

-   if resource is not updated you can `terraform taint` the ressource (get address by `terraform state list`)
-   sometimes you get a state lock - to resolve this do `terraform force-unlock ID`
-   if you want to track a resource via terraform which was initially not provisioned by terraform do `terraform import resource_type.identifier ID`.
    -   you have to add a resource definition with name ID, why is applied right after the import command
    -   resource~type~.identifier could be for example: google~pubsubtopic~.projects/{{project}}/topics/{{name}}
-   `moved {}` block helps you to rename a ressource (or move to a module) without recreating the resource

# 📅 17.09.2021 Fun: gitmoji

-   there is some conventions to make commit messages mor pretty with emojis - [link](https://gitmoji.dev/)

# 📅 16.09.2021 Database: Terms

-   Surrogate key, almost like a primary key

# 📅 14.09.2021 Windows: Lock/Unlock F1-12 keys

-   Press ESC + Fn to toggle

# 📅 10.09.2021 Consulting: Terms

-   SME: Subject matter experts

# 📅 09.09.2021 Terms

-   lift & shift: Move existing on premise applications to the cloud without modifying them
-   Roll Back the Database or Fix Forward?
    -   Rolling back is very time-consuming and complicated
    -   Fix forward is a lot quicker
    -   always ensure that migrationns

# 📅 08.09.2021 Python: Quick start with isolated environment

-   python3 -m venv venv && source venv/bin/activate
-   pip install -r requirements.txt
-   Use debugger: import pdb; pdb.set~trace~()

# 📅 08.09.2021 pact: How to do contract testing?

-   [source](https://www.youtube.com/watch?v=U05q0zJsKsU&list=PLwy9Bnco-IpfZ72VQ7hce8GicVZs7nm0i&index=1)
-   In a microservice context integration is hard
    -   all have to be in the same environment
    -   slow
    -   hard to parallelize
    -   hard to debug (in which service was it failing?)
-   One solution: Spec-First design
    -   e.g. with OpenApi spec
    -   Good communication tool
    -   Problem: When updating the spec to v2 - a lot of consumers are breaking now
-   Better solution: Consumer-driven contracts

# 📅 07.09.2021 Pattern: Outbox pattern

-   outbox pattern := Create events table which is then published as events e.g. with CDC
    -   also called Transactional outbox pattern
    -   Problem description ([source](https://microservices.io/patterns/data/transactional-outbox.html))
        -   Microservices do not exist in isolation and have to propagate own data changes to other services
        -   How do you make sure that you commit changes in application **and** propagate the changes? In theory the first part could go through but the seconds fails, then you have inconsistent state accross the system
    -   Why not using CDC aka just streaming each change without staging table, directly?
        -   advantage: do not bind consumer of the event on the implementation of the datatable, you have no controll what the event looks like
    -   Problem about a syncronous approach (just calling dependent services via Rest for instance):
        -   a lot of consumers to take care off
        -   service can\'t function without the other services (latency is determined by slowest dependent)

# 📅 07.09.2021 Learnings

-   Reconciliations run: Check if two data sources are in sync
-   staging tables: containing business data, prepared for being loaded by the application (cleaning/modification beforehand), only temporary
-   **change data capture (CDC)**: A set of design patterns to capture changes in a data source
    -   lacking re-playability: new service can\'t consumer old changes

    ```{=html}
    <!-- -->
    ```
    -   including
        -   timestamps
        -   version numbers
        -   log scanners which emit detected transactions as a change event

# 📅 30.08.2021 GCP CLI

-   Showing current running builds: `gcloud builds list --ongoing`

# 📅 30.08.2021 Monitoring

-   Micrometer: metrics collection facade, like SLF4J but for metrics
-   Spring Boot Actuator: provides common metrics and autoconfiguration
-   REST vs RPC?

# 📅 25.08.2021 Contract-First vs Code-First

-   Contract-First
    -   Autogenerate DTO from existing Open-Api definition
    -   what happens if a new swagger definition breaks existing contract?
        -   you use minor/major versions to avoid to automatically pull (since a new DTO definition can break the code
    -   (+) Have a final version which allows others to talk about it (perfect for non-technical people)
    -   (-) for having contract-first you can do a contract-testing and should not rely on Swagger/Open-API.
    -   (-) you need to update open-api definition in repositoriy manually if you change behavior in code
        -   but still you could automate publishing of code-first generated contract
-   Code-First
    -   Generate Open-Api defintion from code
    -   (+) The agile way. Specifying it is part of the processes and not some final version (as in contract-first), less work

# 📅 19.08.2021 Under the Covers of Spring Boot

-   [source](https://www.youtube.com/watch?v=jDchAEHIht0)
-   Two phases of scanning
    -   1.  User configuration (`@Component`, `@Configuration`, `@Controller` etc.) - enable by `@ComponentScan`
    -   2.  Auto configuration - enable by `@EnableAutoConfiguration`
            -   Only those things are configured which is not already configured in first step 1 (e.g. datasource)
-   JUnit
    -   `@Rule` annotation allows you reference a `TestRule` class which is setup/tearn down after before/after each test
        -   `TemporaryFolder`: Creates and deletes a temp folder for one test
        -   `OutputCapture`: Captures stdout and allows to do assertions on it

# 📅 16.08.2021 Security
-   oAuth2
    -   original goal: allow 3rd party applications to access users (e.g. google) data without having their password, it now rediects to the original service (e.g. google) which then returns a access token
    -   further advantage: also all first party apps are more secure because there does exist only one oauth server which has to be secured e.g. gmail login redirects to accounts.google. Also easier to refactor (e.g. 2f-auth) because there is only one server
    -   `client` is requesting a `token` at `authorization server` which in turn allows access `resource server` which is owned by `resource owner` (often you)
-   How to store passwords
    -   first only plaintext, then it was hashed, and then it was hashed with a salt (to avoid rainbow tables which hackers used to compare them with alreday hashed passwords. The salt ensures that everytime we have a new hash
    -   let spring decide on which passwords encoders to use([source](https://code-held.com/2021/05/15/spring-password-encoder/)): `DelegatingPasswordEncoder` will be updated according to best practice standards in security. Algorithm, salt etc. is encoded in the encoded string so it can also be updated dynamically while ensuring backwards compatibility (`Password Storage Format`)
-   Spring Security
    -   get UserDetails: `UserDetailsService`
        -   Spring security needs information what to check for authentication
        -   your Database and User representation is highly specific, a `UserDetailsService` abstracts this and only returns a `UserDetails` object

# 📅 12.08.2021 spring: Common data access abstractions
- **JDBC**: All Java persistence is built on this. Lowest level
- **JPA**: Agnostic way to do Java persistence without coupling your clients to Hibernate, etc.
- **Hibernate**: object-relational mapping solution for Java environment
- **Spring Data JPA**: Abstraction on top of Hibernate, e.g. no need to write DAO implementations
- **DAO**: Data Access Object, you only create the DAO interface with method heads and the rest will be implemented
- **DTO**: Data Transfer Object
  - Is never a POJO since usually a framework provides the external system side formatting, e.g. @Entity (for db), @JsonProperty (for REST/JSON response)
  - Decouple persistence models from API models: No messy attributes as @JSONIgnore, Mixing with persistence annotations, More difficult to create a Swagger out of it because you do not want to annotate your internal data model for the API description [source](https://stackoverflow.com/a/36175349)

# 📅 05.08.2021 terraform: More Terraform concepts
- `locals`: like actual variables to resuse the same expression in the same module
- first you need to enable certain api\'s for your project before you can create the ressources (`depends_on` needed)
- `null_ressource`: A block of coded executed on a trigger or depends on statement

# 📅 04.08.2021 gcp: Popular services
- source: [Google Glossary](https://cloud.google.com/terms/services)
- "Cloud Source Repositories": provides git version controll
- "Cloud Build": built environment and publish artifact somewhere
- "Cloud Logging": log aggregation with error reporting features, search for "logs explorer"
- "Cloud Run: run stateless containers on a fully-managed environment, also manages thinks like replicas etc.
- "Cloud Ressource Manager": Hierachical origanization of your Cloud resources, allows access controll and configuration settings
- "Service Networking API": Set's up subnetworks, vpc's, DNS-Record Sets

# 📅 04.08.2021 terraform: Terraform 101

- General idea
- automate manage your infrastructure: platform and services
- Steps
  - first: infrastructure provisioning: like ec2 instances,users, docker installation, network, security, pipeline
  - second: actual deployment
- Terraform is used for the first step
- Difference between Ansible and terraform:
  - Terraform: mainly provisioning tool
  - Ansible: only for configuration, more advanced/mature
- Managing existing infrastructure
  - create infrastructure
  - changes to infrastructure
  - replicating infrastructure (different environments)
- How does Terraform connect to it\'s providers?
  -  Elements
   - CORE figures out based on: 1) Local TF-Configs 2) State
   - PROVIDERS: Like AWS, Kubernetes etc. with each having ressources
  -   Core then creates a execution plan to apply through providers
- Commands
  - `refresh`: Query providers to get current state
  - `plan`: Creates an execution plan based in state
  - `apply`: Execute plan
  - `destroy`: Remove all ressources/infrastructures (e.g. for demo env)
- Concepts - taken from [Terraform-Glossary](https://www.terraform.io/docs/glossary.html)
- `ressource`: Representation of a provider ressource Terraform will create once declared
- `data`: Retrieve data outside of Terraform, supplied to `ressource`
- `module`: collection of Terraform configurations (can be parametrized via `variable`), a module has to be called by some other configuration in order to be applied to the state
- `variable`: Key/Value pairs which can be injected into a module which is the used there (child module retrieves from parent module), Note: Never put hard-coded values in here. Also can be accessed via \"\${var.name}\" in all the modules
- `backend`: Defines e.g. where the state is stored (allowing colloboration)
- `output`: Module exporting data (can be shown to user or used by other module)

# 📅 29.06.2021 mockito: How to mock deeply nested object?
- Verification only works with the last mock in the chain
- Mock deeply nested object: `RETURNS_DEEP_STUPS`
```java
@Mock(answer = Answers.RETURNS_DEEP_STUBS)
Object objectMock;
```

# 📅 29.06.2021 team: Agile routines I like
-   Lake of feelings in [english](https://github.com/biocarl/img/blob/master/Lake%20of%20Feelings-english.png) and [german](https://github.com/biocarl/img/blob/master/Lake%20of%20Feelings.png)
-   Inbox
-   Walking the board
-   Sign-Ups

# 📅 29.06.2021 workshop: retro: Tipps for facilitating retros's
-   Let people room to speak
-   Don't ask if it is ok what you are doing (you are the facilitator)
-   Don't ask closed question
-   Make people speak as soon as possible
-   Do less items

# 📅 29.06.2021 intellij: Shortcuts
-   Use F2 to navigate to next error (Fn + f2)
-   Command E: Recent files
-   2 x CTRL: Run script from anywhere
-   Command + Shift + Enter: Fancy autocomplete
-   Control + T: See all refactor commands
-   Command P -> show parameters
-   Multiple cursors ([source](https://stackoverflow.com/a/55221176))
    -   Go to vim emulation settings and set command G to Intelli
    -   Maybe set to hex input:
    -   <Control G>: highlight next match as multiple cursors
    -   <Control + Command + G>: Highlight them all at once

# 📅 29.06.2021 vim: Folding commands
-   close single fold: `zc`
-   open single fold: `zo`
-   close all folds: `zR`
-   open all folds: `zM`

# 📅 29.06.2021 Spring: Actuator: How to read out the heap from the jvm?
- Available heap: `http://localhost:7979/metrics/jvm.memory.max?tag=area:heap`
- Used heap space: `http://localhost:7979/metrics/jvm.memory.used?tag=area:heap`

# 📅 29.06.2021 knowledge: How to find things aka. Data acquisition
-   Cloudsearch
-   Jira tickets from other teams
-   Company Documentation (tech, confluence,...)
-   Github
-   Chats/G-Groups
-   Always return to the initial onboarding documents - you might miss things

# 📅 29.06.2021 jira: How to format text
-   Jira-Formatting: [link1](https://jira.atlassian.com/secure/WikiRendererHelpAction.jspa?section=advanced) and [link2](https://jira.atlassian.com/secure/WikiRendererHelpAction.jspa?section=advanced)

# 📅 29.06.2021 git: Useful bash/zsh alias
-   git push upstream: `gpsup`
-   git checkout -b: `gcb`
-   Git commands for undo changes
-   git reset --hard
-   git clean -f

# 📅 29.06.2021 unix: Edit and execute last command
-   edit and execute last command: `fc`

# 📅 29.06.2021 docker: Useful docker commands
-   List CPU's: `docker ps -q | xargs  docker stats --no-stream`
-   Run local docker container: `docker run --publish 8090:8080 --env SPRING_PROFILES_ACTIVE=local IMAGE`
-   Delete all docker containers originating from one image: `docker rm -f $(docker ps -a -q  --filter ancestor=postgres:13)`
-   delete all docker containers: `docker rm -f $(docker ps -a -q)`

# 📅 29.06.2021 kubectl: Useful kubectl commands
-   list the logs of a previously stopped pod: `kubectl logs --previous`
-   do something with a set of grep'ed pods: `kubectl get pods | grep shard |  cut -d ' ' -f1 | xargs echo`
-   even better, you can use `up` ([github](https://github.com/akavel/up)), to check the results

# 📅 29.06.2021 postgres: Useful postgres commands
-   Show foreign tables and foreign servers: `\des+` and `\dE[S+]`
-   where logs are stored: `SHOW log_directory;`
-   Make a long running query: `select pg_sleep(5 * 60);`
-   Count connections: `select count(*) from pg_stat_activity;`
-   Sample data (for not to big table): 2. `COPY  (select * from table ORDER BY random() LIMIT 10000) TO '/home/postgres/export_10k.csv' CSV HEADER;`
-   List indexes: `select * from pg_indexes where table not like 'pg%';`

# 📅 29.06.2021 postgres: Sharding with fdw and pl-proxy
-   fdw does not parallelize shard access
-   uses flyway placeholders (via env variables or setting placeholders via fluid config)

``` {.sql}
create table table (
    name char(64) NOT NULL,
    id int NOT NULL,
) PARTITION by HASH (id);

CREATE EXTENSION IF NOT EXISTS postgres_fdw;

CREATE SERVER IF NOT EXISTS shard1 FOREIGN DATA WRAPPER postgres_fdw OPTIONS (dbname '${shard1_db_name}', host '${shard1_host}', port '${shard1_port}');
CREATE SERVER IF NOT EXISTS shard2 FOREIGN DATA WRAPPER postgres_fdw OPTIONS (dbname '${shard2_db_name}', host '${shard2_host}', port '${shard2_port}');

CREATE USER MAPPING IF NOT EXISTS FOR PUBLIC SERVER shard1 OPTIONS (user '${shard1_user}', password '${shard1_password}');
CREATE USER MAPPING IF NOT EXISTS FOR PUBLIC SERVER shard2 OPTIONS (user '${shard2_user}', password '${shard2_password}');

CREATE FOREIGN TABLE table_shard1 PARTITION OF table for values with (modulus 2, remainder 0) SERVER shard1 OPTIONS (table_name 'table');
CREATE FOREIGN TABLE table_shard2 PARTITION OF table for values with (modulus 2, remainder 1) SERVER shard2 OPTIONS (table_name 'table');

CREATE EXTENSION IF NOT EXISTS plproxy;

CREATE SERVER IF NOT EXISTS shards FOREIGN DATA WRAPPER plproxy OPTIONS (
    p0 'dbname=${shard1_db_name} host=${shard1_host} port=${shard1_port} application_name=plproxy user=${shard1_user} password=${shard1_password}',
    p1 'dbname=${shard2_db_name} host=${shard2_host} port=${shard2_port} application_name=plproxy user=${shard2_user} password=${shard2_password}'
    );

-- needed otherwise you can't provide username/password in server definition above
CREATE USER MAPPING IF NOT EXISTS for public SERVER shards OPTIONS (user '${shard1_user}');

CREATE OR REPLACE FUNCTION get_entry_by_name(p_name varchar(64))
    RETURNS TABLE (name char(64), id int) AS $$
    CLUSTER 'shards';
RUN ON ALL;
SELECT name, id FROM table WHERE name = p_name;
$$ LANGUAGE plproxy;
```

# 📅 29.06.2021 kubernetes: You can patch a deployment and also inject spring variables like so
-   [source](https://github.com/spring-projects/spring-boot/wiki/Relaxed-Binding-2.0#lists-1)
- `kubectl patch deployment $DEPLOYMENT --patch "$(cat sharding-patch.yaml)"`

# 📅 25.06.2021 docker: Change local host reference to maschine host in docker image
- `docker exec -u 0 $CONTAINER /bin/sh -c 'sed "s/127.0.0.1/$(dig +short host.docker.internal)/g" /etc/hosts > tmp.txt && cat tmp.txt > /etc/hosts'`

# 📅 11.06.2021 git: Show previous stashes
- `git stash show -p stash@{3}`

# 📅 11.06.2021 java: Collectors and teeing operator
-   Combine two collectors
``` {.python}
HashMap<String, Employee> result = employeeList.stream().collect( 
                        Collectors.teeing(
                                Collectors.maxBy(Comparator.comparing(Employee::getSalary)),
                                Collectors.minBy(Comparator.comparing(Employee::getSalary)),
                                (e1, e2) -> {
                                    HashMap<String, Employee> map = new HashMap();
                                    map.put("MAX", e1.get());
                                    map.put("MIN", e2.get());
                                    return map;
                                }
                        ));
```

# 📅 11.06.2021 postgres: How to speed up index creation?
-   Speed up index creation and maintenance work related processes
`SET maintenance_work_mem TO '1000 MB';` `SET max_parallel_maintenance_workers TO 5;`

# 📅 11.06.2021 kubernetes: Useful commands
-   Shell into db
`kubectl exec -it podname bash` `psql -U postgres -d db_name` // -c \"Direct string\" and -f \"Load from file\"
-   Edit deployment files in prod
`kubectl edit deployment DEPLOYMENT_ID` Sometimes needed `kubectl rollout restart deployment DEPLOYMENT_ID`

# 📅 11.06.2021 postgres: What is one disadvantage of using partitioning?
-   if a lot will impact query planner performance (over 500)
-   there are not global unique constraints, only uniqueness in a partition can be guaranteed
-   [Course](https://www.udemy.com/course/postgresql-high-performance-tuning-guide/) you want to take

# 📅 11.06.2021 GSuite short links
-   Docs \>\> create and collaborate on documents
`docs.new | doc.new | document.new`
-   Sheets \>\> create and collaborate on spreadsheets
`sheets.new | sheet.new | spreadsheet.new`
-   Slides \>\> create new powerful presentations
`slides.new | slide.new | presentation.new | deck.new`
-   Forms \>\> create forms, registrations, surveys and quizzes
`forms.new | form.new`
-   Calendar \>\> schedule a new event
`cal.new | meeting.new`
-   Meet \>\> make video conferences and share your screen
`meet.new`
-   Jamboard \>\> collaborate in real time on a digital whiteboard
`jam.new`
-   Sites \>\> create a website to share info with others
`site.new | sites.new | website.new`
-   Diagrams \>\> create, edit, and share diagrams (formerly known as draw.io)
`diagram.new | diagrams.new`
-   Keep \>\> create, edit, and share notes
`keep.new`

# 📅 30.04.2021 postgres: How to use Postgres EXPLAIN

-   What it is
-   executed plan generated by the optimizer
-   Parameters
-   `ANALYZE`: Be aware: Does also executes the query!
-   `BUFFERS`: works only together with ANALYZE, shows what buffer is used in each step
-   `VERBOSE`: Print each step in the execution plan
-   `SETTINGS`: Print all performance-relevant parameters which are different from their output

# 📅 24.03.2021 postgres: Postgres Performance Optimization

-   Tablespaces := Are the way to tell the Postgres server where to place the physical files for SQL objects.
-   Partitoning your table is also good since you can deploy "multiple autovacuum workers on the same logical table"

# 📅 16.03.2021 postgres: Roadmap for sharding

-   [source](https://www.youtube.com/watch?v=C4GJAjUcAtg)
-   Approaches
    -   Application-side sharding
    -   PL/Proxy: Remote procedure calls between databases (used by netflix)
    -   Postgres-Forks: Postgres-XC/XL, with distributed queries implemented (heaviliy modified)
    -   Citus: Postgres-Extension (heaviliy modified)
    -   Not postgres based, like hadoop
-   Replicated tables
    -   Small dictionaries you would have repliacted on each shard since it is quicker to look up and you do not need to do costly joins
-   Streaming replication
    -   Each shard will have replicated tables from other shards (shardman us doing this)

# 📅 09.03.2021 tracing: Basics of distributed tracing
-   Why?
  -   increasingly more distributed infrastructures
  -   microservices in isolation are easy to manage and understand but complexity arises with interaction with its environment (distributed computing)
  -   need for increasing visibility across teams
  -   identify bottlenecks in the system (e.g. adaptive paging in Zalando)
    -   global health of the system/detect root cause of a problem in a system
-   What?
  -   is tracing a request accross multiple systems
  -   tracing is a bunch of log messages which can be correlated together through a correlation id
  -   distributed tracing starts with one request and following the flow other systems will do operations on it resulting in other traces, which itself is segmented in spans, unique actitivies performed by the system
  -   spans can fork into child spans (for instance parallel processes) resulting in a span tree which in its totality represents the whole trace
- Components
  -   **Instrumentation**: The process of collecting data (a lot of automated tools)
  -   **Trace context**: You need a unique ID passed along with timestamp to reconstruct the order
  -   A trace contains
      -   spans (with component, operation, duration, other metadata)
      -   errors
  -   **Analysis and visualization**: Frontend of telling the story of one trace. Standards like Opentracing/OpenCensus create a interface between metric collection (instrumentation) and frontend/analysis solutions
  -   Observability: "Observability lets you understand why something is wrong, compared with monitoring, which simply tells you when something is wrong."
  -   Adaptive Paging
    -   if there is one service down you will have a christmas tree (all components fire alarms), all incident teams will try to solve the issue but usually only one team can solve this (creates alarm fatigue)
    -   solution, page the team closest to the problem
-   **ingress operations**: the first operations handling external requests from outside that service (starting out a trace)
-   **egress operations**: are those operations that call out to external services (ending the trace of a single service)

# 📅 25.02.2021 postgres: General concepts

-   Views := A named query, usually combines several base tables but does not store extra data (vs materialized view)
  -   useful to wrap complex queries
    -   good for granting users only a subset of different base tables
    -   consistent abstraction layers even if underlaying base tables change
-   Stored procedures := Some kind of functions you can define to do complex operations in a batch
  -   you can define control flows like if etc.
-   Elasticity := Describes the flexibility how a distributed database can adapt to changes
  -   changes could be adding/removing nodes or data models (which is rather fix for relational databases)

# 📅 23.02.2021 Sharding and Foreign Data Wrapper in Postgres

-   Sharding is just a view to a external table, but looks like a local table
-   Parameters required:
    -   foreign server
    -   user mapping
    -   create a table: need to define how the foreign table looks like ok the remote side (but there is also the IMPORT FOREIGN SCHEMA option)
-   Facts
    -   there is always a head node, with all the fdw pointing to different shards (sometimes also called: data and coordinator nodes)
    -   the head/coordinator node is recieving the query is doing the planning and offloading analysis and queries to shards
    -   in the same way there is also the concept of parent and child transactions, same is the case for transactions (child will rollback, if parent does rollback)
    -   for high traffic we can have several coordinator nodes easliy since those nodes are stateless, all data is stored on the data nodes
    -   JOINS are done on the master, all the data has to be transferred therefore make sure you push where clauses down -\> seq scans can run on each shard?
        -   **Enabling parallelism on the coordinator**
            -   With PostgreSQL 9.6 [parallel queries](https://www.postgresql.org/docs/10/parallel-query.html) were introduced
            -   When optimal will create query plan (which is a [tree](https://tatiyants.com/postgres-query-plan-visualization/)) containing a gather/gather merge node which contains a single plan which is then executed in paralell
            -   This is done by spawning a bunch of background workers (including a leader which is reponsible of gathering the data)
            -   Gather nodes do not care about the ordering of the tuples generated by the workers and the leader merges them as they come, a merge gather node means that all workers and the leaders cares about the ordering
            -   gather merge nodes were added with v10, no need to have a parent sorting node anymore if you are interested in the order
            -   queries against several fdw are not parallized (current [state](https://www.postgresql.org/docs/12/parallel-safety.html)), each partition is scanned one after another - although there exists some [unofficial patch](https://github.com/swarm64/parallel-postgres-fdw-patch), [another one](https://pgxn.org/dist/pmpp/doc/pmpp.html), see also `IsForeignScanParallelSafe`
    -   It always inserts to whole table on the foreign server if this is the foreign table definitions (there are no defaults)
    -   you you run ANALYZE on the local system it will collect stats on the foreign system and bring them back to local
    -   Use presharding (read more \[[here](https://redis.io/topics/partitioning#presharding))
    -   Still do partitioning on shards, small tables are always good since it helps you to keep the index small or potentially even not needing one (seq scan is faster, no need to build b-tree and not random access)
    -   You can also fire procedures on the foreign server for example before every insert
-   About connections
    -   there is not connection pooling for the fdw in place, meaning if you have 12 incoming connections and 10 shards, your postgres backend has potentially 12\*10 outgoing connections
    -   but outgoing connections are cached (same connection is used for the incomming connection) (see [difference](https://stackoverflow.com/questions/5095884/what-is-the-difference-between-caching-and-pooling#:~:text=The%20distinction%20is%20usually%20drawn,See%20this%20explanation.&text=Caching%20usually%20refers%20to%20holding,of%20the%20value%20is%20expensive).))
    -   `fetch_size` is the number of rows to be transfered from master node to shard in one batch (100k performs well)
-   About backups
    -   doing backup of every slave/shard
    -   if there is transactions over several shards WAR based backup might be not that easy since consitency is key here
-   Current state of fdw
    -   lacks support for INSERT statements with an ON CONFLICT DO UPDATE clause
-   Useful commands for postgres
    -   `EXPLAIN (verbose) command` shows the also commands executed on foreign server
-   Useful Sources
    -   this [video](https://www.youtube.com/watch?v=3JQrfgb3Av0)
    -   about a [elastic postgres solution](https://swarm64.com/post/scaling-elastic-postgres-cluster/)
    -   from gitlab [blog](https://about.gitlab.com/handbook/engineering/development/enablement/database/doc/fdw-sharding.html)

# 📅 16.02.2021 postgres: Sharding and data structures

-   Table scans
  -   INDEX SCAN: Go over index b-tree and afterwards potentially over heap if not available in non-key columns. Still can be quite expensive since fetching from Heap is a random access operation (which seq scan is not)
    -   INDEX ONLY SCAN: Like above but everything you need is included in non-key cols (no HEAP needed)
    -   BITMAP SCAN: First creates a bitmap of all indices who fufill the predicate and then bundles the heap access to not needing to much random access (working with offsets)
    -   SEQUENTIAL SCAN: The classic full table scan
-   Sharding
  -   Why sharding in the first place? Indicies grow large -\> longer queries -\> more cpu/memory
    -   Unless your sharding field is a seq key you will need to ensure conistent hashing
    -   Difference to horizontal sharding: it is still the same database, but different tables or even schema, client has to know those
    -   Pros: Horizontally easy to scale + Security (e.g. a user only has access to one shard)
    -   Cons: Complex for client to decide to which shard to talk to, how to deal with transactions which impact two shards at the same time? Rollbacks are very hard. Schema changes are hard. Joins across shards are slow. If key you are looking for is not sharding field it is very slow because you have to hit all shards
-   Interesting thoughts
  -   Why do we have one billion rows in the first place? Can you design your data model differently?
    -   What is the read/write ratio and what are the access patterns?
-   Vertical partiting in postgresql works out of the box - client does not have to worry
-   Sharding is especially usefull if there are many connections/clients to one service and it also get\'s a CPU/Memory problem
-   but for this you can also get some read replicas (but only if you don\'t write a lot)
-   Partitions still support transactions
-   Sharding has no ACID transactions
-   Re-Sharding is very complicated (because all client has to adapt when you have application layer sharding)
-   YouTube has introduced a service layer before it vitess.io

# 📅 15.02.2021 postgres: Performance considerations
-   You don\'t need heap fetches if you just select the index (super fast but useless)
-   Always avoid full table scans
-   For looking at the details of a query always do explain analyze QUERY
-   LIKE statements will always trigger a full select because b-tree can\'t be scanned on partial string
-   key column: the index itself, non-key column: Include the value in the index itself so that you don\'t have to jump to the location of the whole row

# 📅 23.10.2020 mongodb: MongoDb 101

-   Setting up mongo db locally
    -   docker pull mongo
    -   docker run -p 27017:27017 -d mongo
-   Setting up mongo shell
    -   brew install mongodb-community-shell
    -   brew tap mongodb/brew
-   Shell into local mongodb
    -   mongo \"<mongodb://localhost:27017>\"
-   List all databases
    -   show dbs
    -   use local

# 📅 23.10.2020 queues: Deliver at least once principle

-   Messages emmited can be duplicated

# 📅 23.10.2020 queues: Dead letter queue

-   Store messages which are not valid in a separate place while allowing to the main queue to continue. Usually messages on a dlq are not retried

# 📅 09.10.2020 pandas: Rolling Window

-   Do a rolling window which is vectorized

``` {.python}
df["result"] = (
    df.groupby("date")
    .rolling(window=7, min_periods=1) # will try to find at least 1 non-nan value
    .mean(skipna=True)
    .shift((-1 * window) + 1) #trick to go backwards
    .reset_index(drop=True)
)
```

# 📅 09.10.2020 pandas: Melting

-   Convert columns into row values

``` {.python}
pd.melt(df, id_vars=["week"], value_name="items", var_name="country")
# id_vars: variables which stay as such
```

# 📅 09.10.2020 bash: A bash script for running functions

-   Source: @emilyagras
-   bash script.sh run flag

``` {.bash}
   #!/usr/bin/env bash
   __run() {
     if [ "$1" == "flag" ]; then
      echo "Hello! 🤓"
      exit
    fi
  }
# Using the code below, you can create any new function with two underscores (__hello-world) and it
# will be accessible as an argument for this script like: ./run hello-world
validate_args() {
  acceptable_args="$(declare -F | sed -n "s/declare -f __//p" | tr '\n' ' ')"

  if [[ -z $1 ]]; then
    echo "Must provide an argument"
    echo -e "Available commands:\n$(declare -F | sed -n "s/declare -f __/ - /p")"
    exit 1
  fi
  if [[ ! " $acceptable_args " =~ .*\ $1\ .* ]]; then
    echo "Invalid argument: $1"
    echo -e "Available commands:\n$(declare -F | sed -n "s/declare -f __/ - /p")"
    exit 1
  fi
}

CMD=${1:-}
shift || true
if validate_args ${CMD}; then
  __${CMD} $@
  exit 0
fi

```

# 📅 07.10.2020 vim: Use vim in unix pipe to do linewise operations

``` {.bash}
#vim.sh
vim - -esbnN -c "% $1" -c 'w!/dev/stderr|q!' 2>&1 >/dev/null # % denotes when using norm will be applied on each line
#usage:
cat source.txt | bash vim.sh "% norm dt[xf,xf]xwwdfnr " | bash vim.sh "g/>/d"
```

-   [source](https://blog.robertelder.org/use-vim-inside-a-unix-pipe-like-sed-or-awk/)

-   (vim-intelliJ) Use cowsay in IntelliJ

``` {.bash}
#cowsay
read output
cat <<EOF
-------$output
-------$parameters
EOF
#usage:
:<1,>!bash cowsay "parameter"
```

-   (vim-intelliJ) Use norm and g command in IntelliJ

``` {.bash}
#vim

#!/bin/bash
command=$(echo $@) # Catch parameters
while IFS= read -r line; do # Catch stream
       printf '%s\n' "$line" | vim - -esbnN -c "% $command" -c 'w!/dev/stderr|q!' 2>&1 >/dev/null # % denotes when using norm will be applied on each line
done

#usage:
'<,'>!./vim g/if/norm I---
```

# 📅 01.09.2020 pandas: Pandas merge and relational algebra

-   `on`: the column names to use for alligning the rows (has to be in left/right df)
-   `left_on/right_on`: as above but to use if they are different
-   `left_index/right_index`: as above but use the index as join key
-   `how`: specifies how to determine which keys are to be included in the resulting table
    -   `left` Use keys from left frame only
        -   Can result in several rows with the same key if the right side has several of those keys
        -   Can result in nan cells if the keys are only present on the left side and not on right side
    -   `right` Use keys from right frame only
    -   `outer` Use union of keys from both frames
    -   `inner` Use intersection of keys from both frames
-   `suffixes`: Overlapping columns which are not part of the keys are suffixed (tupel for left and right)
-   if there are non-uniqs on both sides it results in a cartesian product of both

# 📅 01.09.2020 data: Tidy Data

-   Denotes the concept of having a data matrix whereas each row is a observation and each column a variable and each cell a value.
-   Using the format makes column-wise calculations and combining data much easier

# 📅 01.09.2020 pandas: Cookbook examples

``` {.python}
# If condition matches assign 555 to the columns BBB, CCC
df.loc[df.AAA >= 5, ['BBB', 'CCC']] = 555
# Alternative: operates on bool series
df.where(df_mask, -1000)
# Filter dataframe by multiple criteria
Crit1 = df.AAA <= 5.5
Crit2 = df.BBB == 10.0
Crit3 = df.CCC > -40.0
AllCrit = Crit1 & Crit2 & Crit3
# Use dictionary to create a new column
categories = {1: 'Alpha', 2: 'Beta', 3: 'Charlie'}
df[new_cols] = df[source_cols].applymap(categories.get)
```

# 📅 09.08.2020 pandas: Working with data frames

-   When you want to operate on a bunch values in a series you can use this notation
-   It seems to be a shorthand for apply

``` {.python}
# Example for replacing the whitespaces of all column names
df.columns.str.replace(' ','_') # Returns a series with updated column names (you just have to reassign it)
# A more common case - filtering
df.column1.str.contains("Hallo") # Returns a series of bools which then can be used as a mask
```

# 📅 09.08.2020 pandas: Convert a catamorphic function to a homomorphic one

-   A function like `sum` acts as aggregator, if you want to maintain structure you can call the function like `transform('sum')` so it will pad cells with the same result
-   Very useful if you do something like `orders.groupby('orderid').itemprice.transform('sum')`, the result will have the same length as orders

# 📅 08.08.2020 python: Use named subgroups and go functional in python

-   By naminging subgroups \`(?P\<name\>+̣)\` you can return a \`groupdict\` containing \<name,match\> pairs.

``` {.python}
dic_raw = open('data/cedict_ts.u8').readlines()
spec = re.compile("(?P<traditional>\w)\s(?P<simplified>\w)\s\[(?P<pinyin>.+)\]\s\/(?P<english>.+)\/$")

list(map(lambda line: spec.match(line).groupdict(),
        filter(lambda line: not re.match(r"^[#|%]", line) and spec.match(line), dic_raw)))


# file=decdict_ts.u8
# 
# #! date=2020-08-08T07:57:03Z
# #! time=1596873423
# 龐雜 庞杂 [pang2 za2] /enormously complex/a vast jumble/
# 龑 䶮 [yan3] /high and bright/
# 龒 龒 [long2] /old variant of 龍|龙[long2]/
# 龔 龚 [Gong1] /surname Gong/
#


```

-   Output

``` {.python}
[{'traditional': '㩐',
  'simplfied': '㩐',
  'pinyin': 'den4',
  'english': 'variant of 扽[den4]'},
  {'traditional': '㩗',
   'simplfied': '携',
  'pinyin': 'xie2',
  'english': 'old variant of 攜|携[xie2]'}]
```

# 📅 08.07.2020 clojure: Use merge-with for conflicting hash-map merges

``` {.clojure}
(merge-with + {:a 1  :b 2} {:a 1  :b 2 :c 3})   
;; output {:c 3, :a 2, :b 4}
```

# 📅 03.06.2020 clojure: Operate on only one of the key-value pairs in a hash-map

``` {.clojure}
(reduce-kv #(assoc %1 %2 (flatten %3)) {})
```

# 📅 02.06.2020 clojure: Use matching groups when replacing with regex

``` {.clojure}
(str/replace % #"\{:([^\s]+)[^{^}]*\}" "<$1>")
;; input:  喝 act-on {:drink 茶 饮料 啤酒 水 牛奶}
;; output: 喝 act-on <drink>
(str/replace "<subject><predicate><object>" #"\<([a-z]+)\>" "<$1>&lt;$1></$1>")
;; This is very useful if you want to quote a xml element and at the same time not
```

# 📅 28.05.2020 chrome: Make content of any website editable

-   `document.designMode = 'on'.`
-   This allows you to edit content of a website directly in the view without manipulating the dom tree via for instance the Chrome Developer Tools

# 📅 16.05.2020 unix: The zsh shell allows you to write to your own prompt!

-   `print -z echo Hello world`
-   I can see how this becomes very useful if you load syntax files and edit them before running them
-   You would put something like this in your `.zshrc`

``` {.zsh}
function edit(){
   print -z $(cat $1)
}
```

``` {.bash}
$ edit syntax
```

-   You can also try to reproduce this in other shells - [see stackoverflow ](https://unix.stackexchange.com/questions/213799/can-bash-write-to-its-own-input-stream/213821#213821)

# 📅 15.05.2020 english: Name of modifier keys

-   `Strg` (Steuerungstaste) 🇩🇪 == `Ctrl` (Control-Taste) 🇨🇭/🇬🇧
-   `⇧` == (Umschalttaste) 🇩🇪 == (Shift) 🇬🇧
-   `Alt` == (Alttaste) 🇩🇪 == (Alt key) 🇬🇧
-   `⇪` == (Feststelltaste) 🇩🇪 == (Caps Lock) 🇬🇧
-   `↹` == (Tabulatortaste) 🇩🇪 == (Tab key) 🇬🇧
-   `Fn` == (Fn-Taste) 🇩🇪 == (Fn key) 🇬🇧

# 📅 15.05.2020 english: parameter vs argument

-   parameter := is a variable in a method definition
-   argument := is the data you pass into the method\'s parameters when calling the method

# 📅 15.05.2020 english: Names of english symbols

-   \"round brackets\" `( )`
-   \"square brackets\" or \"box brackets\" `[ ]`
-   \"curly brackets\" `{ }`
-   \"angle brackets\" `< >`
-   (English) Other key symbols
-   **\~** Tilde
-   **\`** back quote
-   **!** sometimes bang
-   **\#** sharp, hash
-   **°** degree
-   \*^\*^ caret or circumflex
-   **&** ampersand

\- \* asterisk, star

-   **-** hyphen, minus, dash
-   **:** colon
-   \' apostrophe, single quote
-   **\<** sometimes less than
-   **.** period, dot, full stop

# 📅 14.05.2020 git: Initalize your `.gitignore`

-   `ls -a . >> .gitignore` Why did I take so long to start doing this? 🤔

# 📅 13.05.2020 unix: Several commands

-   (textutil) Resolve wired encoding issues of text/html files
-   `textutil -convert txt *.html` batch processing (OSX)
-   (xargs) How to use xargs with a consecutive actions afterwards (like pipe)
-   Snippet: How to concat a large (!) number of textfiles
-   `find . -name "*.txt" -print0 | xargs -0 -I {} sh -c "echo {}; cat {} >> total.txt".`
-   (awk) Use ranges to only iterate over lines withing a certain `start` and `end` pattern
-   `awk '/start/, /end/ {action}'.` Can match several times
-   (awk) The `next` statement allows to go into the **else** case of the pattern match
-   `awk '/pattern/ {print $2;next} {print}' stripped.txt`
-   (vim) Show whitespace characters in vim
-   Toggle with `:set nolist//list`

# 📅 12.05.2020 unix: More commands

-   (awk) Group matches inside gawk (this does not work in the mac version)
-   `brew install gawk`
-   `gawk { match($0, /#([0-9]+)/, arr); print arr[1] }`
-   (sed) A how to split sentences in seperate lines
-   `sed 's/[.!?]  */&\n/g' file.txt` where the `&` is the back reference to the match

# 📅 11.05.2020 unix: awk commands

-   (awk) Basic commands
-   1.  Basic structure: `pattern {action}`
-   When the pattern matches the action is executed.
-   Either one of them can be ommited, resulting implicitly in a) in match all lines (default pattern) b) print whole line (default action)
-   `{print $2}` print second row of each line (implicit pattern)
-   `$3 == 10` print whole line which has 10 at the third row (implicit action)
-   1.  Built-in variables
-   **NF** := number of fields of current line
-   **NR** := nth line
-   Default delimiter is whitespace (for splitting (**FS**) and joining (**OFS**))
-   You can even change the definition of what a line is: **RS** - defaults to \"`\n`{=latex}\" (with the join analog **ORS**)
-   2.  Syntax for patterns
-   `/regex/` without \$, results implicitley in \$0 (whole line)
-   `$1 ~ /regex /` runs the regex on first column of the line
-   `NR=10, NR=20` example for ranges (executes action on lines 10 to 20)
-   3.  Some useful actions
-   String functions like gsub, substring
-   `{gsub (/pattern/, "to subsitute"); print}`
-   String concat: `{print $1 $2}` -\> one string \|\| `{print $1,$2}` -\> joined with OFS
-   You can execute external commands: `awk /Hallo/ {system ("touch " $2)}` text.txt
-   Append prints to specific files `{print $0 >>"file.txt"}` // pipe also works
-   we can define global variables: `{chars += length; print chars}`
-   Extended structure: `BEGIN {action} pattern {action} END {action}`
-   `awk '{chars += length;print} END {print "Total amount of chars: ",chars}' text.txt`
-   4.  Equivalent unix commands
-   `cat file.txt` == `awk '{print}'` (defaults to print \$0)
-   `grep /pattern/ file.txt` == `awk '/pattern/'`
-   `nl file.txt` == `awk 'print NR,$0'`

# 📅 10.05.2020 vim: Use surround.vim (default in evil-mode)
- In order to swap brackets or any flanking symbol (e.g. \" \", {}, \[\]) press `cs` `+` **(** for **(** as flanking symbol.

# 📅 07.05.2020 trivia: Linguistics 101
- For some side project of mine I need to learn some specifics how syntax and semantics of a sentence play together.
-   Transitivity of verbs := A intransitive verb does not allow a direct object. Whereas a transitive verb requires at least one object.
-   Topic-prominent language := A language which is syntactically structured in a way so that it focus on the topic (the given, old information), followed by a comment (for instance how that changes into a new on information)

# 📅 06.05.2020 clojure: Implement atom? for clj/cljs using reader conditionals
- Some language features are not implemented the same way in clojure and clojurescript. To use the same code base for both one might use reader conditionals.

``` {.clojure}
(defn atom? [x]
   #?(:clj (instance? clojure.lang.IAtom x)
      :cljs (instance? cljs.core.IAtom x)))

```

\~ by [vlaaad](https://clojureverse.org/t/creating-a-cljc-atom-function/3885/3)

**Bonus:** To make this work you need to change the file extension from `.clj/.cljs` to `.cljc`

# 📅 05.05.2020 Currying vs partial application
- **Partial application** means creating an intermediate function by already defining part of its arguments **Currying** means breaking down a function in a bunch of intermediate functions which take only one argument.
- *Partial application is when you curry a function, and use some, but not all of the resulting functions.* \~ [SpoonMaiser](https://stackoverflow.com/questions/218025/what-is-the-difference-between-currying-and-partial-application#comment87580_218055)

# 📅 04.05.2020 vim: Start using the jump list
- This is a huge productivity booster: Use `Ctrl-o` and `Ctrl-i` (in command mode) to move forwards/backwards through the jumplist. The jumplist is maintained project wide!
- With `:jumps` you can see where you are currently located in the jumplist. The relative number `N` of jumps allows you to go directly to a jump of interest `N` `Ctrl-o`.
- **Bonus:** If you are using this in Spacemacs a split window will open with the jump list and you can just click on the item - maintaining the split layout. I love this 💚

# 📅 03.05.2020 Clojure: How to use quote and break out of it (unquote-splicing).
- Super useful when you want to write clojure/clojurescript into a file.

``` {.clojure}
(eval (read-string (str `(+ ~@(take 10 (range)))))) ;; 45
```

# 📅 02.05.2020 unix: Set readline to vim mode

``` {.bash}
set -o vim
set -o emacs (default)
```

# 📅 03.03.2020 intellij: Debugging 101

-   `Frames`: lets you navigate in call stacks of the threads.
-   this is especially useful if you set a debug point in a method and want to know which params passed in parent evocations

# 📅 01.05.2020 Clojure: Compute 2-dimensional matrix
- First time I found a use case for partials. I proudly present my helper function I made:

``` {.clojure}
(defn map-matrix [transducer m l]
    "Outputs a 2-dimensional matrix (m x l), each
     entry resulting of the transducer function which takes x ∈ m, y ∈ l."
     (map (fn [x] (map (partial transducer x) l))m))

(map-matrix + [1 2 3] [100 200 300])
;; ((101 201 301) (102 202 302) (103 203 303))

(map-matrix str ["Hey " "Oi " "你好 "] ["John" "Leandro" "白虎"])
;; (("Hey John" "Hey Leandro" "Hey 白虎") ("Oi John" "Oi Leandro" "Oi 白虎") ("你好 John" "你好 Leandro" "你好 白虎"))

```

# 📅 30.04.2020 Spacemacs: Replace Clojure expression through its result
- , e w

# 📅 30.04.2020 Git: Delete last commit locally (with changes in working dir)
-   `git reset HEAD`

# 📅 30.04.2020 Clojure: Rprewalk-replace Use clojure.walk/prewalk-replace to globally replace a object in arbitrarily nested object

``` {.clojure}
(defn update-all-with [atom  name new-block]
  "Updates existing block with more general elements. Recieves an atom <s> block,
   a name of the block to be substituted, and the new block."
    (reset! atom (clojure.walk/prewalk-replace {name new-block} @atom))
  )
```
