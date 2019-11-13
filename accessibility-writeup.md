# Accessibility in Web

---

This document is an overview of some of the accessibility considerations to make when working on a project. It's by no means a fully comprehensive list as guidelines are constantly evolving. With that in mind, the last section of this document will list a selection of resources to look through for further reading as well as some tools to help with development.

## Contents

---

1. Overview
2. HTML and Accessibility (work in progress!)

   _...more content to come...._

3. Resources

## 1. Overview

---

[W3.org](https://w3.org/WAI/fundamentals/accessibility-intro/) defines Web accessibility in their introduction as websites, tools and technologies being designed and developed in such a way that people with disabilities can use them. In particular, users should be able to perceive, understand, navigate and interact with content as well as being able to contribute to the Web.

All disabilities that affect access to the Web are encompassed by Web accessibility. The terms below are a broad overview and cover a wide spectrum of conditions:

- **Auditory**

  _can include hearing loss and the loss of partial or total ability to hear. Something to also consider are conditions such as Auditory Processing Disorder, which affects the individuals ability to interpret or discriminate sounds._

- **Cognitive**

  _can include individuals who experience certain limitations in learning, memory, attention, communication, decision making._

- **Neurological**

  _diseases of the brain, spine and nerves that affect them_

- **Physical**

  _a limitation on a person's physical functioning, mobility, dexterity or stamina_

- **Speech**

  _a condition in which a person has problems creating or forming the speech sounds needed to communicate with others_

- **Visual**

  _decreased ability to see to a degree that causes problems not fixable by usual means, such as glasses_

## 2. HTML and Accessibility

---

### 2.1 The Importance of Semantic HTML

With the increase in prevalence of JavaScript and CSS in web applications, it has become increasingly easier to make any HTML behave in any way you like, (e.g. making a p tag look like a header).

```html
<!-- BAD -->
<p class="header h1">This is a header</p>

<!-- GOOD -->
<h1 class="header h1">This is also a header</h1>
```

For users that navigate using the keyboard only and users who use screen readers, this will likely result in a worst experience. Many screen readers provide shortcuts to allow you to skim key features of the content to allow quicker navigation. For header tags a user would be able to read each header and only read that section if it's of interest. If p tags are used, this functionality wouldn't work.

The sections below will provide some examples to cover this in more detail.

### 2.2 Using clear language

When creating the content for your application make sure to consider the following:

- **Avoid jargon or slang** that may not be easily understood by the user or correctly pronounced by a screen reader.
- **Avoid Abbreviations** e.g. use January, instead of Jan.
- Try to **avoid characters** where there is an equivalent word e.g. 5 to 8 instead of 5-8.
- Make sure that the first instance of an acronym has the full word equivalent so that users can understand it if they've not come across it before. e.g. Cascading Style Sheets (CSS).

### 2.3 Don't use tables for content positioning

Using tables for overall layout of content other than actual tables, causes confusion for people with screen readers. Now that CSS has evolved to include more positioning features, this should be avoided.

### 2.4 Don't use CSS grid as a replacement for proper HTML ordering

CSS grid allows you to position and reorder your content visually. A good use case for this is having sections stacked in mobile view but rearranged to fit more content in larger screens.

The problem is that screen readers will always read the content in the order it's been written in the HTML. Therefore, make sure to organise the HTML in a way that would make sense, even if the user can't see the screen. Don't put the nav at the bottom of the HTML and then position it at the top of the screen with CSS grid!

### 2.5 Use meaningful text labels for UI elements

When screen reader users get a list of buttons and form controls on a page, if they all say "Click here!" or "Enter text here", that's not going to be very helpful!

```html
<!-- BAD -->
<p>
  Cheese is great. To view more cheese content<a href="https://www.cheese.com"
    >click here!</a
  >
</p>

<p>
  Baguettes are great. To view more baguette content<a
    href="https://www.baguettes.com"
    >click here!</a
  >
</p>

<!-- GOOD-->
<p>
  Cheese is great. <a href="https://www.cheese.com">View more cheese content</a>
</p>

<p>
  Baguettes are great.<a href="https://www.baguettes.com"
    >View more baguette content</a
  >
</p>
```

### 2.6 Don't remove visual focus indicators from focusable elements

The blue line around focusable elements may not be in keeping with the overall look of your website design, but removing them can be detrimental to keyboard users. People who tab to this content aren't able to get the feedback that this is the element that's focused. (Check out this Stack Overflow post to read more)[https://stackoverflow.com/questions/20340138/remove-blue-border-from-css-custom-styled-button-in-chrome].

## 3. Resources

---

### 3.1 MacOS VoiceOver Tool

MacOS has a built in screen reader tool that can be accessed from the accessibility options in system preferences. There is also a built in tutorial to take you through the key features of this tool.

### 3.2 Websites

1. **[WebAIM](https://webaim.org/)**

   _"WebAIM's mission is to expand the potential of the web for people with disabilities by providing the knowledge, technical skills, tools, organizational leadership strategies, and vision that empower organizations to make their own content accessible to people with disabilities."_

2. **[W3.org - Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/)**

   _"The WCAG documents explain how to make web content more accessible to people with disabilities. Web “content” generally refers to the information in a web page or web application, including:
   natural information such as text, images, and sounds code or markup that defines structure, presentation, etc."_

3. **[Section 508 Policy (USA)](https://www.section508.gov/)**

   _"In 1998, Congress amended the Rehabilitation Act of 1973 to require Federal agencies to make their electronic and information technology (EIT) accessible to people with disabilities. The law (29 U.S.C § 794 (d)) applies to all Federal agencies when they develop, procure, maintain, or use electronic and information technology. Under Section 508, agencies must give disabled employees and members of the public access to information comparable to the access available to others."_

4. **[Vox Media Accessibility Checklist](http://accessibility.voxmedia.com)**

   _"Making work accessible creates a better experience across the board. Use this checklist to help build accessibility into your process no matter your role or stage in a project."_

5. **[Accessibility regulations for public sector bodies (23 September 2018, UK)](https://www.gov.uk/guidance/accessibility-requirements-for-public-sector-websites-and-apps)**

   _"New regulations came into force for public sector bodies on 23 September 2018. They say you must make your website or mobile app more accessible by making it ‘perceivable, operable, understandable and robust’. The full name of the regulations is the Public Sector Bodies (Websites and Mobile Applications) (No. 2) Accessibility Regulations 2018."_

6. **[The A11Y Project](https://a11yproject.com/)**

   _"Accessibility can be a complex and difficult topic. The Accessibility Project understands this and wants to help make it easier to implement on the web. Our goal is to accomplish this with three principles in mind:_

   1. _**Digestible.** We strive to feature short, digestible pieces of content._
   2. _**Up-to-date.** The project is hosted on GitHub so information can be current with the latest standards._
   3. _**Forgiving.** People make mistakes, so we seek to be encouraging."_

### 3.3 Browser Tools

1. Chrome

   - [Funkify Disability Simulator](https://chrome.google.com/webstore/detail/funkify-%E2%80%93-disability-simu/ojcijjdchelkddboickefhnbdpeajdjg?hl=en)

     _"Funkify is a brand new extension for Chrome that helps you experience the web and interfaces through the eyes of extreme users with different abilities and disabilities."_

   - [Axe - Web Accessibility Testing](https://chrome.google.com/webstore/detail/axe-web-accessibility-tes/lhdoppojpmngadmnindnejefpokejbdd)

     _"Accessibility checker for WCAG 2 and Section 508 accessibility. Find accessibility defects on your website or web application by using the axe Chrome extension. Drop the axe on your accessibility defects!"_

   - [Accessibility Insights for Web (Chrome)](https://chrome.google.com/webstore/detail/accessibility-insights-fo/pbjjkligggfmakdaogkfomddhfmpjeni)

     _"Accessibility Insights for Web is an extension for Chrome and Microsoft Edge Insider that helps developers find and fix accessibility issues in web apps and sites."_

2. Firefox

   - [Firefox Accessibility Inspector](https://developer.mozilla.org/en-US/docs/Tools/Accessibility_inspector)

     _Available in developer tools menu since Firefox 63!_

     _"The Accessibility Inspector provides a means to access important information exposed to assistive technologies on the current page via the accessibility tree, allowing you to check what's missing or otherwise needs attention."_

   - [Axe Developer Tools](https://addons.mozilla.org/en-GB/firefox/addon/axe-devtools/)

     _"Automated tool to find Accessibility defects on your web site by using the axe Firefox extension. Drop the axe on your accessibility defects!"_

3. Safari

   At the time of writing, there doesn't seem to be too much in the way of tools or extensions, but this may change in the future. There is [a11yTools](https://apps.apple.com/us/app/a11ytools/id1364813335?ign-mpt=uo%3D4&mt=12), but the reviews aren't great and it is a paid for content.

4. Edge

   - [Microsoft Edge Developer Tools](https://docs.microsoft.com/en-gb/microsoft-edge/devtools-guide)

     _*Microsoft Edge introduces great new improvements to F12 developer tools, including some of the most requested features from UserVoice. The new tools are built in TypeScript, and are always running, so no reloads are required.*_

   - [Accessibility Insights for Web (Edge)](https://microsoftedge.microsoft.com/insider-addons/detail/ghbhpcookfemncgoinjblecnilppimih)

     _"Accessibility Insights for Web is an extension for Chrome and Microsoft Edge Insider that helps developers find and fix accessibility issues in web apps and sites."_
