- The `link` element is used to link to external resources like stylesheets and site icons. Here is the basic syntax for using the `link` element for an external CSS file:
	- `<link rel="stylesheet" href="./styles.css" />`
	- The `rel` attribute is used to specify the relationship between the linked resource and the HTML document. In this situation, we need to specify that this linked resource is a `stylesheet`.
	- It is considered best practice to separate your HTML and CSS in different files. Developers will use the `link` element for their external CSS file instead of writing everything in the HTML document.
	- The `href` attribute is used to specify the location of the URL for the external resource.
	- The `dot` followed by a forward slash in the example tells the computer to look in the current folder, or directory, for the `styles.css` file.
	- The `link` element should be placed inside the `head` element as seen in the following example:
	  `<head>`
		  `<meta charset="UTF-8" />`
		  `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`
		  `<title>Examples of the link element</title>`
		  `<link rel="stylesheet" href="./styles.css" />`
	 `</head>` 
	- Often times you will see multiple `link` elements inside a professional codebase that link to different stylesheets, fonts, and icons. Here is an example of using the `link` element to link to an external Google Font called _Playwright Cuba_:
	  `<link rel="preconnect" href="https://fonts.googleapis.com" />`
		`<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />`
		`<link`
	  `href="https://fonts.googleapis.com/css2?family=Playwrite+CU:wght@100..400&display=swap"`
	  `rel="stylesheet"`
		`/>`
	- the `preconnect` value for the `rel` attribute tells the browser to create an early connection to the value specified in the `href` attribute. This is done to speed up loading times for these external resources.
	- Another common use case for the `link` element is to link to icons. Here is an example of linking to a favicon:
	  `<link rel="icon" href="favicon.ico" />`

> HTML Boilerplate 

`<!DOCTYPE html>`
`<html lang="en">`
  `<head>`
    `<meta charset="utf-8" />`
    `<meta`
       `name="viewport"`
       `content="width=device-width, initial-scale=1.0" />`
    `<title>freeCodeCamp</title>`
    `<link rel="stylesheet" href="./styles.css" />`
  `</head>`
  `<body>`
  `</body>`
`</html>`

- `<!DOCTYPE html>` : It tells browsers which version of HTML you're using
- `<html lang = "en">...</html>` : This wraps around all your content, and can specify the language of your page.
- `<head>` : The `head` section contains important behind-the-scenes information:
- `<meta>` : site's metadata, contained in `meta` elements, has details about things like character encoding, and how websites like Twitter should preview your page's link
- `<title>` : site's title, found in the `title` element, determines the text that appears in the browser tab or window.
- Finally, you'll typically link your page's external stylesheets in the `head` section using `link` elements.
- `<body>` : The `body` section is where all your content goes:
- **WHY Boilerplate** : It ensures your pages are structured correctly and work well across different browsers. Using a boilerplate helps you avoid common mistakes and follow best practices. It's a great starting point for any web project. Remember, you can customize your own boilerplate to fit your needs. As you gain experience, you might add your own preferred elements or `meta` tags. As you continue to improve your personal boilerplate, you'll find that it saves you time when starting new projects.

> # UTF-8 Character Encoding

- UTF-8, or UCS Transformation Format 8, is a standardized character encoding widely used on the web. Character encoding is the method computers use to store characters as data. Essentially, all text on a web page is a sequence of characters stored as one or more bytes. In computing, a byte is a unit of data consisting of 8 bits, or binary digits. UTF-8 supports every character in the Unicode character set - and this includes characters and symbols from all writing systems, languages, and technical symbols.
- 