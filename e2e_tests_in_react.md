## Preamble
_End-to-end testing is a Software testing methodology to test an application flow from start to end. The purpose of End to end testing is to simulate the real user scenario and validate the system under test and its components for integration and data integrity._ 

This post outlines a strategy for writing end-to-end test/acceptance testing web-based applications. 

**There's a lot of testing strategies like it, but this one is mine. My testing strategy is my best friend. It is my life. I must master it as I must master my implementation code. Without me, my testing strategy is useless. Without my testing strategy, I am useless.**

Since you are reading this, there's a big chance that you to are looking for a testing strategy to incorporate in your workflow. There might be many reasos as to why you would want that, and I will not speculate any further. That's not my scope. If you want to write automated tests, then you do it. If not, then you don't. If reading about my workflow helps you in any way, then I'm glad I could help. If not, let's part amicably. 

## Practicalities 

If you want to use this post as a guide to implement my solution, you might have to make some adjustments to the presented code snippets.

Unlike many other posts, I will assume that you have a React application configured and upp and running. I will be using a scaffold that based on the Create React App generator. I removed the generated content and most of the css to have a clean Single Page Application to work on. 

## Let's get after it...

First things first. In order to be able to write some tests we will need to add some dependencies and configure them. I love simple things. The less code I need to write and get the results I'm after the better. 

There are some fantastic packeges out there that I leverage on to get the configuration right. 
 
Puppeteer is a Node library which provides a high-level API to control Chrome or Chromium over the DevTools Protocol. Puppeteer runs headless by default, but can be configured to run full (non-headless) Chrome or Chromium.
One is the Jest-Puppeteer library. 

Add the dependencies

```bash
$ yarn add -D puppeteer jest-puppeteer expect-puppeteer
// or 
$ npm install -D puppeteer jest-puppeteer expect-puppeteer
```

Create a `.eslintrc.js` file in your root folder:

```javascript
module.exports = {
  env: {
      es6: true,
      jest: true,
  },
  globals: {
      page: true,
      browser: true,
      context: true,
      jestPuppeteer: true,
  },
}
```

Create a `jest.config.js` file in your project root folder:

```javascript
module.exports = {
  verbose: true,
  preset: "jest-puppeteer",
  "setupTestFrameworkScriptFile": "expect-puppeteer",
  testRegex: ".feature|e2e\\.js$",
  globals: {
    appURL: "http://localhost:3001"
  }
};
```

Create a `jest-puppeteer.config.js` file in your project root folder:

```javascript
module.exports = {
  launch: {
    headless: false,
    slowMo: 100,
    devtools: true,
    args: [
      '--disable-setuid-sandbox',
      '--no-sandbox',
      '--ignore-certificate-errors',
      "--disable-popup-blocking",
      "--disable-infobars",
      '--disable-web-security'
      ]
  },
  browserContext: 'default',
  server: {
    command: `BROWSER=none npm run start`,
    port: 3001,
    launchTimeout: 4000,
  }
}
```
### The first feature

In your `src` folder, go ahead and create a folder named `__features__`.  In that folder, we can go ahead and create our first feature file. Let's call it `userCanSeeAGreeting.feature.js` or something appropriate.

```javascript
describe('User visits the site and', () => {

  beforeAll(async () => {
    await page.goto(appURL);
  });

  beforeEach(async () => {
    await page.reload();
  })

  it('see a greeting', async () => {
    await expect(page).toMatchElement('#main', {
      text: 'Hello Stranger!'
    })
  })
})
```




