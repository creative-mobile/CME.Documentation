# Getting Started with CME CloudPurchase

Installing **CME CloudPurchase** is pretty straightforward and consists of the following steps:

1. Install the plug-in from the [Unity Asset Store](https://assetstore.unity.com/preview/224332/710152).
2. Get the [AWS Credentials](#aws-credentials).
3. Make the [first deployment](#deployment).
4. Configure [access keys](#stores) to the Google Developer Console.

## <a id="aws-credentials"></a> Get your AWS security credentials

If you do not yet have an **AWS** account, we recommend following the instructions in the [official manual](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/){target=_blank}.

If you already have an account, you can move on to getting the access keys.

### Generating security credentials

For access keys, go to [Identity and Access Management | Your Security Credentials](hhttps://us-east-1.console.aws.amazon.com/iam/home#/security_credentials){target=_blank} and get an access key by following the steps below:

![!](../assets/get_aws_creds.gif)

## <a id="deployment"></a> Make your first deployment

<div class="admonition warning">
<p class="admonition-title">Warning</p>
Payments in the <b>Google Play Store</b> cannot be verified without the configuration of <b>Google Developer Console</b> <a href="#stores">access keys</a>. Therefore, the verification may display an error:</p>
<img src="../assets/google-creds-error.jpg">
</div>

You are now ready to deploy your first **CME CloudPurchase** application. To do this, open the **Unity Editor** with the plug-in installed and click the **Deploy** button:

![](../assets/first deploy.gif)

Вероятнее всего, вам прийдется установить сгенерированные ключи доступа AWS в открывшийся файл `.aws/credentials` в вашей домашней директории. Подробнее про него можно прочитать в [официальной документации](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html).

## <a id="stores"></a> Configure stores integrations

Для получения ключей доступа к **Google Developer Console** необходимо перейти в [Google Play Console](https://play.google.com/console/){target=_blank} и выполните следующие действия:

1. Создайте сервисный аккаунт.
![!](../assets/google_1.gif)

2. Создайте новый приватный ключ.
![!](../assets/google_2.gif)

3. Выдайте необходимые разрешения для аккаунта.
![!](../assets/google_3.gif)

Подробнее о процессе создания и настройки сервисного аккаунта можно узнать [в официальной документации](https://developers.google.com/workspace/guides/create-credentials#service-account){target=_blank}.
