---
title: Невозможно обновить базы данных только для чтения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3757183f61a3f70097d5abb7a0d01d6381a1d10e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134094"
---
# <a name="read-only-databases-cannot-be-upgraded"></a>Доступные только для чтения базы данных не могут быть обновлены
  Помощник по обновлению определил, что некоторые базы данных в этом экземпляре служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не могут быть обновлены.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Обнаружена база данных, доступная только для чтения. Чтобы обновить базу данных, программа установки должна иметь возможность записи в базу данных.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если никто не использует базу данных, использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], или инструкции ALTER DATABASE, чтобы изменить базу данных для чтения и записи. Следующая инструкция переводит базу данных в режим чтения и записи.  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 Дополнительные сведения об инструкции ALTER DATABASE см. в разделе «ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
