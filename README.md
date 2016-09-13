## Google Apps Script QUnit Key Points:
1. Tests run on Google's servers, not in the browser. The browser only displays test results.
2. Configuration is required by calling `QUnit.config(myConfig)`, where `myConfig` is an object in your configuration settings.
3. The GAS service running the tests need to implement a `doGet(e)` function that:
  * Calls `QUnit.urlParams(e.parameter)`, which ensures that QUnit-specific HTTP parameters are handled when you interact with the QUnit GUI;
  * Optionally, it configures QUnit with the `QUnit.config()` function;
  * Loads test with `QUnit/load(myTests)`, where `myTests` is a function containing your tests;
  * Returns the result of `QUnit.getHtml();`
  * Some helper functions can be imported from QUnit to the test suite by calling `QUnit.helpers(this).`

##Steps for adding QUnit in your project:
1. Open the script editor
2. Go to 'Resources > Libraries'
3. Enter project key (**MxL38OxqIK-B73jyDTvCe-OBao7QLBR4j**) in the 'Find the Library' field. Click 'Select'
4. Select most recent version, choose QUnit as the identifier (Do not use Development Mode), then click 'Save'
5. All available functions show by typing QUnit followed by a dot. Alternatively, read the [API docs](https://script.google.com/macros/library/versions/d/MxL38OxqIK-B73jyDTvCe-OBao7QLBR4j)

####**Sample code:**
```javascript
function calculuateAmountAndQty(quantity,amount){
  if(typeof {quantity) == 'undefined' || quantity == 'null' || isNaN(quantity)) {
    quantity=0;
  }

  if(typeof (amount) == 'undefined' || amount == 'null' || isNaN(amount)) {
    amount=0;
  }

  return (quantity*amount);
  }
```
#### Test cases for above code:
```javascript
 QUnit.helpers( this );
  function testFunctions() {
    testingCalculateAmountAndQty();
  }

  function doGet( e ) {
      QUnit.urlParams( e.parameter );
      QUnit.config({
        title: 'QUnit for GAS - Test Suite'  // Sets the title of the test page
      });
      QUnit.load( testFunctions );

      return QUnit.getHtml();
  };

  function testingCalculateAmountAndQty(){
    QUnit.test( "calculateAmountAndQty testing", function() {
      expect(7);
      equal( calculateAmountAndQty(10,2), 20, "Test for quantity : 10 and amount : 2 so output is 20" );
      equal( calculateAmountAndQty("poop",2), 0, "Test for quantity : poop and amount : 2 so output is 0" );
      equal( calculateAmountAndQty(5,"puppy"), 0, "Test for quantity : 5 and amount : puppy so output is 0" );
      equal( calculateAmountAndQty(null,24), 0, "Test for quantity : null and amount : 24 so output is 0" );
      equal( calculateAmountAndQty(3,null), 0, "Test for quantity : 3 and amount : null so output is 0" );
      equal( calculateAmountAndQty(undefined,4), 0, "Test for quantity : undefined and amount : 4 so output is 0" );
      equal( calculateAmountAndQty(7,undefined), 0, "Test for quantity : 7 and amount : undefined so output is 0" );
   });
  }
```

####Steps to Run QUnit Test Case:
1. 'Publish' > 'Deploy as Web App'
2. Click 'Deploy'
3. Click on latest code (redirects to QUnit page where all test case report is displayed)


####For more reference:
See [QUnit](https://qunitjs.com).
