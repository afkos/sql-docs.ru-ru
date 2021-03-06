---
title: Класс событий Bitmap Warning | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Bitmap Warning event class
ms.assetid: 5bf9b4e3-0eba-4e67-8ba9-30ca4b48e1d4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3fbd8408df9425f2e42d0819d1efa1c4bdcc4dd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124144"
---
# <a name="bitmap-warning-event-class"></a>Bitmap Warning, класс событий
  Класс событий **Bitmap Warning** можно использовать для мониторинга фильтрации по битовым картам в запросах. Подкласс этого события применяется для сообщения об отключенных фильтрах по битовым картам в запросе.  
  
## <a name="bitmap-warning-event-class-data-columns"></a>Столбцы данных класса событий Bitmap Warning  
  
|Имя столбца данных|Тип данных|Описание|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|`nvarchar`|Имя клиентского приложения, установившего соединение с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот столбец заполняется значениями, передаваемыми приложением, а не отображаемым именем программы.|10|Да|  
|**ClientProcessID**|`int`|Идентификатор, присвоенный главным компьютером сервера процессу, в котором работает клиентское приложение. Этот столбец данных заполняется в том случае, если клиент предоставляет идентификатор клиентского процесса.|9|Да|  
|**DatabaseID**|`int`|Идентификатор базы данных, указанной в инструкции USE *database* , или базы данных по умолчанию, если для данного экземпляра инструкция USE *database* не выполнялась. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] отображает имя базы данных, если столбец данных **ServerName** захвачен при трассировке и сервер доступен. Определите значение для базы данных, используя функцию DB_ID.|3|Да|  
|**DatabaseName**|`nvarchar`|Имя базы данных, в которой выполняется пользовательская инструкция.|35|Да|  
|**EventClass**|`int`|Тип события = 212.|27|Нет|  
|**EventSequence**|`int`|Последовательность данного события в запросе.|51|Нет|  
|**EventSubClass**|`int`|Тип подкласса события. 0 = фильтр по битовым картам отключен.|21|Да|  
|**HostName**|`nvarchar`|Имя компьютера, на котором выполняется клиентская программа. Заполнение этого столбца данных производится в том случае, если клиент предоставляет имя узла. Чтобы определить имя узла, используйте функцию HOST_NAME.|8|Да|  
|**IsSystem**|`int`|Указывает, произошло событие в системном или в пользовательском процессе. 1 = системный, 0 = пользовательский.|60|Да|  
|**LoginName**|`nvarchar`|Имя входа пользователя (либо защищенное имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , либо учетные данные входа Windows в формате *ДОМЕН\имя_пользователя*).|11|Да|  
|**LoginSid**|`image`|Идентификатор безопасности вошедшего в систему пользователя. Эти сведения можно найти в представлении каталога **sys.server_principals** . Значение идентификатора безопасности уникально для каждого имени входа на сервере.|41|Да|  
|**NTDomainName**|`nvarchar`|Домен Windows, к которому принадлежит пользователь.|7|Да|  
|**NTUserName**|`nvarchar`|Имя пользователя Windows.|6|Да|  
|**ObjectID**|`int`|Идентификатор узла для корня группы хэширования, участвующей в перераспределении секций. Соответствует идентификатору узла в Showplan.|22|Да|  
|**RequestID**|`int`|Идентификатор запроса, содержащего инструкцию.|49|Да|  
|**ServerName**|`nvarchar`|Имя экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого производится трассировка.|26|Нет|  
|**SessionLoginName**|`nvarchar`|Имя входа пользователя, создавшего сеанс. Например, при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по имени "Имя_входа1" и при выполнении инструкции под именем "Имя_входа2" **SessionLoginName** содержит значение "Имя_входа1", а **LoginName** — значение "Имя_входа2". В этом столбце отображаются как имена входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , так и имена входа Windows.|64|Да|  
|**SPID**|`int`|Идентификатор сеанса, в котором произошло событие.|12|Да|  
|**StartTime**|`datetime`|Время начала события, если оно известно.|14|Да|  
|**TransactionID**|`bigint`|Назначенный системой идентификатор транзакции.|4|Да|  
|**XactSequence**|`bigint`|Токен, который описывает текущую транзакцию.|50|Да|  
  
  
