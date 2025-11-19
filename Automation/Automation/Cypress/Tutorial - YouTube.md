**You tube tutorial source :** 
- https://www.youtube.com/watch?v=u8vMu7viCm8
- app link - https://cypress-course.vercel.app/
- Repo : https://github.com/coderyansolomon/cypress-course.git


**Steps :** 

***Overview and install :***

1. VS Code : `git clone <repository>`
2. VS Code : Enter the newly loaded folder and run 
	1. `npm install`  *(this will install the dependencies)* 
3. VS Code : run the app but entering 
	1. `npm run dev` *(This will launch the app in the local server)*
	2. local server :  http://localhost:3000
	3. This local host needs to be kept alive
4. VS Code : open up a new terminal 
	1. Install Cypress
	2. `npm install cypress --save-dev`
5. VS Code : Open and configure cypress
	1. `npx cypress open`
6. Cy Test Runner : Select E2E testing 
7. Cy Test Runner : Config files will get auto generated and `Continue`
8. Cy Test Runner : Choose Browser and `Start E2E Testing ...`
9. Cy Test Runner : `Create new spec`
	1. `Spec` files aka `Test` files 
10. Cy Test Runner : rename the spec file name to *fundamentals.cy.js* and `Create Spec` 
	1. `cypress/e2e/fundamentals.cy.js`
11. Cy Test Runner : `Okay. run the spec`
12. VS Code : new list of folder and files get auto generated. 
	1. Cypress
		1. `downloads`
		2. `e2e` - `fundamentals.cy.js` file got stored 
		3. `fixtures` - 
		4. `support` - to include custom commands and other configurations 
	2. `cypress.config.js` file - to setup other configurations and stuffs

***Testing Fundamentals :***

1. `describe` block 
	1. takes 2 arguments 
		1. Description of the test/spec [String]
		2. A Callback function : this will contain all the tests 
		3. *Overall test File* is `describe` block
2. `it`block 
	1. contains single tests within an overall test file
	2. similar to `describe` block
	3. takes 2 arguments 
		1. Description of the individual test
		2. Callback function - Contains `test code`
	4. Contains *Individual tests* for the overall `describe` block 
3. Commands and Interacting with elements 
	1. `cy` object for the commands
		1. example : `cy.visit('/')` - this navigates the cypress runner to `base url` (configured)* [cypress docs : ## Actionability section]
4. VS Code : update URL in the fundamentals.cy.js file to point to local host
	1. local host : http://localhost:3000/fundamentals [Dev server needs to be kept running]
5. **Getting Elements**
6. Command Chaining and assertion 
7. Focusing on a single test
	1.  Run the app in CY test runner
	2. CY test runner : Go to inspect more and select the "Test Fundamentals" heading
8. Added the following to get the web elements from the app 
	1. `cy.get('[data-test = "fundamentals-header"]').contains('Testing Fundamentals')`
		1. `...contains(/Testing Fundamentals/i)` - this will make it case insensitive 
	2. `cy.get('[data-test = "fundamentals-header"]').should('contain.text','Testing Fundamentals')` => this is an assertion
	3. added ' *data-test = "fundamentals-header"*' in the react page.jsx file under the `h1` tag
9. Setting up Base URL in the cypress code
	1. go to `cypress.config.js` file
	2. Include "*baseURL*" attribute to *e2e*
		1. `baseUrl: 'http://localhost:3000',`  *(note : baseUrl is is case sensitive)* 
	3. In the *e2e/fundamentals.cy.js* file add the following 
		1. `cy.visit('/fundamentals')`
10. Testing open and close functionality of the collapsible menu 
	1. as there are duplicate ID for multiple elements, need to add a unique attribule
		1. `data-test = {`accordion-item-${item.id}`}` (in the react *accordion.jsx* file)
		2. when closing it is tapping on the text, so add the role button to the get element query 
			1. `cy.contains("Your tests will exist in a describe block.").should('not.be.visible')`
			2. `cy.contains("Your tests will exist in a describe block.").should('not.be.visible')`
11. focus on ONLY on test among the "*Describe*" suite 
	1. add **only** with the `it`
		1. `it.only('Accordion is workling correctly',() => {...})`
12. `before each` command //*Best Practice*
	1. `beforeEach(() = > {cy.visit('/fundamentals')})`
13. User can use custom cypress command
	1.  location *cypress/support/commands.js*
	2. customizing `cy.get('[data-test....]')`
	3. `Cypress.Commands.add('getDataTest', (dataTestSelector) => {...})`
	4. `{...}` = `return cy.get(`[data-test ="${dataTestSelector}"]`)`


***Testing Forms***

1. General coding of cypress
2. negative testing 
3. Using Aliases
	1. ` cy.getDataTest('subscribe-form').find('input').as('subscribe-input')`


***Examples :***

1. Multi Page testing 
	1.  `cy.location('pathname').should('equal','/')`
2. Intercept
	1. ` cy.intercept('POST','http://localhost:3000/examples',{ body: { message: 'Successfully intercepted the request'}})`


***Helpful Methods :*** 

1. `cy.its()` 
2. `cy.invoke()`
3. `cy.request()`
4. `cy.within()`

***Grudge List***

1. used `cy.within()`
2. used `cy.its()`

***Component test :***

1. Reopen cypress by `npx cypress open`
2. CY test runner : Select Component testing 
3. CY test runner : Select *Next* (install any Next related dependencies)
4. CY test runner : Select Chrome 
5. CY test runner : Create new specs
6. CY test runner : Rename the file *cypress\component\Accordion.cy.jsx*  
7. VS Code : similar to usual e2e testing
8. e2e vs component test : *...the main difference is that Cypress Component Testing builds your components using a development server instead of rendering within a complete website...*
	1. no need to login to application or authentications
	2. no need to navigate to the reach the component 
	3. mount a component using `cy.mount()`
9. Getting **ERROR** compiling >> ***NEED TO RETURN BACK HERE***


***NOTES :***
- Cypress has an Asynchronous nature 
	- Cypress **DO NOT** return their subjects 
	- **NOT** recommended to use *variables*
	- **Recommended** to use *Yield* their subjects
- Retry-ability
	- Aliases 
		- `cy.get("table").find("tr").as(rows)`
		- `cy.get(rows)` 