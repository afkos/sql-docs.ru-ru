---
title: SQL Server, объект клерков брокера памяти | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
author: dagiro
ms.author: v-dagir
manager: craigg
ms.openlocfilehash: 32c12c07b5f5a410220557561e0f7eddc12f6c0e
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030404"
---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, объект клерков брокера памяти
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Объект производительности **SQLServer:Memory Broker Clerks** предоставляет счетчики для сбора статистики по клеркам брокера памяти.

В следующей таблице представлены объекты производительности **Memory Broker Clerks** SQL Server.

|**SQL Server, счетчики клерков брокера памяти**|Описание|  
|-------------|-----------------|  
|**Внутреннее преимущество**|Внутреннее значение нехватки памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер клерка брокера памяти**|Размер клерка памяти в страницах.|
|**Периодические вытеснения (страниц)**|Число страниц, удаленных из клерка брокера при последнем периодическом удалении.|
|**Вытеснения с давлением (стр/с)**|Число страниц в секунду, удаляемых из клерка брокера из-за нехватки памяти.|
|**Преимущества эмуляции**|Значение клерка памяти в миллисекундах на страницу, умноженное на 10 миллиардов и округленное до целого числа.|
|**Размер эмуляции**|Текущий размер эмуляции клерка в страницах.|

Существует экземпляр счетчика для буферного пула и для пула объектов хранилища столбцов.

## <a name="see-also"></a>См. также:  
[Наблюдение за использованием ресурсов (системный монитор)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
