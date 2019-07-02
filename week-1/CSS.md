# Slides: [Presentation](https://hackmd.io/@3h2qEDKEQXSZK4l2wloSMg/CSS)  
# CSS Research 
## Responsive vs mobile-first design

---

### Responsive Web Design (RWD)
#### Approach/Process
- starts on the desktop (i.e. max required resolution) and then scales down to the smallest screen
- uses only HTML and CSS
- URL and HTML code are consistent across all devices

---

![image of responsive process](https://darwindigital.com/wp-content/uploads/2018/03/responsive-web-design.png)

---

**What does it take to create a responsive design**
- flexible, grid-based layout 
- flexible images and media 
- media queries

**Suggested steps**
1. Make web images responsive 
2. Consider responsive typed content (using the vw unit)
3. Define media queries (using breakpoints)
4. Test your prototype



---




### Application 
common when content needs to be authoritative & informative (B2B, traditional website)

##### Pros
– Good for heavily stacked information websites
– Easier for large forms and complex call-to-actions
– Cost-effective development and maintenance
– Great for SEO

##### Cons
– The mobile experience is not 100% optimized



---

### Mobile-first 

#### Mobile-first is about a primarily mobile oriented user-experience 

Mobile-first responsive web design **assumes the worst case scenario first** 

![image of mobile first design process](https://darwindigital.com/wp-content/uploads/2018/03/mobile-first-design.png)
This includes:
* an app-like user-interface
*  less text, larger fonts,
*  fast download speed,
*  one call-to-action per page 
*  clear and concise forms.

---

Pros:
* Better user experience on mobile devices
* majority of web browsing today is done on mobile devices.
* If your page loads on unstable mobile networks, it will load on anything. 
* Forces the designer to focus on essential content, reduces clutter. 

---

* Scaling up from the mobile context versus scaling down from the desktop context **ensures that your core message, content and functionality remain intact** as the screen real estate and connection speed increase.
* Ensuring a seamless experience on mobile will help drive and engage more traffic on your site
* Website can be designed to use built in phone features(camera, gps, haptic feedback, voice detection etc)
* cheaper than building a native iOS or Android App

---

Cons:

* Desktop experience may not fully utilize all the available space
* Not suitable for websites with lots of content. Mobile first design requires simplicity.

---

### Responsive vs Mobile-First: 80-20 rule

If 80% of your target audience is on desktop use, responsive design; if 80% are on mobile phone use mobile-first. 
To find out how users access your site mostly:  
- Use  Google analytics
- Use industry statistics 
- Use user testing

---

## How to write CSS with BEM

---

### What is BEM?
BEM is an abbreviation of the key elements of the methodology — Block, Element and Modifier. One of the basic rules of the BEM methodology is to use only class selectors. BEM is a methodology designed by Yandex, its goal is to help developers better understand the relationship between the HTML and CSS in a given project. 

---

BEM proposes that the three basic entities (blocks, elements and modifiers) are enough to define how to author HTML and CSS, structure code and components, describe interfaces and scale a project up to an industry-leading service.

---

![image of BEM](https://i.imgur.com/glhBlak.png)

---

1. Block
Standalone entity that is meaningful on its own.
Examples of blocks include:

    * heading
    * button
    * navigation menu

---

2. Element
A part of a block that has no standalone meaning and is semantically tied to its block.

Examples of elements include:

    * a navigation menu (block) that contains menu items;
    * a table (block) that contains rows, cells and headings.

---

3. Modifier
A flag on a block or element. Use them to change appearance or behavior.

    * checked
    * disabled


---

### Discuss Examples
![](https://i.imgur.com/UaqZHEp.png)

---

![](https://i.imgur.com/6S1NAcH.png)

---

#### Why should we consider BEM?

1. If we want to make a new style of a component, we can easily see which modifiers and children already exist. We might even realize we don't need to write any CSS in the first place because there is a pre-existing modifier that does what we need.

---

2. If we are reading the markup instead of CSS, we should be able to quickly get an idea of which element depends on another.

---

3. Designers and developers can consistently name components for easier communication between team members. In other words, BEM gives everyone on a project a declarative syntax that they can share so that they're on the same page.

---

 Team: Reuben, Leonie, Gigi & Emmanuel
 ## THANK YOU!  
 
### References:  

[Responsive resource](http://bradfrost.github.io/this-is-responsive/resources.html)  
[What is BEM?](http://getbem.com/introduction/)  
[Why you should use BEM?](https://www.smashingmagazine.com/2018/06/bem-for-beginners/#the-main-reasons-why-we-do-not-use-any-selectors-except-classes)

