SauceDemo Playwright Automation
This project contains automated end-to-end tests for the SauceDemo web application using Playwright and TypeScript. The tests cover login functionality and shopping cart actions, following the Page Object Model for maintainability and scalability.

Table of Contents
Project Structure
Prerequisites
Installation
Configuration
Running the Tests
Writing Tests
Extending the Framework
Troubleshooting
License
Project Structure

.├── src/│   └── pages/│       ├── login-page.ts│       └── inventory-page.ts│   └── data/│       └── test-users.ts├── tests/│   └── inventory.spec.ts├── playwright.config.ts├── package.json└── README.md
src/pages/: Page Object Model classes for different pages.
src/data/: Test data such as user credentials.
tests/: Test specifications.
playwright.config.ts: Playwright configuration.
package.json: Project dependencies and scripts.
Prerequisites
Node.js (v16 or higher recommended)
npm or yarn
Internet connection (for SauceDemo site)
Installation
Clone the repository:


git clone <your-repo-url>cd <repo-folder>
Install dependencies:


npm install
or


yarn install
Install Playwright browsers:


npx playwright install
Configuration
Base URL:
By default, tests run against https://www.saucedemo.com/.
To override, set the BASE_URL environment variable:


set BASE_URL=https://your-custom-url.com
Test Users:
User credentials are managed in test-users.ts.

Running the Tests
Run all tests:


npx playwright test
Run a specific test file:


npx playwright test tests/inventory.spec.ts
Run tests with UI (headed mode):


npx playwright test --headed
View HTML report:


npx playwright show-report
Writing Tests
Tests are written in TypeScript using Playwright’s test runner.

Page Object Model is used for maintainability.

Example test (inventory.spec.ts):


test('should add an item to the cart', async ({ page }) => {  const inventoryPage = new InventoryPageWithCart(page);  await expect(await inventoryPage.isLoaded()).toBeTruthy();  await inventoryPage.addItemToCart('sauce-labs-backpack');  expect(await inventoryPage.getCartBadgeCount()).toBe(1);});
Extending the Framework
Add new page objects:
Create a new file in pages and extend the base Page class.
Add new tests:
Create a new .spec.ts file in the tests directory.
Add new test data:
Update or add files in data.
Troubleshooting
Browsers not launching:
Run npx playwright install to ensure all browsers are installed.
Environment variables not set:
Double-check your BASE_URL or other environment settings.
Test failures:
Use Playwright’s trace viewer or HTML report for debugging.
License
This project is for educational and demonstration purposes.
See LICENSE for more details.

Happy Testing!