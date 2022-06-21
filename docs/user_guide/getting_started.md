# Getting Started with CME CloudPurchase

Установка CME CloudPurchase довольно проса и состоит из следующих шагов.

## <a id="install"></a> Install the Unity plugin

Актуальная версия CME CloudPurchase находится в [Unity Asset Store](ссылка на платну версию), при желании можно воспользоваться [пробной версией](ссылка на бесплатную версию).

Хороший мануал по установки unity плагинов есть на [сайте](https://docs.unity3d.com/Manual/AssetPackagesPurchase.html){target=_blank} официальной документации Unity.

## <a id="aws-credentials"></a> Get your AWS security credentials

Если у вас еще нету аккаунта в AWS, то рекомендуем выполнить шаги [официального руководства](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/){target=_blank}.

В случае, если аккаунт уже есть то можно переходить к получению ключей доступа.

### Generating security credentials

Для получения ключей доступа перейите в раздел [Identity and Access Management](https://console.aws.amazon.com/iamv2/home){target=_blank} и выполните следующие действия:

![!](../assets/AWS%20first%20run3.gif)

## <a id="deployment"></a> Make your first deployment

Теперь вы готовы развернуть свое первое CME CloudPurchase приложения, для этого откройте Unity Editor преокт с установленным плагинов и выполните следующие действия:

![!](../assets/unity%20first%20run3.gif)

## <a id="stores"></a> Configure stores integrations

Без конфигурации ключей доступа к Google Developer Console нет возможности проверять патежи в Google Play Store, поэтому проверка может выдавать ошибку:

![!](../assets/google-creds-error.jpg)

Для получения этих ключей необходимо перейти в [Google Play Console](https://play.google.com/console/){target=_blank} и выполните следующие действия:

1. Создайте сервисный аккаунт.
![!](../assets/google_1.gif)

2. Создайте новый приватный ключ.
![!](../assets/google_2.gif)

3. Выдайте необходимые разрешения для аккаунта.
![!](../assets/google_3.gif)

Подробнее о процессе создания и настройки сервисного аккаунта можно узнать [здесь](https://developers.google.com/workspace/guides/create-credentials#service-account){target=_blank}