 1. AIO 
	1. testing framework
	2. Assertion Library
	3. with mocking and 
	4. Stubbing 
2. E2E Component testing
3. Wrote in Javascript and runs in browser
4. Can be integrated in CI/CD process
5. native access to the DOM


**Must checks**
**Cypress :**
- docs : https://docs.cypress.io/app/get-started/why-cypress 
	- **Important :** *Assertions* : https://docs.cypress.io/app/references/assertions#__docusaurus_skipToContent_fallback 
		- Chai assertion library : https://www.chaijs.com/guide/helpers/
	- **intercepts :** https://docs.cypress.io/api/commands/intercept#__docusaurus_skipToContent_fallback 
	- **Cypress methods you need to know :** https://learn.cypress.io/advanced-cypress-concepts/important-cypress-methods-you-need-to-know
	- **Read from an external file** : https://docs.cypress.io/api/commands/readfile
		- *read from xlsx document* : https://dev.to/aswani25/how-to-read-and-write-from-excel-files-in-cypress-352h
		- *read from JSON doc :* 
		  `cy.readFile('path/to/data.json').its('name').should('eq', 'Eliza')`
		- read for external files using `fixtures()` : https://www.youtube.com/watch?v=-hn5uKczmKw
	- **Check font colors** : 
		- `cy.get('.my-element').should('have.css', 'color', 'rgb(255, 0, 0)'); // Asserts that its text color is red`
