---
title: Как выполнить запрос Oracle из больших данных кластера SQL Server | Документация Майкрософт
description: Этом руководстве показано, как запрашивать данные Oracle из кластера SQL Server 2019 больших данных (Предварительная версия). Создайте внешнюю таблицу данных в Oracle и выполняют запрос.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/12/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: 7f5383a6faf13f0454439a42efb7524eaeda7c76
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644250"
---
# <a name="tutorial-query-oracle-from-a-sql-server-big-data-cluster"></a>Руководство: Выполнение запросов Oracle из больших данных кластера SQL Server

Этом руководстве показано, как запрашивать данные Oracle из кластера SQL Server 2019 больших данных. Для использования этого учебника, необходимо иметь доступ к серверу Oracle. Если у вас нет доступа, этот учебник поможет вам понять, как работает виртуализация данных для внешних источников данных в кластере SQL Server больших данных.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
> * Создайте внешнюю таблицу для данных во внешней базе данных Oracle.
> * Объединение этих данных с помощью данных высокой ценности, в основной экземпляр.

> [!TIP]
> При желании можно загрузить и запустить сценарий для команды в этом руководстве. Инструкции см. в разделе [образцы данных виртуализации](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) на сайте GitHub.

## <a id="prereqs"></a> Предварительные требования

* [Развертывание кластера больших данных в Kubernetes](deployment-guidance.md).
* [Установка Studio данных Azure и расширение SQL Server 2019](deploy-big-data-tools.md).
* [Загрузка образца данных в кластере](#sampledata).

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-oracle-table"></a>Создайте таблицу Oracle

Далее создайте образец таблицы с именем `INVENTORY` в Oracle.

1. Подключение к Oracle экземпляра и базы данных, которая будет использоваться в этом руководстве.

1. Выполните следующую инструкцию для создания `INVENTORY` таблицы:

   ```sql
    CREATE TABLE "INVENTORY"
    (
        "INV_DATE" NUMBER(10,0) NOT NULL,
        "INV_ITEM" NUMBER(10,0) NOT NULL,
        "INV_WAREHOUSE" NUMBER(10,0) NOT NULL,
        "INV_QUANTITY_ON_HAND" NUMBER(10,0)
    );

    CREATE INDEX INV_ITEM ON HR.INVENTORY(INV_ITEM);
    ```

1. Импортируйте содержимое файла **inventory.csv** файл в эту таблицу. Этот файл был создан с помощью сценариев создания образца в [предварительные требования](#prereqs) раздел.

## <a name="create-an-external-data-source"></a>Создание внешнего источника данных

Первым шагом является создание внешнего источника данных с доступом к серверу Oracle.

1. В Azure Data Studio подключитесь к основной экземпляр SQL Server кластера больших данных. Дополнительные сведения см. в разделе [подключение к экземпляру SQL Server master](deploy-big-data-tools.md#master).

1. Дважды щелкните подключение в **серверы** окно для отображения панели мониторинга сервера для главного экземпляра SQL Server. Выберите **новый запрос**.

   ![Запрос главного экземпляра SQL Server](./media/tutorial-query-oracle/sql-server-master-instance-query.png)

1. Выполните следующую команду Transact-SQL, чтобы изменить контекст, чтобы **Sales** базы данных master экземпляра.

   ```sql
   USE Sales
   GO
   ```

1. Создайте учетные данные уровня базы данных для подключения к серверу Oracle. Укажите соответствующие учетные данные к серверу Oracle, в следующей инструкции.

   ```sql
   CREATE DATABASE SCOPED CREDENTIAL [OracleCredential]
   WITH IDENTITY = '<oracle_user,nvarchar(100),SYSTEM>', SECRET = '<oracle_user_password,nvarchar(100),manager>';
   ```

1. Создание внешнего источника данных, указывающий на сервере Oracle.

   ```sql
   CREATE EXTERNAL DATA SOURCE [OracleSalesSrvr]
   WITH (LOCATION = 'oracle://<oracle_server,nvarchar(100)>',CREDENTIAL = [OracleCredential]);
   ```

## <a name="create-an-external-table"></a>Создайте внешнюю таблицу, выполните следующие действия.

Затем создайте внешнюю таблицу с именем **iventory_ora** через `INVENTORY` таблицы на сервере Oracle.

```sql
CREATE EXTERNAL TABLE [inventory_ora]
    ([inv_date] DECIMAL(10,0) NOT NULL, [inv_item] DECIMAL(10,0) NOT NULL,
    [inv_warehouse] DECIMAL(10,0) NOT NULL, [inv_quantity_on_hand] DECIMAL(10,0))
WITH (DATA_SOURCE=[OracleSalesSrvr],
        LOCATION='<oracle_service_name,nvarchar(30),xe>.<oracle_schema,nvarchar(128),HR>.<oracle_table,nvarchar(128),INVENTORY>');
```

> [!NOTE]
> Имена таблиц и имена столбцов, будут использовать ANSI SQL, заключенный в кавычки идентификатор при выполнении запроса к Oracle. Таким образом именах учитывается регистр. Важно указать имя в определении внешней таблицы, который соответствует точный регистр имен таблицы и столбца в метаданных Oracle.

## <a name="query-the-data"></a>Запрос данных

Выполните следующий запрос, чтобы объединить данные `iventory_ora` внешнюю таблицу с таблицами в локальной `Sales` базы данных.

```sql
SELECT TOP(100) w.w_warehouse_name, i.inv_item, SUM(i.inv_quantity_on_hand) as total_quantity
  FROM [inventory_ora] as i
  JOIN item as it
    ON it.i_item_sk = i.inv_item
  JOIN warehouse as w
    ON w.w_warehouse_sk = i.inv_warehouse
 WHERE it.i_category = 'Books' and i.inv_item BETWEEN 1 and 18000 --> get items within specific range
 GROUP BY w.w_warehouse_name, i.inv_item;
```

## <a name="clean-up"></a>Очистить

Используйте следующую команду для удаления объектов базы данных, созданной в этом учебнике.

```sql
DROP EXTERNAL TABLE [inventory_ora];
DROP EXTERNAL DATA SOURCE [OracleSalesSrvr] ;
DROP DATABASE SCOPED CREDENTIAL [OracleCredential];
```

## <a name="next-steps"></a>Следующие шаги

Узнайте, как прием данных в пуле данных:
> [!div class="nextstepaction"]
> [Загрузка данных в пул данных](tutorial-data-pool-ingest-sql.md)
