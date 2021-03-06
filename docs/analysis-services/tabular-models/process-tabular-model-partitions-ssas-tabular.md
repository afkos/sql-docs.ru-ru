---
title: Обработка секций табличной модели | Документы Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ceaf64d4d1ef04f410be306c622ca78b3671d526
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="process-tabular-model-partitions"></a>Обработка секций табличной модели 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Секции разделяют таблицу на логические части. Каждая секция затем может обрабатываться (обновляться) независимо от других секций. Приведенные в этом разделе задачи описывают обработку секций в базе данных model с помощью диалогового окна **Обработка секций** в [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
###  <a name="bkmk_create_new"></a> Обработка секции  
  
1.  В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]щелкните правой кнопкой мыши таблицу, в которой есть секции для обработки, и выберите пункт **Секции**.  
  
2.  В диалоговом окне **Секции** на вкладке **Секции**нажмите кнопку «Обработка».  
  
3.  В диалоговом окне **Обработка секций** выберите один из следующих режимов из списка **Режим** :  
  
    |Режим|Description|  
    |----------|-----------------|  
    |**Обработка. По умолчанию**|Обнаруживает состояние обработки объекта секции и выполняет обработку, необходимую для перевода необработанных или частично обработанных объектов секции в полностью обработанное состояние. Выполняется загрузка данных для пустых таблиц и секций; иерархии, вычисляемые столбцы и связи строятся или перестраиваются.|  
    |**Обработка. Полная**|Обрабатывает объект секций и все объекты, которые в нем содержатся. Если объект, который обрабатывается методом полной обработки, уже был обработан, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] удаляют все данные объекта, а затем обрабатывают его. Этот тип обработки требуется при внесении структурных изменений в объект.|  
    |**Обработка данных**|Выполняется загрузка данных в секцию или таблицу без перестроения иерархий или связей или повторного вычисления вычисленных столбцов и мер.|  
    |**Обработка с очисткой**|Удаляет все данные из секции.|  
    |**Обработка с добавлением**|Постепенно обновляет секцию с включением новых данных.|  
  
4.  В столбце флажков **Обработка** выберите секции для обработки в текущем режиме и нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Секции табличных моделей](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [Создание секций табличной модели и управление ими](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)  
  
  
