<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

- [Check for missing names](#check-for-missing-names)
- [Label documents and frames](#label-documents-and-frames)
- [Include text alternatives for images and objects](#include-text-alternatives-for-images-and-objects)
- [Images as links and inputs](#images-as-links-and-inputs)
- [Embedded objects](#embedded-objects)
- [Label buttons and links](#label-buttons-and-links)
- [Buttons](#buttons)
- [Links](#links)
- [Label form elements](#label-form-elements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Labels and text alternatives

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

- <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
- <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
- <a href="https://robdodson.me" class="w-author__link">Blog</a>

In order for a screen reader to present a spoken UI to the user, meaningful elements must have proper labels or text alternatives. A label or text alternative gives an element its accessible **name**, one of the key properties for [expressing element semantics in the accessibility tree](/semantics-and-screen-readers/#semantic-properties-and-the-accessibility-tree).

When an element's name is combined with the element's **role**, it gives the user context so they can understand what type of element they're interacting with and how it is represented on the page. If a name is not present, then a screen reader only announces the element's role. Imagine trying to navigate a page and hearing, "button," "checkbox," "image" without any additional context. This is why labeling and text alternatives are crucial to a good, accessible experience.

## Inspect an element's name <a href="#inspect-an-element&#39;s-name" class="w-headline-link">#</a>

It's easy to check an element's accessible name using Chrome's DevTools:

1.  Right-click on an element and choose **Inspect**. This opens the DevTools Elements panel.
2.  In the Elements panel, look for the **Accessibility** pane. It may be hidden behind a `»` symbol.
3.  In the **Computed Properties** dropdown, look for the **Name** property.

<figure><img src="https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format" alt="DevTools accessibility pane showing the computed name for a button." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/38c68DmamTCqt2LFxTmu.png?auto=format&amp;w=1600 1600w" width="800" height="471" /><figcaption>DevTools accessibility pane showing the computed name for a button.</figcaption></figure>To learn more, check out the [DevTools Accessibility Reference](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference).

Whether you're looking at an `img` with `alt` text or an `input` with a `label`, all of these scenarios result in the same outcome: giving an element its accessible name.

## Check for missing names <a href="#check-for-missing-names" class="w-headline-link">#</a>

There are different ways to add an accessible name to an element, depending on its type. The following table lists the most common element types that need accessible names and links to explanations for how to add them.

<table><thead><tr class="header"><th>Element type</th><th>How to add a name</th></tr></thead><tbody><tr class="odd"><td>HTML document</td><td><a href="#label-documents-and-frames">Label documents and frames</a></td></tr><tr class="even"><td><code>&lt;frame&gt;</code> or <code>&lt;iframe&gt;</code> elements</td><td><a href="#label-documents-and-frames">Label documents and frames</a></td></tr><tr class="odd"><td>Image elements</td><td><a href="#include-text-alternatives-for-images-and-objects">Include text alternatives for images and objects</a></td></tr><tr class="even"><td><code>&lt;input type="image"&gt;</code> elements</td><td><a href="#include-text-alternatives-for-images-and-objects">Include text alternatives for images and objects</a></td></tr><tr class="odd"><td><code>&lt;object&gt;</code> elements</td><td><a href="#include-text-alternatives-for-images-and-objects">Include text alternatives for images and objects</a></td></tr><tr class="even"><td>Buttons</td><td><a href="#label-buttons-and-links">Label buttons and links</a></td></tr><tr class="odd"><td>Links</td><td><a href="#label-buttons-and-links">Label buttons and links</a></td></tr><tr class="even"><td>Form elements</td><td><a href="#label-form-elements">Label form elements</a></td></tr></tbody></table>

## Label documents and frames <a href="#label-documents-and-frames" class="w-headline-link">#</a>

Every page should have a [`title`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title) element that briefly explains what the page is about. The `title` element gives the page its accessible name. When a screen reader enters the page, this is the first text that is announced.

For example, the page below has the title "Mary's Maple Bar Fast-Baking Recipe":

    <!doctype html>
      <html lang="en">
        <head>
          <title>Mary's Maple Bar Fast-Baking Recipe</title>
        </head>
      <body>
        …
      </body>
    </html>

For tips on writing effective titles, see the [Write descriptive titles guide](/write-descriptive-text).

Similarly, any `frame` or `iframe` elements should have `title` attributes:

    <iframe title="An interactive map of San Francisco" src="…"></iframe>

While an `iframe`'s contents may contain their own internal `title` element, a screen reader usually stops at the frame boundary and announces the element's role—"frame"—and its accessible name, provided by the `title` attribute. This lets the user decide if they wish to enter the frame or bypass it.

## Include text alternatives for images and objects <a href="#include-text-alternatives-for-images-and-objects" class="w-headline-link">#</a>

An `img` should always be accompanied by an [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#Attributes) attribute to give the image its accessible name. If the image fails to load, the `alt` text is used as a placeholder so users have a sense of what the image was trying to convey.

Writing good `alt` text is a bit of an art, but there are a couple of guidelines you can follow:

1.  Determine if the image provides content that would otherwise be difficult to attain from reading the surrounding text.
2.  If so, convey the content as succinctly as possible.

If the image acts as decoration and does not provide any useful content, you can give it an empty `alt=""` attribute to remove it from the accessibility tree.

Learn more about writing effective `alt` text by checking out [WebAIM's guide to Alternative Text](https://webaim.org/techniques/alttext/).

### Images as links and inputs <a href="#images-as-links-and-inputs" class="w-headline-link">#</a>

An image wrapped in a link should use the `img`'s `alt` attribute to describe where the user will navigate to if they click on the link:

    <a href="https://en.wikipedia.org/wiki/Google">
      <img alt="Google's wikipedia page" src="google-logo.jpg">
    </a>

Similarly, if an `<input type="image">` element is used to create an image button, it should contain `alt` text that describes the action that occurs when the user clicks on the button:

    <form>
      <label>
        Username:
        <input type="text">
      </label>
      <input type="image" alt="Sign in" src="./sign-in-button.png">
    </form>

### Embedded objects <a href="#embedded-objects" class="w-headline-link">#</a>

`<object>` elements, which are typically used for embeds like Flash, PDFs, or ActiveX, should also contain alternative text. Similar to images, this text is displayed if the element fails to render. The alternative text goes inside the `object` element as regular text, like "Annual report" below:

    <object type="application/pdf" data="/report.pdf">
    Annual report.
    </object>

## Label buttons and links <a href="#label-buttons-and-links" class="w-headline-link">#</a>

Buttons and links are often crucial to the experience of a site, and it is important that both have good accessible names.

### Buttons <a href="#buttons" class="w-headline-link">#</a>

A `button` element always attempts to compute its accessible name using its text content. For buttons that are not part of a `form`, writing a clear action as the text content may be all you need to create a good accessible name.

    <button>Book Room</button>

<img src="https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format" alt="A mobile form with a &#39;Book Room&#39; button." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/tcIDzNpCHS9AlfwflQjI.png?auto=format&amp;w=1600 1600w" width="800" height="269" />

One common exception to this rule is icon buttons. An icon button may use an image or an icon font to provide the text content for the button. For example, the buttons used in a What You See Is What You Get (WYSIWYG) editor to format text are typically just graphic symbols:

<img src="https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format" alt="A left align icon button." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ZmQ77kLPbqd5iFOmn4SU.png?auto=format&amp;w=1600 1600w" width="800" height="269" />

When working with icon buttons, it can be helpful to give them an explicit accessible name using the `aria-label` attribute. `aria-label` overrides any text content inside the button, letting you clearly describe the action to anyone using a screen reader.

    <button aria-label="Left align"></button>

### Links <a href="#links" class="w-headline-link">#</a>

Similar to buttons, links primarily get their accessible name from their text content. A nice trick when creating a link is to put the most meaningful piece of text into the link itself, rather than filler words like "Here" or "Read More."

Not descriptive enough

    Check out our guide to web performance <a href="/guide">here</a>.

Useful content!

    Check out <a href="/guide">our guide to web performance</a>.

This is especially helpful for screen readers that offer shortcuts to list all of the links on the page. If links are full of repetitive filler text, these shortcuts become much less useful:

## <figure><img src="https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format" alt="Example of VoiceOver, a screen reader for macOS, showing the navigate by links menu." sizes="(min-width: 519px) 519px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/IPxS2dwHMyGRvGxGi5n2.jpg?auto=format&amp;w=1038 1038w" width="519" height="469" /><figcaption>Example of VoiceOver, a screen reader for macOS, showing the navigate by links menu.</figcaption></figure>Label form elements <a href="#label-form-elements" class="w-headline-link">#</a>

There are two ways to associate a label with a form element such as a checkbox. Either of the methods causes the label text to also become a click target for the checkbox, which is also helpful for mouse or touchscreen users. To associate a label with an element, either:

- Place the input element inside of a label element

<!-- -->

    <label>
      <input type="checkbox">Receive promotional offers?</input>
    </label>

- Or use the label's `for` attribute and refer to the element's `id`

<!-- -->

    <input id="promo" type="checkbox"></input>
    <label for="promo">Receive promotional offers?</label>

When the checkbox has been labeled correctly, the screen reader can report that the element has a role of checkbox, is in a checked state, and is named "Receive promotional offers?" like in the VoiceOver example below:

<figure><img src="https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format" class="w-screenshot" sizes="(min-width: 640px) 640px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/WklT2ymrCmceyrGUNizF.png?auto=format&amp;w=1280 1280w" width="640" height="174" /></figure>Check whether sample HTML elements have accessible names

![temp](https://web-dev.imgix.net/image/user/temp.svg)

Does this image have an accessible name?

**Yes**. Give an image an accessible name by adding an `alt` attribute.

    <object type="application/pdf" data="/report.pdf" alt="Annual report"></object>

Does this object have an accessible name?

**No**. Give an `<object>` element a name by providing text content. (An `alt` attribute on an object will not be read by assistive technologies.)

This sample renders an icon button:

    <button>
      <svg class="icon">
        <use xlink:href="#icon-1" />
      </svg>
    </button>

Does this button have an accessible name?

**No**. Give a button an accessible name by providing text content, an `aria-label` attribute, or an `aria-labelledby` attribute.

This sample renders an icon button with a tooltip that appears on hover and focus:

    <button>
      <svg class="icon">
        <use xlink:href="#icon-1" />
      </svg>
      <span class="tooltip hidden">Open menu</span>
    </button>

Does this button have an accessible name?

**Yes**. Even if the button's tooltip is visually hidden using CSS, assistive technologies can still read its text content.

**Caution:** When visually hiding button text, use CSS rather than the `hidden` attribute. The `hidden` attribute removes the element from the accessibility tree.

    <label>
      <input type="checkbox" value="subscribe"></input>
      Subscribe to the newsletter?
    </label>

Does this checkbox have an accessible name?

**Yes**. The label is associated with the checkbox because the label is the checkbox's parent. So, assistive technologies treat the label's text content as the input's name.

    <input type="checkbox" value="subscribe"></input>
    <label for="subscribe">Subscribe to the newsletter?</label>

Does this checkbox have an accessible name?

**No**. The checkbox's `value` attribute indicates what text will be saved when the form is submitted, but assistive technologies don't read it. To provide an accessible name, add an `id` attribute with the value `subscribe` to associate the checkbox with the label.

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/labels-and-text-alternatives/index.md)

<a href="/accessible" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

- ### Contribute

  - <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
  - <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

- ### Related content

  - <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
  - <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
  - <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
  - <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
  - <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
  - <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

- ### Connect

  - <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
  - <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

- <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
- <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
- <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
- <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

- <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
- <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
