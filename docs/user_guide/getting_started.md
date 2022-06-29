# Getting Started with CME CloudPurchase

Установка **CME CloudPurchase** довольно проста и состоит из следующих шагов:

1. Установить плагин из [Unity Asset Store](https://assetstore.unity.com/preview/224332/710152).
2. Получить [AWS Credentials](#aws-credentials).
3. Выполнить [первый деплой](#deployment).
4. Сконфигурировать [ключи доступа](#stores) к Google Developer Console.

## <a id="aws-credentials"></a> Get your AWS security credentials

Если у вас еще нету аккаунта в **AWS**, то рекомендуем выполнить шаги [официального руководства](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/){target=_blank}.

В случае, если аккаунт уже есть то можно переходить к получению ключей доступа.

### Generating security credentials

Для получения ключей доступа перейите в раздел [Identity and Access Management | Your Security Credentials](hhttps://us-east-1.console.aws.amazon.com/iam/home#/security_credentials){target=_blank} и получите ключ доступа, выполнив следующие действия:

![!](../assets/get_aws_creds.gif)

## <a id="deployment"></a> Make your first deployment

<div class="admonition warning">
<p class="admonition-title">Warning</p>
<p>Без конфигурации <a href="#stores">ключей доступа</a> к <b>Google Developer Console</b> нет возможности проверять патежи в <b>Google Play Store</b>, поэтому проверка может выдавать ошибку:</p>
<img src="../assets/google-creds-error.jpg">
</div>

Теперь вы готовы развернуть свое первое **CME CloudPurchase** приложение, для этого откройте **Unity Editor** с установленным плагинов и нажмите на кнопку **Deploy**:

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
