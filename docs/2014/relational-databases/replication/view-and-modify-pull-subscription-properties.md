---
title: Просмотр и изменение свойств подписки по запросу | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- modifying subscriptions
- viewing replication properties
- modifying replication properties, pull subscriptions
- pull subscriptions [SQL Server replication], modifying
- subscriptions [SQL Server replication], pull
- pull subscriptions [SQL Server replication], properties
- modifying subscriptions, SQL Server Management Studio
ms.assetid: 1601e54f-86f0-49e8-b023-87a5d1def033
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab2dd19449e83468063e3e191c816cf1cfe4c755
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112954"
---
# <a name="view-and-modify-pull-subscription-properties"></a>Просмотр и изменение свойств подписки по запросу
  В данном разделе описывается просмотр и изменение свойств подписки по запросу в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Для просмотра и изменения свойств подписки по запросу используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотрите свойства подписки по запросу в издателе или подписчике в диалоговом окне **Свойства подписки —\<издатель>: \<база данных публикации>**, которое доступно из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. На подписчике можно просмотреть и изменить ряд дополнительных свойств. Свойства можно также просмотреть на издателе на вкладке **Все подписки** , доступной в мониторе репликации. Сведения о запуске монитора репликации см. в [этой статье](monitor/start-the-replication-monitor.md).  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-management-studio"></a>Просмотр свойств подписки по запросу на издателе в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Раскройте соответствующую публикацию, щелкните правой кнопкой мыши подписку и выберите **Свойства**.  
  
4.  Просмотрите свойства, а затем нажмите кнопку **ОК**.  
  
#### <a name="to-view-and-modify-pull-subscription-properties-from-the-subscriber-in-management-studio"></a>Просмотр и изменение свойств подписки по запросу на подписчике в среде Management Studio  
  
1.  Подключитесь к подписчику в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем — папку **Локальные подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и выберите **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### <a name="to-view-pull-subscription-properties-from-the-publisher-in-replication-monitor"></a>Просмотр свойств подписки по запросу на издателе в мониторе репликации  
  
1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
2.  Перейдите на вкладку **Все подписки** .  
  
3.  Щелкните правой кнопкой мыши подписку и выберите **Свойства**.  
  
4.  Просмотрите свойства, а затем нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Подписки по запросу можно изменять и получать доступ к их свойствам программно с помощью хранимых процедур репликации. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит подписка.  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Просмотр свойств подписки по запросу на публикацию моментальных снимков или публикацию транзакций  
  
1.  На подписчике выполните хранимую процедуру [sp_helppullsubscription](/sql/relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql). Задайте значения для параметров **@publisher**, **@publisher_db**и **@publication**. Тем самым возвращаются сведения о подписке, хранящиеся в системных таблицах на подписчике.  
  
2.  На подписчике выполните процедуру [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql). Задайте значения для параметров **@publisher**, **@publisher_db**, **@publication**, а также одно из следующих значений в параметре **@publication_type**:  
  
    -   **0** — подписка принадлежит публикации транзакций;  
  
    -   **1** — подписка принадлежит публикации моментальных снимков.  
  
3.  На издателе выполните хранимую процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql). Укажите параметр **@publication** и **@subscriber**.  
  
4.  На издателе выполните хранимую процедуру [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), указав параметр **@subscriber**. Будут выведены сведения о подписчике.  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Изменение свойств подписки по запросу на публикацию моментальных снимков или публикацию транзакций  
  
1.  На подписчике выполните хранимую процедуру [sp_change_subscription_properties](/sql/relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql), указав параметр **@publisher**, **@publisher_db**, **@publication**, значение **0** (публикация транзакций) или **1** (публикация моментальных снимков) в параметре **@publication_type**, изменяемое свойство подписки как **@property**и новое значение как **@value**.  
  
2.  На подписчике в базе данных подписки выполните хранимую процедуру [sp_changesubscriptiondtsinfo](/sql/relational-databases/system-stored-procedures/sp-changesubscriptiondtsinfo-transact-sql). Укажите идентификатор задания агента распространителя в параметре **@jobid**и следующие свойства пакетов служб DTS:  
  
    -   **@dts_package_name**  
  
    -   **@dts_package_password**  
  
    -   **@dts_package_location**  
  
     Свойства пакета служб подписки будут изменены.  
  
    > [!NOTE]  
    >  Идентификатор задания можно получить, выполнив процедуру [sp_helpsubscription](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql).  
  
#### <a name="to-view-the-properties-of-a-pull-subscription-to-a-merge-publication"></a>Просмотр свойств подписки по запросу на публикацию слиянием  
  
1.  На подписчике выполните хранимую процедуру [sp_helpmergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql). Задайте значения для параметров **@publisher**, **@publisher_db**и **@publication**.  
  
2.  На подписчике выполните процедуру [sp_helpsubscription_properties](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql). Задайте значения для параметров **@publisher**, **@publisher_db**, **@publication**и значение 2 в параметре **@publication_type**.  
  
3.  Чтобы вывести сведения о подписке, выполните на издателе хранимую процедуру [sp_helpmergesubscription](/sql/relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql) . Чтобы возвратить сведения о конкретной подписке, необходимо указать параметры **@publication**, **@subscriber**и значение **pull** в параметре **@subscription_type**.  
  
4.  На издателе выполните хранимую процедуру [sp_helpsubscriberinfo](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql), указав параметр **@subscriber**. Будут выведены сведения о подписчике.  
  
#### <a name="to-change-the-properties-of-a-pull-subscription-to-a-merge-publication"></a>Изменение свойств подписки по запросу на публикацию слиянием  
  
1.  На подписчике выполните хранимую процедуру [sp_changemergepullsubscription](/sql/relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql). Задайте значения для параметров **@publication**, **@publisher**, **@publisher_db**, изменяемое свойство подписки как **@property**и новое значение как **@value**.  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Конкретные классы объектов RMO, используемые для этого, зависят от типа публикации, для которой создается подписка по запросу.  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-snapshot-or-transactional-publication"></a>Просмотр или изменение свойств подписки по запросу на публикацию моментальных снимков или транзакций  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPullSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, либо на подписку на шаге 3 были неверно определены свойства, либо подписка не существует на сервере.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.TransPullSubscription> , которое можно установить, и затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно).  
  
7.  Чтобы просмотреть новые параметры, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> , который перезагрузит свойства статьи (необязательно).  
  
8.  Закройте все соединения.  
  
#### <a name="to-view-or-modify-properties-of-a-pull-subscription-to-a-merge-publication"></a>Просмотр или изменение свойств подписки по запросу на публикацию слиянием  
  
1.  Создайте соединение с подписчиком с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePullSubscription> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.DatabaseName%2A>, <xref:Microsoft.SqlServer.Replication.PullSubscription.PublisherName%2A>и <xref:Microsoft.SqlServer.Replication.PullSubscription.PublicationDBName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает `false`, либо на подписку на шаге 3 были неверно определены свойства, либо подписка не существует на сервере.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.MergePullSubscription> , которое можно установить, и затем вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно).  
  
7.  Чтобы просмотреть новые параметры, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.Refresh%2A> , который перезагрузит свойства статьи (необязательно).  
  
8.  Закройте все соединения.  
  
## <a name="see-also"></a>См. также  
 [Просмотр сведений и выполнение задач для подписки (монитор репликации)](monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Рекомендации по защите репликации](security/replication-security-best-practices.md)   
 [Подписка на публикации](subscribe-to-publications.md)  
  
  
