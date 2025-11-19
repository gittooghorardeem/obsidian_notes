1. `npm init playwright@latest` - for new or existing project
2. run test : `npx playwright test`
3. Show report : `npx playwright show-report`
4.  Some npx commands 
	1. `npx playwright test` - Runs the end-to-end tests.
	2. `npx playwright test --ui` - Starts the interactive UI mode  **
	3. `npx playwright test --project=chromium` - Runs the tests only on Desktop Chrome
	4. `npx playwright test example`- Runs the tests in a specific file.
	5. `npx playwright test --debug` - Runs the tests in debug mode.
	6. `npx playwright codegen` - Auto generate tests with Codegen.
5. Show the tests in real time - `npx playwright test --headed`

**Random Snippets**

- `require` - 
- `expect()`
- playwright method use - `async` at the function level
- playwright method use - `await` 
- `test('test 1', async function({page}){})`
- use fixed view port : `test.use({viewport:{width:1920, height:1080}})` - *login.spec.js*
- Codegen : `npx playwright codegen`
	- `npx playwright codegen https://opensource-demo.orangehrmlive.com/web/index.php/auth/login -o ./e2e/codegen.spec.js` - store the auto generated code in a directory
- Before each : 
	- `test.beforeEach(async ({ page }) => { await page.goto('https://www.example.com'); });`
- POM - Page object model creation 
	- [google query](https://www.google.com/search?q=can+you+set+an+alias+for+repeatedly+used+web+elements+in+playwright+in+js&sxsrf=AE3TifMwkqOd7gSpOzu4RxbuFuJ-VEjDRQ%3A1761732973295&udm=50&aep=10&ntc=1&mtid=EuoBabHoJ-Tp4-EPyt_IuQs&mstk=AUtExfBzhGJVjU07PUpRS193aShwLAN16hw6UPv51Q3fS5tN51iEYjBUGU-KUT2warjk4qg07clum6fuY-Dr46O-L2Wh4SLbVqz4FI1CU1kSM9TF-qyfc9zvIFSqot0l-WD0VYUrf_6OsaSt2bfVzROInjv_wkPALT-j1i-JAy8daR6MsB90XdNDUZNB5-h6dB2NfMeRIok4wnaRdY0IszA0iwMeqdb9z6Qm2YHhWhRHf0Bn8eX4_IF6l3TplmF-AIaLkddgVNDpQVqxVDj1sb45IGp0tcNfbN1pc1i5Fm4l4XM_l9z5jVNruHutKlLhKvKDsIrvlpSWalzG3bJYHo2Eus9MHqAh60lNsg&csuir=1) 
- **New tab check** - https://www.youtube.com/watch?v=VtgqD_ksHNg
- **Fixtures :**
	- https://www.youtube.com/watch?v=2O7dyz6XO2s
- **Export external data**
	- [google query](https://www.google.com/search?q=why+i+am+getting+locator%28%27text%3D%5C%27div+input%5Bname%3D%22email%22%5D%5C%27%27%29&sxsrf=AE3TifOzLV1loaOKdrJBfdi-AbCrkxsvvA%3A1761804060970&udm=50&aep=10&ntc=1&mstk=AUtExfAXLoMbbV1R6V4u2ZKGMnNA-mpg38Jz1YpxCg75Yy57r2nA0e7vSBa1rkNetXLRRSKVGhwnufA6vzBTgef4PVrMNBet-z3yUQd7Qwf2PSGt01Sh0P31qddDHGXtzTG8-QXyWAaYXqPM9SHWJfyXG6Jnb9iDzm0FaI6F3xBDC_8Cku6Jq8evyQrfF5wJ4f3FBbNUfn-l5F0YEEkZbJONzyDUAMToObFokTRsutEGiTsSZh5vCLCaS86eEBQZU58FL_UuvS7jmwxBIQycyAainv1DXvSdxmQMWLX83ITqzuBB4-y6zEaoikqouyxfCuRrk9HXAwOxJgTflQ&csuir=1&mtid=gQQDacLmJ7nC4-EP39mXuQw)
- **List items check :**
```
const listItems = page.getByRole('listitem')
const expectedItems = ['Order Dashboard','Add Order',
                        'Analytics','Menu','Inventory',
                        'Brand','Location','User','Reservation',
                        'Customer Hub','Live Monitor',
                        'Printer Settings','Links','Activity Log']

for(let i = 0; i < expectedItems.length; i++){
	await expect(listItems.nth(i)).toHaveText(expectedItems[i])
}
```

> **Report Generation**

- Allure Reporting
	- `package.json` : under `dependecies` 
		- `"allure-playwright": "3.4.2"`
		-  then run `npm install` : this will install the allure packages
		- update the `playwright.cofig.json` file `reporter` data : 
			- `reporter: [
			    ['html'],
			    ['dot'],
			    ['list'],
			    ['allure-playwright'],
			    ['json',{outputFile: 'report.json'}]
			  ]`
		- simply running the playwright test file will generate the allure reporting file 
		- install allure commandline
			- `npm install -D allure-commandline`
		- ` npx allure generate ./allure-results --clean` - this will  generate the report
		- `npx allure open .\allure-report\` - this will open the report
		- YT link : https://www.youtube.com/watch?v=u0KyDdYxALI
		- **NOTE >>** system is required to have java installed.  
- Default Reporting
	- `playwright.cofig.json` - reporter
- 