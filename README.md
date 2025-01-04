# Strava to Google Sheets Integration

## Overview

This script fetches your recent running activities from the **Strava API**, processes the data (e.g., time for 6.7 km, total distance, and total time), and updates a specified **Google Sheets** document with the results. It ensures data consistency by checking if entries for the last 7 days already exist before adding new data.

---

## Prerequisites

1. **Python Environment**:
   - Install Python 3.8 or later.

2. **Google Cloud Setup**:
   - Enable the **Google Sheets API** and **Google Drive API** in your [Google Cloud Console](https://console.cloud.google.com/).
   - Create a **Service Account** and download the JSON credentials file.

3. **Strava API Setup**:
   - Create a Strava application via the [Strava Developers Portal](https://developers.strava.com/).
   - Obtain your `client_id`, `client_secret`, and `refresh_token`.

4. **Google Sheet**:
   - Create a Google Sheet and share it with the service account email (e.g., `your-service-account@<project-id>.iam.gserviceaccount.com`).
   - Ensure the Google Sheet has a tab named `data`.

---

## Setup

### 1. Clone the Repository

### bash
git clone https://github.com/your-repository-name.git
cd your-repository-name

2. Install Required Dependencies
Install the required Python libraries:

bash
Kopiera kod
pip install requests gspread google-auth
3. Configure Environment Variables
Create a .env file in the project root and add the following variables:

plaintext
Kopiera kod
CLIENT_ID=your_strava_client_id
CLIENT_SECRET=your_strava_client_secret
REFRESH_TOKEN=your_strava_refresh_token
CREDENTIALS_FILE=path_to_your_google_credentials.json
SPREADSHEET_ID=your_google_spreadsheet_id
Replace the placeholders with your actual values:

your_strava_client_id: Strava API client ID.
your_strava_client_secret: Strava API client secret.
your_strava_refresh_token: Refresh token obtained from Strava.
path_to_your_google_credentials.json: Path to the Google Service Account JSON file.
your_google_spreadsheet_id: The unique ID of your Google Sheet (from the URL).
Running the Script
Run the script using Python:

bash
Kopiera kod
python script_name.py
Expected Output
The script will:

Fetch running activities from Strava for the last 7 days.
Calculate:
Total distance.
Total time.
Time for 6.7 km.
Update the specified Google Sheet in the data tab.
Example Google Sheet Output:

Date	Time for 6.7km	Total Distance	Total Time
2025-01-01	01.15.30	10,00	01.30.00
2025-01-02	01.12.45	12,00	01.25.30
Features
Strava Integration:

Fetches recent activities using the Strava API.
Filters for "Run" activities only.
Data Processing:

Calculates:
Total Distance: Formatted with a comma , as the decimal separator (e.g., 10,00).
Total Time: Converted to hh.mm.ss format (e.g., 01.30.00).
Time for 6.7 km: Extrapolated based on average pace.
Google Sheets Integration:

Authenticates with Google Sheets using a service account.
Updates the data tab in a Google Sheet, ensuring no duplicate entries for the last 7 days.
Notes
Custom Date Formats:

Dates are formatted as YYYY-MM-DD.
Times are in hh.mm.ss format.
Distances use a comma , as the decimal separator.
Error Handling:

Ensure your Google Sheet is shared with the service account email.
Verify that your Strava API tokens are valid and the required scopes (read, activity:read) are granted.
Debugging:

To debug the script, print responses from the Strava API or Google Sheets updates using print() statements.
Troubleshooting
Common Errors
401 Unauthorized (Strava API):

Ensure your refresh token is valid.
Verify the client_id, client_secret, and refresh_token in your .env file.
Check if the required scopes (read, activity:read) are enabled for your Strava app.
Google Sheets API Errors:

Ensure the Google Sheet is shared with the service account email.
Verify that the Google Sheets API is enabled in the Google Cloud Console.
Check the SPREADSHEET_ID and TAB_NAME for accuracy.
Invalid Data Formatting:

Ensure that distances are formatted as floats (e.g., 10.00) before replacing the decimal separator with a comma.
Contributing
Feel free to submit pull requests or file issues to improve the functionality or address bugs.

License
This project is licensed under the MIT License. See the LICENSE file for details.

vbnet
Kopiera kod

You can copy and paste this markdown into your `README.md` file directly. Let me know if you ne
