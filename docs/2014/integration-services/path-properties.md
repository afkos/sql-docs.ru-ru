---
title: Свойства пути | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- paths [Integration Services], properties
ms.assetid: 89b1e347-9579-4f6b-af74-c6519ea08eea
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a1b69e60cc4adc85d6af9a909f3278a179ea06df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171004"
---
# <a name="path-properties"></a>Свойства пути
  Объекты потока данных в объектной модели служб [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] обладают общими свойствами и пользовательскими свойствами на уровне компонента, входами и выходами, а также входными и выходными столбцами. Многие свойства имеют значения, доступные только для чтения и присваиваемые подсистемой обработки потока данных на этапе выполнения.  
  
 Этот раздел содержит список и описание пользовательских свойств путей, соединяющих объекты потоков данных.  
  
## <a name="path-properties"></a>Свойства пути  
 В модели объектов служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] путь, соединяющий компоненты потока данных, реализует интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>.  
  
 В следующей таблице показаны настраиваемые свойства путей в потоке данных. Подсистема обработки потока данных также назначает значения дополнительным, доступным только для чтения, свойствам, которые здесь не перечислены.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|PathAnnotation|Integer (перечисление)|Значение показывает, следует ли отображать описание рядом с путем в области конструктора. Возможные значения: `AsNeeded`, `SourceName`, `PathName`, и `Never`. Значение по умолчанию — `AsNeeded`.|  
|DestinationName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>|Вход, связанный с путем.|  
|SourceName|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>|Выход, связанный с путем.|  
  
## <a name="see-also"></a>См. также  
 [Пути служб Integration Services](data-flow/integration-services-paths.md)   
 [Общие свойства](../../2014/integration-services/common-properties.md)   
 [Пользовательские свойства преобразования](data-flow/transformations/transformation-custom-properties.md)   
 [Свойства потока данных, которые можно задавать с помощью выражений](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
