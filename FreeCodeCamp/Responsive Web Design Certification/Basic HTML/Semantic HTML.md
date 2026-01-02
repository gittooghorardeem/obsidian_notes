- **Semantics** are the meaning of words, or phrases, in a language. In HTML, which is a language, elements have their own semantic meaning too. In fact, you can think of your HTML document like you would a text document. And much like a text document, you might have headings, images, bold text, and other formatting.
- The semantic meaning of an element refers to what special information that element conveys. The semantic meaning of a `p` element, for example, is a paragraph of text:
- Most elements have semantic meaning. The `div` element is one of the very few that does not.

- **Structural hierarchy**
- The most important aspect of creating a structural hierarchy is the proper use of heading elements. Heading elements are numbered as `h1`, `h2`, `h3`, and so on. These numbers represent the heading level for that element.


- **Presentational and Semantic HTML**
- Presentational HTML focuses on the appearance and style of the content. In the early days of HTML, developers would use elements like the `center`, `big`, and `font` elements. But in modern web development you shouldn't use these types of elements, because of their limitations and negative impact on accessibility and maintainability.
- The `font` element is a deprecated element used to set the font size and color of the text. Here's an example of a `font` element.
- The range for the `size` attribute is from `1` to `7`, with `1` being the smallest and `7` being the largest. The default value is `3`, if you don't set the value explicitly.
- The `center` element is another deprecated element that is used to center the content horizontally within its container. Here's an example of the `center` element that contains text and a paragraph element.
- The `header` element for defining the header of the document, or section.
- The navigation section element, `nav`, for sections with navigation links.
- The `section` element for grouping related information.
- The `figure` element for illustrations and diagrams.

**Nuanced Semantic Elements**
- These elements are very closely related to the concepts of presentational and semantic HTML. The idiomatic text element, `i`, was originally used for presentational purposes to display the text in italics. But now, it is frequently used for highlighting alternative voice or mood, idiomatic terms from another language, technical terms, and thoughts.
- If you do need to emphasize the importance of the text, you can use a similar semantic element called the emphasis element, `em`.
- The "bring attention to" element, `b`, is commonly used to highlight keywords in summaries, or product names in reviews. Usually, browsers display this text in boldface. Here's an example using the `b` element to highlight product names in this review:
- 
  `<dl>`
  `<dt>Flour</dt>`
  `<dd>2 cups</dd>`
  `<dt>Sugar</dt>`
  `<dd>1/2 cup</dd>`
  `<!-- <dt>Vegetable Oil</dt>`
  `<dd>2 tablespoons</dd> -->`
  `</dl>`
- **Block quotes**
- In HTML, quoted elements are used to distinguish quoted text from the surrounding content. This gives the quoted text a format that is easy to identify.
- You should use the block quotation element for representing a section quoted from another source. It's mainly used for extended quotations. If the source of the quote has an address, you can cite it with the `cite` attribute. The value of this attribute should be a valid URL. This is an example of a quote within a block quotation element:
- Abbreviation in HTML `<abbr>...</abbr>`
- Address content
- 
  `<address>`
  `<h2>Company Name</h2>`
  `<p>`
    `1234 Elm Street<br />`
    `Springfield, IL 62701<br />`
    `United States`
  `</p>`
  `<p>Phone: <a href="tel:+15555555555">+1 (555) 555-5555</a></p>`
  `<p>Email: <a href="mailto:contact@company.com">contact@company.com</a></p>`
  `</address>`
- **Time element**
- The `time` element is used to represent a specific moment in time.
- The `datetime` attribute is used to translate dates and times into a machine-readable format.
	- This is important, because it helps with search engine results and helps the browser process date and time information more effectively.
	- The value for the `datetime` attribute must be either a valid year, valid month, valid time, local date, global date, or valid duration string.
	- 
	  `<p>`
	  `The graduation will be on <time datetime="2024-06-15T15:00">June 15</time>`
	 `</p>`
- 