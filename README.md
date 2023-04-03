# ASINs to Hyperlinks
Convert ASINs from Amazon reports into hyperlinks.

Google Sheets > Extensions > App Script
Paste the code below > save > click "run" > grant permissions

```javascript
function createAmazonLinks() {
  var sheet = SpreadsheetApp.getActiveSheet();
  var data = sheet.getDataRange().getValues();

  for (var i = 0; i < data.length; i++) {
    for (var j = 0; j < data[i].length; j++) {
      var cell = data[i][j];
      if (typeof cell === "string" && cell.match(/^B0[0-9A-Z]{8}$/)) {
        var asin = cell;
        var link = "https://www.amazon.com/dp/" + asin;
        var range = sheet.getRange(i + 1, j + 1);
        range.setValue('=HYPERLINK("' + link + '", "' + asin + '")');
      }
    }
  }
}
```
