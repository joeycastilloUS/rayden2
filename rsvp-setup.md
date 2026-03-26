# RSVP Google Sheets Setup

## Step 1: Create the Google Sheet

1. Go to https://sheets.google.com
2. Create a new spreadsheet
3. Name it: "Rayden's Birthday RSVP"
4. In Row 1, add these headers:
   - A1: `Timestamp`
   - B1: `Name`
   - C1: `Guests`
   - D1: `Message`

## Step 2: Create the Apps Script

1. In the spreadsheet, click **Extensions > Apps Script**
2. Delete everything in the editor
3. Paste this code:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);

  sheet.appendRow([
    new Date(),
    data.name || '',
    data.guests || '',
    data.message || ''
  ]);

  return ContentService
    .createTextOutput(JSON.stringify({ status: 'ok' }))
    .setMimeType(ContentService.MimeType.JSON);
}
```

4. Click **Save** (Ctrl+S), name the project "RSVP Handler"

## Step 3: Deploy as Web App

1. Click **Deploy > New deployment**
2. Click the gear icon, select **Web app**
3. Set:
   - Description: "Rayden RSVP"
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Click **Deploy**
5. Authorize when prompted (click through the "unsafe" warning — it's your own script)
6. **Copy the Web app URL** — it looks like: `https://script.google.com/macros/s/ABC.../exec`

## Step 4: Update the Site

Replace `YOUR_APPS_SCRIPT_URL` in index.html with the URL from Step 3.

That's it! RSVPs will appear in the Google Sheet automatically.
