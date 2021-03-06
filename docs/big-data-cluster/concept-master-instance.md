---
title: Что такое большие данные кластеров SQL Server главного экземпляра? | Документы Майкрософт
description: В этой статье описывается основной экземпляр в кластере SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 50955f8c781dcf370aa3f48ed72a0ed993854655
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221600"
---
# <a name="what-is-the-sql-server-big-data-cluster-master-instance"></a>Что такое большие данные SQL Server кластера главного экземпляра?

В этой статье описывается роль *главного экземпляра SQL Server* в кластере SQL Server 2019 больших ata. Основной экземпляр является экземпляром SQL Server работает в кластере SQL Server больших данных [плоскость управления](big-data-cluster-overview.md#controlplane).

Основной экземпляр SQL Server предоставляет следующие функциональные возможности:

## <a name="connectivity"></a>Соединение

Основной экземпляр SQL Server предоставляет конечную точку TDS доступном для кластера. Вы можете подключиться, приложения и средства SQL Server, например Studio данных Azure или SQL Server Management Studio к этой конечной точке, так же, как бы любой другой экземпляр SQL Server.

## <a name="scale-out-query-management"></a>Горизонтальное масштабирование запросов управления

Основной экземпляр SQL Server содержит ядро запросов горизонтального масштабирования, который используется для распределения запросов между экземплярами SQL Server на узлах в [вычислений пула](concept-compute-pool.md). Обработчик запросов горизонтальное масштабирование также предоставляет доступ через Transact-SQL для всех таблиц Hive в кластере без дополнительной настройки. (Поддержка таблиц hive не CTP 2.1)

## <a name="metadata-and-user-databases"></a>Метаданные и пользовательских баз данных

В дополнение к стандартной системы баз данных SQL Server основной экземпляр SQL также содержит следующие элементы:

- Метаданные базы данных, который содержит метаданные таблицы HDFS
- Карта сегментов плоскости данных
- Сведения о внешних таблиц, которые обеспечивают доступ к плоскости данных кластера.
- PolyBase внешние источники данных и внешние таблицы, определенные в пользовательской базе данных.

Можно также добавить собственные пользовательские базы данных master экземпляра SQL Server.

## <a name="machine-learning-services"></a>Службы машинного обучения

Службы машинного обучения SQL Server является функцией расширения к компоненту database engine, используемый для выполнения кода Java, R и Python в SQL Server. Эта функция основана на структуре расширяемости SQL Server, который изолирует внешних процессов из основных процессов, но полностью интегрируется с реляционными данными как хранимые процедуры, скрипт T-SQL, содержащий инструкции R или Python или Java, R или Код Python, содержащий T-SQL.

Как часть кластера больших данных SQL Server службы машинного обучения будут доступны в экземпляре SQL Serevr master по умолчанию. Это означает, что после выполнения внешнего скрипта будет включен в основной экземпляр SQL Server, она будет возможна, для выполнения Java, Python и R сценариев, с помощью процедуры sp_execute_external_script.

### <a name="advantages-of-machine-learning-services-in-a-big-data-cluster"></a>Преимущества служб машинного обучения в кластере больших данных

SQL Server 2019 упрощает для больших объемов данных будет присоединен к многомерных данных, обычно хранятся в корпоративной базе данных. Значение больших данных значительно увеличивается, когда он не просто в руки частей организации, но также включается в отчеты, панели мониторинга и приложений. В то же время, обработке и анализу данных могут продолжать использовать такие средства экосистемы Spark или HDFS и легким, имеют реальном времени доступа к данным в основной экземпляр SQL Server, так и во внешних источниках данных доступны _через_ master SQL Server экземпляр.

С SQL Server 2019 кластерами больших данных, новые возможности работы с Озера данных вашего предприятия. Разработчики SQL Server и аналитиков могут:

* Создавайте приложения, использующие данные из Озера данных предприятия.
* Обосновать все данные с запросами Transact-SQL.
* Используйте существующие экосистемы средств SQL Server и приложений, получать доступ и анализировать корпоративные данные.
* Сократить число необходимых для перемещения данных с помощью виртуализации данных и киоски данных.
* Продолжайте использовать Spark при обработке больших данных.
* Создание интеллектуальных корпоративных приложений с помощью Spark или SQL Server для обучения моделей по Озера данных.
* Ввод в эксплуатацию моделей в рабочих базах данных для достижения оптимальной производительности.
* Stream данные непосредственно в киоски данных предприятия для аналитики в реальном времени.
* Просмотр данных, визуально с помощью интерактивного анализа и средств бизнес-Аналитики.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных SQL Server, см. в разделе приведены общие:

- [Что такое кластеры SQL Server 2019 больших данных?](big-data-cluster-overview.md)
