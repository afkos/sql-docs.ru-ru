---
title: Изменить дискретизацию столбца в модели интеллектуального анализа данных | Документы Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e9d6b2c75becad147e196534bb4d366dff01a13d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="change-the-discretization-of-a-column-in-a-mining-model"></a>изменить дискретизацию столбца в модели интеллектуального анализа данных
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В некоторых сценариях службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически дискретизируют значения, то есть сегментируют данные в цифровом столбце. Например, если в данных содержатся непрерывные числовые данные и создается модель дерева принятия решений, каждый столбец непрерывных данных автоматически будет сегментирован (в зависимости от распределения данных). Если вам необходимо управлять процессом дискретизации данных, измените свойства столбца структуры интеллектуального анализа данных, управляющие использованием данных в модели.  
  
 Общие сведения о задании свойств в модели интеллектуального анализа данных см. в разделе [Столбцы модели интеллектуального анализа данных](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-display-the-properties-for-a-mining-model-column"></a>Отображение свойств столбца модели интеллектуального анализа данных  
  
1.  На вкладке **Модели интеллектуального анализа данных** в конструкторе интеллектуального анализа данных щелкните правой кнопкой мыши либо заголовок столбца, содержащего имя модели интеллектуального анализа данных, либо строку сетки, содержащую имя алгоритма. Потом выберите **Свойства**.  
  
     В окне **Свойства** отображаются свойства, связанные с моделью интеллектуального анализа данных в целом.  
  
2.  В столбце **Структура** , расположенном на левой стороне экрана, щелкните по столбцу, содержащему подлежащие дискретизации непрерывные числовые данные.  
  
     Окно **Свойства** изменится и будет отображать только те свойства, которые связаны с выбранным столбцом.  
  
### <a name="to-change-the-discretization-method"></a>Изменение метода дискретизации  
  
1.  В окне **Свойства интеллектуального анализа данных** щелкните по текстовому полю **Содержимое**и выберите в раскрывающемся списке пункт **Discretized** .  
  
     В окне <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> и <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> включены.  
  
2.  На вкладке **Свойства** щелкните по текстовому полю <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> и выберите одно из следующих значений: **Automatic**, **EqualAreas**или **Cluster**.  
  
    > [!NOTE]  
    >  Если использование столбца установлено в значение **Ignore**, окно **Свойства** для данного столбца будет пустым.  
  
     Новое значение вступает в силу после выбора другого элемента в конструкторе.  
  
3.  На вкладке **Свойства** щелкните по текстовому полю <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> и введите числовое значение.  
  
    > [!NOTE]  
    >  После изменения данных свойств необходимо выполнить повторную обработку структуры и всех моделей, для которых должны действовать новые настройки.  
  
## <a name="see-also"></a>См. также  
 [Задачи модели интеллектуального анализа данных и инструкции](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
