## Google Apps Script QUnit Key Points:
1. Tests are run on Google's servers, not in your browser. The browser only displays test result.
2. Configuration is required by calling `QUnit.config(myConfig)`, where `myConfig` is an object in your configuration settings.
3. The GAS service running the tests need to implement a `doGet(e)` function that:
  * Calls `QUnit.urlParams(e.parameter)`, which ensures that QUnit-specific HTTP parameters are handled when you interact with the QUnit GUI;
  * Optionally, it configures QUnit with the `QUnit.config()` function;
  * Loads test with `QUnit/load(myTests)`, where `myTests` is a function containing your tests;
  * Returns the result of `QUnit.getHtml();`
  * Some helper functions can be imported from QUnit to the test suite by calling `QUnit.helpers(this).`

##Steps for adding 'QUnit' in your project:
1. Open the script editor
2. Go to 'Resources > Libraries'
3. Enter project key (MxL38OxqIK-B73jyDTvCe-OBao7QLBR4j) in the 'Find the Library' field. Click 'Select'
4. Select most recent version, choose QUnit as the identifier (Do not use Development Mode), then click 'Save'
5. All available functions show by typing QUnit followed by a dot. Alternatively, read the [API docts](https://script.google.com/macros/library/versions/d/MxL38OxqIK-B73jyDTvCe-OBao7QLBR4j)
