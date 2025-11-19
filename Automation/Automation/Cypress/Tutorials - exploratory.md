**Quick looks :**

1. for placeholder text assertions 
	1. `cy.get('form div input[id = "username"]').should('have.attr', 'placeholder', 'Type your email here')`
2. to open the redirect link in the same tab
	1. `cy.get('div div[class="mt-4 mb-8 text-sm text-grey-darker"] a[class="no-underline text-primary"]').invoke('removeAttr','target').click()`
	2. source : https://www.youtube.com/watch?v=JLAgP3R-WMc
3. Using `fixture()` to user data from external files 
	1. `cy.fixture('kUserData.json').then(kUserEmail =>{kUserData = kUserEmail})`
	2. ~~Using as alias : `cy.fixture('users.json').as('userData')`~~
