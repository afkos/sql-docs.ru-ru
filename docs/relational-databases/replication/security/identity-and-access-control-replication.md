---
title: Идентификатор и контроль доступа (репликация) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- access controls [SQL Server replication]
- security [SQL Server replication], identity and access control
- authentication [SQL Server replication]
- identity [Replication]
ms.assetid: 4da0e793-1ee4-4f69-a80b-45c6732a238d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 50e746f05ba3d38a99aa8ccd1c783aec9be87f40
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836544"
---
# <a name="identity-and-access-control-replication"></a>Идентификатор и управление доступом (репликация)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Проверка подлинности представляет собой процесс проверки сущностью (в данном контексте, как правило, компьютером) другой сущности, также называемой *участником*(как правило, это другой компьютер или пользователь). Авторизация — это процесс, с помощью которого авторизованный участник получает доступ к ресурсам, например к файлу в файловой системе или таблице в базе данных.  
  
 Система безопасности репликации использует проверку подлинности и авторизацию для контроля доступа к реплицируемым объектам базы данных, к компьютерам и агентам, участвующим в процессе репликации. Эти действия выполняются с помощью трех механизмов.  
  
-   Безопасность агентов  
  
     Модель безопасности агентов репликации обеспечивает точный контроль учетных записей, под которыми запускаются и подключаются агенты репликации. Подробные сведения о модели безопасности агентов см. в разделе [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md). Сведения о настройке имен для входа и паролей агентов см. в статье [Управление именами для входа и паролями при репликации](../../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md).  
  
-   Роли администрирования  
  
     Убедитесь, что для настройки, обслуживания и обработки репликации используются правильные роли серверов и баз данных. Дополнительные сведения см. в статье [Security Role Requirements for Replication](../../../relational-databases/replication/security/security-role-requirements-for-replication.md).  
  
-   Список доступа к публикации (PAL)  
  
     Предоставьте доступ к публикациям с помощью списка доступа к публикации. Он работает так же, как и список управления доступом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Когда подписчик подключается к издателю или распространителю и запрашивает доступ к публикации, данные для проверки подлинности, переданные агентом, проверяются согласно списку доступа к публикации. Дополнительные сведения и рекомендации по использованию списков доступа к публикации см. в [этой статье](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="filtering-published-data"></a>Фильтрование опубликованных данных  
 В дополнение к использованию проверки подлинности и авторизации для контроля доступа к реплицируемым данным и объектам репликация имеет два параметра для управления доступными данными на подписчике: фильтрация по столбцам и строкам. Дополнительные сведения о фильтрации см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
 При определении статьи можно опубликовать только те столбцы, которые необходимы для публикации, и пропустить несущественные столбцы или столбцы, которые содержат конфиденциальные данные. Например, при публикации таблицы **Заказчик** из базы данных Adventure Works для продавцов на выезде можно пропустить столбец **AnnualSales** , который может быть важен лишь для администрации компании.  
  
 Фильтрация опубликованных данных позволяет ограничить доступ к данным и указать данные, доступные на подписчике. Например, можно отфильтровать таблицу **Заказчик** так, чтобы партнеры компании получали сведения только о тех заказчиках, для которых в столбце **ShareInfo** имеется значение «да». При репликации слиянием может возникать проблема безопасности, если используется параметризованный фильтр, содержащий HOST_NAME(). Дополнительные сведения см. в подразделе «Фильтрация с использованием HOST_NAME()» раздела [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
## <a name="see-also"></a>См. также:  
 [Безопасность и защита (репликация)](../../../relational-databases/replication/security/security-and-protection-replication.md)   
 [Общие сведения о безопасности (репликация)](../../../relational-databases/replication/security/security-overview-replication.md)   
 [Предотвращение угроз и устранение уязвимостей (репликация)](../../../relational-databases/replication/security/threat-and-vulnerability-mitigation-replication.md)  
  
  
