GetCounteragentCertificates
===========================

Имя ресурса: **/GetCounteragentCertificates**

HTTP метод: **GET**

Параметры строки запроса:

-  *myOrgId*: идентификатор организации, от лица которой будет произведен поиск сертификатов контрагента;

-  *counteragentOrgId*: идентификатор организации, для которой осуществляется поиск сертификаторв контрагента;

В запросе должен присутствовать HTTP-заголовок ``Authorization`` с необходимыми данными для :doc:`авторизации <../Authorization>`. Организация имеет право запрашивать список сертификатов контрагента *counteragentOrgId*, если у нее подключена возможность отправки зашифрованных документов.

Параметр *myOrgId* нужен для того, чтобы указать организацию, от которой будет происходить запрос на список сертификатов. Также *myOrgId* нужен для проверки разрешения на запрос списка сертификатов.

В теле ответа содержится информация о сертификатах контрагента *counteragentOrgId*. Эта информация выдается в виде сериализованной структуры данных :doc:`CounteragentCertificateList <../proto/Counteragent>`.

Возможные HTTP-коды возврата:

-  200 (OK) - операция успешно завершена;

-  400 (Bad Request) - данные в запросе имеют неверный формат или отсутствуют обязательные параметры;

-  401 (Unauthorized) - в запросе отсутствует HTTP-заголовок ``Authorization``, или в этом заголовке содержатся некорректные авторизационные данные;

-  403 (Forbidden) - доступ к списку сертификатов организации *counteragentOrgId* от организации *myOrgId* с предоставленным авторизационным токеном запрещен;

-  404 (Not Found) - между организациями myOrgId и counteragentOrgId партнерские отношения никогда не устанавливались;

-  405 (Method not allowed) - используется неподходящий HTTP-метод;

-  500 (Internal server error) - при обработке запроса возникла непредвиденная ошибка.