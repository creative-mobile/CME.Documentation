# Getting Started with CME CloudPurchase

Установка CME CloudPurchase состоит из X шагов.

## <a id="install"></a> Install the Unity plugin

// Скачай с asset store

## <a id="aws-credentials"></a> Get your AWS security credentials

Если нет аккаунта, хлебни лиха — https://aws.amazon.com/ru/premiumsupport/knowledge-center/create-and-activate-aws-account/

To generate security credentials

In the IAM console, open the Access Management, Users page and select the user that you want to generate credentials for.

On the user detail page, open the Security credentials tab.

Go to the Access keys section and choose Create access key.

When the access key is generated, you can view both the access key ID and the secret access key, which together are the access key. Copy both of the access key values, or download them as a .CSV file to a local drive.

## <a id="deployment"></a> Make your first deployment

// Гифка c развертыванием

// Гифка с проверкой

## <a id="stores"></a> Configure stores integrations

Collect your Google credentials
Tip: If you see Google Play Console or Google Developer Console in your local language, add &hl=en at the end of the URL (before any #...) to switch to English.

Open the Google Play Console
- Click Account Details, and note the Developer Account ID listed there
- Click Setup → API access
- Click the Create new service account button
- Follow the Google Cloud Platform link in the dialog, which opens a new tab/window:
- Click the CREATE SERVICE ACCOUNT button at the top of the Google Cloud Platform Console
- Verify that you are on the correct Google Cloud Platform Project by looking for the Developer Account ID from earlier within the light gray text in the second input, preceding .iam.gserviceaccount.com. If not, open the picker in the top navigation bar, and find the one with the ID that contains it.
- Provide a Service account name and click Create
- Click Select a role, then find and select Service Account User, and proceed
- Click the Done button
- Click on the Actions vertical three-dot icon of the service account you just created
- Select Manage keys on the menu
- Click ADD KEY -> Create New Key
- Make sure JSON is selected as the Key type, and click CREATE
- Save the file on your computer when prompted and remember where it was saved to
- Return to the Google Play Console tab, and click DONE to close the dialog
- Click on Grant Access for the newly added service account at the bottom of the screen (you may need to click Refresh service accounts before it shows up)
- Choose the permissions you'd like this account to have. We recommend Admin (all permissions), but you may want to manually select all checkboxes and leave out some of the Releases permissions such as Release to production
- Click Invite user to finish
