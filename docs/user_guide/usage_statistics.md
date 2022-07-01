# Usage Statistics & Monitoring

Basic payment monitoring is available through AWS CloudWatch, and you can use CSV uploaded history to perform full-featured analysis with the tools of your choice.

![!](../assets/dashboard-preview.jpg)

## <a id="dashboard"></a> Dashboard overview

To access the dashboard, press the 'Open Environment Dashboard' button. By default, the dashboard contains the following sections:

 * `Purchases Overview`. Shows the amount of payments by day.
 * `Usage Overview`. The graph shows the number of successful payments and those with an error.
 * `Purchase Details`. Here you can read more about each specific payment.
 * `Purchase Errors`. Детализация по ошибкам платежей.

 В правом верхнем углу находится элементы управления дашбордом. Здесь можно:

 * Изменить рассматриваемый период времени.
 * Изменить интервал обновления данных.
 * Добавить виджеты к дашборду, изменить имя дашборда, удалить дашборд и т.д.

Подробнее о работе с дашбордами в CloudWatch можно узнать в [официальной документации](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html).

## <a id="sensetive-data"></a> Sensetive data 

<div class="admonition warning">
<p class="admonition-title">Warning</p>
<p>В журнал платежей попадают персональные данные пользователя, а именно поле <a href="/api_reference/CME.CloudPurchase/#F-CME-CloudPurchase-ValidationRequest-UserId">UserId</a>. По-умолчанию, время хранения персональных данных составляет две недели.</p>
</div>

## <a id="data-export"></a> Exporting to the `.csv`

В CloudWatch существует возможность экспортировать данные из виджета в `.csv` файл. Для того, чтобы это сделать нужно:

1. Выбрать интересующий вас виджет. Нажать кнопку `View in CloudWatch Logs Insights`.
2. Нажать кнопку `Run query`.
3. Дождаться окончания загрузки.
4. В меню `Export results` выбрать пункт `Download table (CSV)`.

![!](../assets/export-csv.gif)
