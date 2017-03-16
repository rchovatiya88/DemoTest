# Protractor Testing Framework to test AngularJs Application

## A complete Automation Testing framework built on AngularJs javascript using Node.js

### Protractor Installation

Steps to get Protractor working on MAC, windows should be same.


Step 1 - In the Terminal

    Run this command - npm install -g protractor

    Everything should be green, if there is permission issue,

            type 'sudo npm install -g protractor'

Step 2 - In the same Terminal window,
    Run this command - webdriver-manager update
        This is will download the latest version of selenium server automatically.

Step 3 - Now we have to start the server, So run the following command

        webdriver-manager start

        Ensure no errors..

Step 4 - Create a test new folder you can name it anything, inside

    A)   Make a file called - todo-spec.js
           Inside the file copy and paste the following

           ```javascript
           describe('angularjs homepage todo list', function() {
              it('should add a todo', function() {
                browser.get('https://angularjs.org');

                element(by.model('todoList.todoText')).sendKeys('write first protractor test');
                element(by.css('[value="add"]')).click();

                var todoList = element.all(by.repeater('todo in todoList.todos'));
                expect(todoList.count()).toEqual(3);
                expect(todoList.get(2).getText()).toEqual('write first protractor test');

                // You wrote your first test, cross it off the list
                todoList.get(2).element(by.css('input')).click();
                var completedAmount = element.all(by.css('.done-true'));
                expect(completedAmount.count()).toEqual(2);
              });
            });
          ```

    B)    Make a new file called - conf.js

           Copy and paste the following
           ```javascript
               exports.config = {
              seleniumAddress: 'http://localhost:4444/wd/hub',
              specs: ['todo-spec.js']
            };
            ```

Step 5 -  Now open a new terminal
          >  Navigate to directory you created. cd/newtestdir
          >  which should have two file you just created todo-spec.js and conf.js
          > now just run command  protractor conf.js

**This should work for everyone.. **
