# Accessibility Research -> Week 1 

### Accessible Modal
<!--
Codepen examples:
https://codepen.io/scottohara/pen/lIdfv
https://codepen.io/matuzo/pen/GrNdvK?editors=0010

[This article](https://medium.com/@matuzo/writing-javascript-with-accessibility-in-mind-a1f6a5f467b9) is written by Manuel Matuzovic (whose Codepen is the second link in the section above). He talks through how to make an accessible modal window and shows videos of inaccessible and accessible examples. 
Think this is important to remember, especially making our websites over week one:
-->

<!-- How to use tabindex in HTML: https://www.youtube.com/watch?v=Pe0Ce1WtnUM&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=7

**How to step by step:**
https://bitsofco.de/accessible-modal-dialog/
-->
<!-- 1. Intro -> Georgia
2. Markup the Dialog and Dialog Overlay Appropriately -> Tine

2. On Dialog Open, Set Focus -> Tine
3. On Dialog Close, Return Focus to the Last Focused Element -> Tine
4. While Open, Prevent Mouse Clicks Outside the Dialog ->Georgia
5. While Open, Prevent Tabbing to Outside the Dialog -> Georgia
7. Allow the ESC Key to Close the Dialog -> Tine -->

1. Intro

>_Making an accessible site doesn’t mean that you have to decide whether to use JavaScript or not. **Accessibility is about making content available to as many people as possible**, which also includes users with old browsers and computers, slow internet connections, strict security restrictions (e.g. no JavaScript) and so on. The experience under conditions like these where JavaScript may not work or take too long to load might not be ideal but is still good enough if the website is accessible and usable._



---




Markup the Dialog and Dialog Overlay Appropriately 

There are two elements to a modal:

Dialog
When creating a dialog, we need to make sure that it has the appropriate role, in this case dialog. We also need to make sure that there is a label for the dialog, provided using the aria-labelledby and optionally the aria-describedby attributes

Overlay



---



2. On Dialog Open, Set Focus 

When first opened, focus should be set to the first focusable element within the dialog



---




3. On Dialog Close, Return Focus to Last Focused Element
When the dialog is closed, focus should be returned to the element that opened it



---




4. While Open, Prevent Mouse Clicks Outside the Dialog
Users should not be able to click on elements outside the dialog window



---




5. While Open, Prevent Tabbing to Outside the Dialog
User navigating with a keyboard should not be able toTAB out of the dialog content



---




6. Allow the ESC Key to Close the Dialog
When the dialog is open, pressing the ESC key should close it


---




[Demo modal here!](https://ireade.github.io/accessible-modal-dialog/)



---



<!--
## How to explain modals:
Dialog - just another word for a modal - it's the bit you interact with
Overlay - the bit that covers the rest of the webpage - the bit you don't interact with. 
Tabindex - using tabindex can affect your accessibility score. You can prevent this by setting the tabindex of every tag you want to be tabbable to tabindex=0. This will add the tag to the tab order.

# Buliding an accessible nav bar: Some things to think about 
-->

### Menu items should be in a **list** inside a **nav** tag 
 
 
 > </a>Such structural information allows assistive technologies to announce the number of items in the menu and provide corresponding navigation functionality.
 
 
 
 ---
 
 
 

### Make sure your nav bar is accessible on _**touch devices**_ 

If you have a dropdown menu that is triggered by a hover, this could be lost by users with disabilities on a touch device. 




---




### An Example 

**HTML** 

> <div class="linkWithDropdown">
	<a href="/a/"">Place A</a>
	<ul class="dropdown">
		<li><a href="/b/">Place B</a></li>
		<li><a href="/c/">Place C</a></li>
		<li><a href="/d/">Place D</a></li>
	</ul>
</div>
And the relevant CSS like so:

**CSS** 

> .dropdown { display:none; }
.linkWithDropdown:hover .dropdown { display:block; }



---




### Make sure your nav bar is _**keyboard navigation**_ friendly

 1. Make sure the markup is semantic & in the correct order 
 
 2. No autofocusing-elements on page load...if you autofocus on an element it can disrupt the order + therefore the tabbing indexes. 



---



 
 ### Label menus 
 
 
 ></a>Label menus to make them easier to find and understand. Labels should be short but descriptive, to allow users to distinguish between multiple menus on a web page. Use a heading, aria-label, or aria-labelledby to provide the label.
 
```
<nav aria-labelledby="mainmenulabel">
	<h2 id="mainmenulabel" class="visuallyhidden">Main Menu</h2>
</nav>
```



---





 ### Callouts
 A callout is a panel of content that "pops up" when the user initializes its appearance from a trigger element, presenting more information about the trigger element. This allows the user to get more information about an element without actually leaving the page and without interrupting the user's current task.
 To access them with your keyboard, you just have to use the arrows keys.
 To be heard in your HTML, you need to add the `data-callout` attribute.
 
 ```
 <button class="ancBtn iconAfter iconArrowSmallDownAfter" data-callout="<p>I am the content passed through the <code>[data-callout]</code> attribute.</p><img alt='This is an image inside a basic callout.' src='my-image.png' width='256' />" type="button">I will show a basic callout</button>

 ```
 
 
 ---

 
> ### Types of Callouts
> *The types of callouts and their usage can be categorized as follows:*

> **Menu callout**
> A drop-down "menu" of links which can be triggered by any element, such as a button, link, or icon.
>
> **Hover callout**
> A callout that will be opened when the trigger element is hovered.

> **Other Callout**
> A callout that does not fall into any of the above categories; can contain any type of content (i.e., text, images, calls to action, etc.) and is triggered by any element, such as a button, link, or icon.

---

- An input should not have a callout with focusable items since there is no good way to use a keyboard to get to that part of the page.
 
- Callout menus should be as simple as possible. They should not be bloated with unnecessary interactivity or visual effects.
