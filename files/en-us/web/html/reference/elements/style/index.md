---
title: "<style>: The Style Information element"
slug: Web/HTML/Reference/Elements/style
page-type: html-element
browser-compat: html.elements.style
sidebar: htmlsidebar
---

The **`<style>`** [HTML](/en-US/docs/Web/HTML) element contains style information for a document, or part of a document. It contains CSS, which is applied to the contents of the document containing the `<style>` element.

{{InteractiveExample("HTML Demo: &lt;style&gt;", "tabbed-standard")}}

```html interactive-example
<style>
  p {
    color: #26b72b;
  }
  code {
    font-weight: bold;
  }
</style>

<p>
  This text will be green. Inline styles take precedence over CSS included
  externally.
</p>

<p style="color: blue">
  The <code>style</code> attribute can override it, though.
</p>
```

```css interactive-example
p {
  color: #f00;
}
```

The `<style>` element must be included inside the {{htmlelement("head")}} of the document. In general, it is better to put your styles in external stylesheets and apply them using {{htmlelement("link")}} elements.

If you include multiple `<style>` and `<link>` elements in your document, they will be applied to the DOM in the order they are included in the document — make sure you include them in the correct order, to avoid unexpected cascade issues.

In the same manner as `<link>` elements, `<style>` elements can include `media` attributes that contain [media queries](/en-US/docs/Web/CSS/CSS_media_queries), allowing you to selectively apply internal stylesheets to your document depending on media features such as viewport width.

## Attributes

This element includes the [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).

- `blocking`
  - : This attribute explicitly indicates that certain operations should be blocked on the fetching of critical subresources. [`@import`](/en-US/docs/Web/CSS/@import)-ed stylesheets are generally considered as critical subresources, whereas [`background-image`](/en-US/docs/Web/CSS/background-image) and fonts are not. The operations that are to be blocked must be a space-separated list of blocking tokens listed below.
    - `render`: The rendering of content on the screen is blocked.
- `media`
  - : This attribute defines which media the style should be applied to. Its value is a [media query](/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries), which defaults to `all` if the attribute is missing.
- `nonce`
  - : A cryptographic nonce (number used once) used to allow inline styles in a [style-src Content-Security-Policy](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/style-src). The server must generate a unique nonce value each time it transmits a policy. It is critical to provide a nonce that cannot be guessed as bypassing a resource's policy is otherwise trivial.
- `title`
  - : This attribute specifies [alternative style sheet](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet) sets.

### Deprecated attributes

- `type` {{deprecated_inline}}
  - : This attribute should not be provided: if it is, the only permitted values are the empty string or a case-insensitive match for `text/css`.

## Examples

### A basic stylesheet

In the following example, we apply a short stylesheet to a document:

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### Result

{{EmbedLiveSample('A_basic_stylesheet', '100%', '100')}}

### Multiple style elements

In this example we've included two `<style>` elements — notice how the conflicting declarations in the later `<style>` element override those in the earlier one, if they have equal [specificity](/en-US/docs/Web/CSS/CSS_cascade/Specificity).

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: white;
        background-color: blue;
        padding: 5px;
        border: 1px solid black;
      }
    </style>
    <style>
      p {
        color: blue;
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### Result

{{EmbedLiveSample('Multiple_style_elements', '100%', '100')}}

### Including a media query

In this example we build on the previous one, including a `media` attribute on the second `<style>` element so it is only applied when the viewport is less than 500px in width.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="UTF-8" />
    <title>Test page</title>
    <style>
      p {
        color: white;
        background-color: blue;
        padding: 5px;
        border: 1px solid black;
      }
    </style>
    <style media="(width < 500px)">
      p {
        color: blue;
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <p>This is my paragraph.</p>
  </body>
</html>
```

#### Result

{{EmbedLiveSample('Including_a_media_query', '100%', '100')}}

## Technical summary

<table class="properties">
  <tbody>
    <tr>
      <th>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content"
          >Metadata content</a
        >.
      </td>
    </tr>
    <tr>
      <th>Permitted content</th>
      <td>
        Text content matching the <code>type</code> attribute, that is
        <code>text/css</code>.
      </td>
    </tr>
    <tr>
      <th>Tag omission</th>
      <td>Neither tag is omissible.</td>
    </tr>
    <tr>
      <th>Permitted parents</th>
      <td>
        Any element that accepts
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#metadata_content"
          >metadata content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">Implicit ARIA role</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >No corresponding role</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">Permitted ARIA roles</th>
      <td>No <code>role</code> permitted</td>
    </tr>
    <tr>
      <th>DOM interface</th>
      <td>{{domxref("HTMLStyleElement")}}</td>
    </tr>
  </tbody>
</table>

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- The {{HTMLElement("link")}} element, which allows us to apply external stylesheets to a document.
- [Alternative Style Sheets](/en-US/docs/Web/HTML/Reference/Attributes/rel/alternate_stylesheet)
