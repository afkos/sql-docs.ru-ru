---
title: Обновить все целевые серверы перед обновлением главного сервера | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- TSX [SQL Server Agent]
- target servers [SQL Server Agent]
- MSX [SQL Server Agent]
- master servers [SQL Server Agent]
ms.assetid: 2c231793-3878-4a5e-a425-1fa0d787ba84
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97272209c1ceba780711ecf4a07178ddf8943d49
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061957"
---
# <a name="upgrade-all-target-servers-before-upgrading-the-master-server"></a>Обновите все целевые серверы перед обновлением главного сервера
  Перед обновлением главного сервера обновите все компьютеры, на которых работают серверы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , настроенные в качестве целевых серверов.  
  
## <a name="component"></a>Компонент  
 Агент[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]   
  
## <a name="description"></a>Описание  
 Чтобы автоматизировать администрирование многосерверной среды, необходимо иметь по меньшей мере один главный сервер и один целевой. Главный сервер распределяет задания целевым серверам и получает от них события. На главном сервере также хранится центральная копия определений заданий, выполняющихся на целевых серверах.  
  
 Если текущий сервер настроен как главный, необходимо сначала обновить все целевые серверы, а затем главный сервер.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если нельзя обновить все целевые серверы до обновления главного сервера, то следует исключить все целевые серверы и после обновления прикрепить их повторно.  
  
 Дополнительные сведения об определении выполняемых задач см. в разделах «Автоматизация администрирования в масштабах предприятия», «Как отключить целевой сервер от главного сервера» и «Как прикрепить целевой сервер к главному серверу» в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Проблемы при обновлении агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)   
 [Проблемы обновления агента SQL Server](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
