# Getting Started with CME CloudPurchase

Установка CME CloudPurchase довольно проса и состоит из следующих шагов.

## <a id="install"></a> Install the Unity plugin

Актуальная версия CME CloudPurchase находится в [Unity Asset Store](ссылка на платну версию), при желании можно воспользоваться [пробной версией](ссылка на бесплатную версию).

Хороший мануал по установки unity плагинов есть на [сайте](https://docs.unity3d.com/Manual/AssetPackagesPurchase.html) официальной документации Unity.

## <a id="aws-credentials"></a> Get your AWS security credentials

Если у вас еще нету аккаунта в AWS, то рекомендуем выполнить шаги [официального руководства](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/).

В случае, если аккаунт уже есть то можно переходить к получению ключей доступа.

### Generating security credentials

Для получения ключей доступа перейите в раздел [Identity and Access Management](https://console.aws.amazon.com/iamv2/home) и выполните следующие действия:

![](../assets/AWS%20first%20run3.gif)

## <a id="deployment"></a> Make your first deployment

Теперь вы готовы развернуть свое первое CME CloudPurchase приложения, для этого откройте Unity Editor преокт с установленным плагинов и выполните следующие действия:

![](../assets/unity%20first%20run3.gif)

## <a id="stores"></a> Configure stores integrations

Без конфигурации ключей доступа к Google Developer Console нет возможности проверять патежи в Google Play Store, поэтому проверка может выдавать ошибку:

![](скриншит)

Для получения этих ключей необходимо перейти в [Google Play Console](https://play.google.com/console/) и выполните следующие действия:


[//]: # (Collect your Google credentials)

[//]: # (Tip: If you see Google Play Console or Google Developer Console in your local language, add &hl=en at the end of the URL &#40;before any #...&#41; to switch to English.)

Open the Google Play Console
![](../assets/google_1.gif)
- Click Account Details, and note the Developer Account ID listed there
- Click Setup → API access
- Click the Create new service account button
- Follow the Google Cloud Platform link in the dialog, which opens a new tab/window:
- Click the CREATE SERVICE ACCOUNT button at the top of the Google Cloud Platform Console
- Verify that you are on the correct Google Cloud Platform Project by looking for the Developer Account ID from earlier within the light gray text in the second input, preceding .iam.gserviceaccount.com. If not, open the picker in the top navigation bar, and find the one with the ID that contains it.
- Provide a Service account name and click Create
- Click Select a role, then find and select Service Account User, and proceed
- Click the Done button

![](../assets/google_2.gif)
- Click on the Actions vertical three-dot icon of the service account you just created
- Select Manage keys on the menu
- Click ADD KEY -> Create New Key
- Make sure JSON is selected as the Key type, and click CREATE
- Save the file on your computer when prompted and remember where it was saved to

![](../assets/google_3.gif)
- Return to the Google Play Console tab, and click DONE to close the dialog
- Click on Grant Access for the newly added service account at the bottom of the screen (you may need to click Refresh service accounts before it shows up)
- Choose the permissions you'd like this account to have. We recommend Admin (all permissions), but you may want to manually select all checkboxes and leave out some of the Releases permissions such as Release to production
- Click Invite user to finish
