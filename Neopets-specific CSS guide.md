# Neopets-specific CSS guide



###### HTML basics link

###### CSS basics link



The goal of this page is to lay out some of the most common things people want to do with their lookups, and then:

1\. compile the solutions

2\. explain what's going on so you can tinker



### CSS Selectors



The most important thing:

To change anything about an element on the page, whether it's built-in NPC stuff or something you're adding, you need a CSS selector.



###### The selector is usually one of these things:

1\. A class, which starts with period, like .text

2\. An ID, which starts with hash, like #uniquething

3\. A standard HTML thing, like p or div (which tries to select all paragraphs or all divs)

4\. A list of selectors separated by commas (if you're making most of the standard NPC page disappear you'd do this)

5\. A pair of selector separated by other punctuation or space, which indicates their relationship.



###### Breaking down 5:

To select all of the images of your pets on your userlookup, and give them all a red border, you'd use:



.userlookuppets img



which selects every userlookuppets image - meaning within that class, every image.



###### The whole code:



.userlookuppets img {

border: 1px solid red;}



The result would look like this:

\[screenshot]



To identify what selector you're dealing with, you can usually find it with your browser's dev tools. On windows, hit CTRL+SHIFT+i to open the inspector.



My very favorite dev tools feature: the Element Picker. Hit CTRL+SHIFT+c, or select the setting from your dev tools popout. This lets you hover around the page, and everything you highlight will show its element type, class/ID, as well as a color-coded shape for its size and margins. This helps me all the time when aligning messy elements.



Here's a screenshot of a couple pieces of the page I highlighted using the cursor tool:

\[Screenshot]

You can see that there is a div for the userinfo, and one for the usershield, but if we move around, we find a container for both, called, logically, the userinfocontainer.



If you want to replace an image with an overlay, or change the font just within one area of the page, this tool is your best friend.



### How to Use Selectors for NPC:





##### To remove an element from the page:



selector { display: none;}



##### To hide a lot of things at once:



Example:

\#retroTopBar, .navhover, .hdr, #mb { display:none;}

Hides the top headers and the left-hand sidebar



Example 2:

.sidebar-section.sm-filler, .sidebar-section.st, .sidebar-section.se {

background-image: none;

background-color:  rgba(255, 230, 255, 0);}

Makes the right-hand sidebar transparent so it can blend in with your background. The color can be anything rgba as long as the 4th value is 0, which makes it 100% transparent. You have to specify SOMETHING as the background color or it won't overwrite the default NPC yellow.

NOTE: You may need to change the font color of the sidebar too, so it's legible.





##### Things some people may want to hide



These are starting points; you can inspect the page and find others yourself, but reach out on discord or neomail if you are stuck!



###### General:



hr - get rid of the horizontal line between areas



\#retroTopBar - the "Neopets Classic" header at the very very top of the page



.navhover - the lefthand sidebar



.hdr - the header image that changes depending on your page



\#mb - this is specifically a tiny image that is the bottom edge of the left-hand sidebar. I do NOT know why it's not included in the table, but it has to be listed as its own selector. There's probably a reasonable explanation.



###### User Lookups:





\#userShield

NOTE: if you add a space and then img - will select the image inside the usershield div, so you can overlay it



###### On Pet Lookups:



.petImage - you guessed it, the image of your pet



.petbelongingscontainer - your pet's belongings



.petlinks - the pet page and neomail owner icons



.petbdstats - the battledome image and, well, stats





#### Creating classes for your own content



If you want one or multiple little areas on your page, create a class for them that will be decorated with the color, border, etc you want.



Example:

<div class="blurb">Hey! Welcome to my lookup! I'm Johnny Samples.</div>



in the CSS:

.blurb{

color:navy;

background-color:linen;

border:2px dotted navy;

}



Note that you might have to add some child selectors to be sure you override existing styles. On my lookup, I had to target all paragraph elements that were inside my wrapper div in order to change ALL the font color:



.blurb p{color: navy;}



#### Pretty Links





You can also add flair by styling important text, or changing link font. It's important that links are still distinct somehow so people can identify what text IS a link. But to decorate your own, here's what you need to know:



Link elements are just "a" and they look like this:



<a href="url">Click this!</a>



You can target all links with a{} OR you can target links of a certain kind. For example, I like to make my nav links highlight when hovered. You can add a class or ID to the link:



<a href="url" class="coollink">Click this!</a>



Then in your CSS:



a {

text-decoration: none;

color: pink;
}



or, if specific class etc (fill in the brackets with styles)



.coollink { }



or to target just the links in one section:



.userinfo a { }



**Text-decoration: none** removes things like underlines.

**Color** overrides the unclicked link's color, of course.

You can also change the font family and lots of other things.



A fun thing - you can make links change while hovered, or after being visited - check out the W3Schools page for more on that; it's too much to fit here.



##### Add something to the corners or edges of your div



Using positioning is a tower of cards, so be ready to troubleshoot if needed. (Dev tools will tell you when settings aren't working as written!)



Read more about positioning to truly understand it.



If you make your main container - the .petlookupContainer, or a .wrapper div that you create, for example - positioned, then you can add other elements in relation to it.

NOTE: Relative here means relative to its flow in the whole document. It changes a little about how the element behaves, but not as much as absolute positioning does.



.petlookupcontainer{position: relative;}



This will add a cute thing 10 pixels in from the top right corner of the lookup container:



.cutething{

position: absolute;

top: 10px;

right: 10px;}



Example in action:

\[SCREENSHOT - use Apron's page maybe]

