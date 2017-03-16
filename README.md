# Protractor Testing Framework to test AngularJs Application

## A complete Automation Testing framework built on AngularJs javascript using Node.js

### Protractor Installation

Steps to get Protractor working on MAC, windows should be same.


1. - In the Terminal

    Run this command - npm install -g protractor

    Everything should be green, if there is permission issue,

            type 'sudo npm install -g protractor'

2. - Create a test new folder you can name it anything, inside

   A)  Make a file called - test.js
           Inside the file copy and paste the following
           
            describe("Go to the Homepage ", function(){
            browser.ignoreSynchronization=true; // This allows to protractor to run on regular website, not specific to angular 
            it("Go to the Home page ", function(){
            browser.get("http://ornaitjewels.com/"); // Go to a specific URL
             console.log("Home Page Open succesffully") // Log a message
            });
   
             // From the Home Page go to the  Pendant Page 
             it("Go to Pendants Page ", function(){
             var pendants = element(by.css("#tm_menu > div > ul > li:nth-child(2) > a")); // set a variable for action
            pendants.click(); // Click on element
            browser.sleep(1000) // Tell Protractor to Wait for 1000 miliseconds or 1sec
            console.log("From the Home Page go to the Pendant Page "); 
            element(by.css("#content > div:nth-child(2) > div:nth-child(1) > div.product-thumb.transition.options > div.caption > div >                 a")).click(); // Go the element and Click
            // browser.sleep(1000)
            console.log("Go to a specific Product Page");
            // browser.sleep(1000)
            browser.navigate().back(); // Tell the browser to go back 
            });
          });
   
   B) Make a new file called - conf.js
       Inside the file copy and paste the following
       
           exports.config = {
          directConnect: true,
          capabilities:{
          'browserName': 'chrome'},
          framework: 'jasmine2',
          specs: ['test.js']
          };
        

3. -  Now open a new terminal
          >  Navigate to directory you created. cd DemoTest
          >  which should have two file you just created todo-spec.js and conf.js
          > now just run command  protractor conf.js

**This should work for everyone.. **
