# ASINs to Hyperlinks
Convert ASINs from Amazon reports into hyperlinks.

Google Sheets > Extensions > App Script
Paste the code below > save > click "run" > grant permissions

```javascript
function createAmazonLinks() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var data = sheet.getDataRange().getValues();
  
  // This assumes ASINs are in column A
  for (var i = 1; i < data.length; i++) {
    var asin = data[i][0];
    var link = "https://www.amazon.com/dp/" + asin;
    var range = sheet.getRange(i + 1, 1);
    range.setValue('=HYPERLINK("' + link + '", "' + asin + '")');
  }
}
```
