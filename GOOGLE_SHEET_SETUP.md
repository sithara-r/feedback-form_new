# How to Set Up Your Google Sheet Storage

Follow these steps to connect your Principal Feedback Form to a Google Sheet.

## Step 1: Prepare the Google Sheet
1. Create a new Google Sheet.
2. In the first row, add the following headers (optional, but good for organization)7.  **A1**: Timestamp
8.  **B1**: Principal Name
9.  **C1**: Designation
10. **D1**: Email-Id
11. **E1**: Branch
12. **F1**: Session Progress Rating
13. **G1**: Session Regularity
14. **H1**: Trainer Effectiveness
15. **I1**: Teacher Deployment Satisfaction
16. **J1**: Exhibition Prep Rating
17. **K1**: Wizklub Day Status
18. **L1**: Exhibit Learning (Rating)
19. **M1**: Exhibit Confidence (Rating)
20. **N1**: Exhibit Engagement (Rating)
21. **O1**: Exhibition Best Part
22. **P1**: Recommend Wizklub
23. **Q1**: Renewal Expectation

## Step 2: Create the Apps Script
1. In your Google Sheet, go to **Extensions** > **Apps Script**.
2. Delete any existing code and paste the following:

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = e.parameter;
  
  // Append a new row with the form data
  sheet.appendRow([
    data.timestamp || new Date().toLocaleString(),
    data.principal_name,
    data.designation,
    data.email_id,
    data.branch,
    data.rating_punctuality,
    data.rating_conduct,
    data.renewal_expectation,
    data.improvement_recommendations,
    data.session_progress_rating,
    data.session_regularity,
    data.trainer_effectiveness,
    data.teacher_deployment_satisfaction,
    data.exhibition_prep_rating,
    data.wizklub_day_status,
    data.exhibit_learning,
    data.exhibit_confidence,
    data.exhibit_engagement,
    data.exhibition_best_part,
    data.recommend_wizklub,
    data.renewal_expectation_v2
  ]);
  
  // Return a success response to the form
  return ContentService.createTextOutput("Success")
    .setMimeType(ContentService.MimeType.TEXT);
}
```

## Step 3: Deploy as a Web App
1. Click the **Deploy** button at the top right and select **New deployment**.
2. Select **Web app** as the type.
3. In the "Description", type "Feedback Form API".
4. Set "Execute as" to **Me**.
5. Set "Who has access" to **Anyone**. (This is important so the form can send data without a login).
6. Click **Deploy**.
7. Copy the **Web App URL** provided.

## Step 4: Connect to your Code
1. Open `script.js` in your project.
2. Replace `YOUR_GOOGLE_APPS_SCRIPT_URL_HERE` with the URL you just copied.
3. Save the file.
