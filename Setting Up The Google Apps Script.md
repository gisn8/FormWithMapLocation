First, create a new Google Sheets document and then open Google Apps Script by going to Extensions -> Apps Script.

Copy the contents of the gScript.js.template and paste it into the Apps Script editor.

```
function doPost(e) {
  var sheet = SpreadsheetApp.openById('YOUR_SPREADSHEET_ID_HERE').getActiveSheet();
  var newRow = sheet.getLastRow() + 1;
  
  var rowData = [];
  rowData.push(new Date()); // Timestamp
  rowData.push(e.parameter.home);
  rowData.push(e.parameter.name);
  rowData.push(e.parameter.age);
  rowData.push(e.parameter.description);
  rowData.push(e.parameter.latitude);
  rowData.push(e.parameter.longitude);
  
  sheet.getRange(newRow, 1, 1, rowData.length).setValues([rowData]);
}
```
Replace 'YOUR_SPREADSHEET_ID_HERE' with your Google Sheets document's ID.

Now, deploy this as a web app:

1. Save the script.
2. Click on the floppy disk icon or File -> Save.
3. Go to Publish -> Deploy as web app.
4. Set 'Who has access to the app:' to 'Anyone, even anonymous'.
5. Click 'Deploy'.

You will get a URL. This will go into your config.js file or you can apply it directly into the html file replacing "gScriptUrl" in the **POST data to Google Apps Script web app** section. This will send your form data directly to the Google Sheet associated with the Google Apps Script.
