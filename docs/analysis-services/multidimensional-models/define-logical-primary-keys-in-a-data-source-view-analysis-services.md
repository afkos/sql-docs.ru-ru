---
title: Определение логических первичных ключей в представлении источника данных (службы Analysis Services) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 90684f55414fa9e3f0d68a8ec90884fdae4d2c0a
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34021070"
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a>Определение логических первичных ключей в представлении источника данных (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Мастер представлений источника данных и конструктор представлений источника данных автоматически определяют первичный ключ для таблицы, добавляемой в представление источника данных на основе базовой таблицы базы данных.  
  
 Иногда может потребоваться вручную определить первичный ключ в представлении источника данных. Например, по соображениям производительности или архитектурным соображениям таблицы в источнике данных могут не иметь явно определенных первичных ключевых столбцов. В именованных запросах и представлениях первичный ключевой столбец для таблицы также может опускаться. Если таблица, представление или именованный запрос не имеют заданного физического первичного ключа, можно вручную задать логический первичный ключ для таблицы или именованного запроса в конструкторе представлений источника данных.  
  
## <a name="set-a-logical-primary-key"></a>Установка логического первичного ключа  
 Первичные ключи требуются в службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для уникальной идентификации записей в таблице, идентификации ключевых столбцов в таблицах измерений и для поддержки связей между таблицами, представлениями и именованными запросами. Эти связи используются при построении запросов для получения данных и метаданных из базовых источников данных и для использования преимуществ расширенных функций бизнес-аналитики.  
  
 В качестве логического первичного ключа можно использовать любой столбец, включая именованное вычисление. При создании логического первичного ключа в представлении источника данных создается ограничение уникальности, которое помечается как ограничение первичного ключа. Любой другой существующий в выбранной таблице логический первичный ключ удаляется.  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект или подключитесь к базе данных, содержащей представление источника данных, в котором необходимо установить логический первичный ключ.  
  
2.  В обозревателе решений откройте папку **Представления источников данных** и дважды щелкните представление источника данных.  
  
     Чтобы найти таблицу или представление, можно использовать команду **Поиск таблицы** , выбрав меню **Представление источника данных**  или щелкнув правой кнопкой мыши рабочую область панели **Таблицы** или панели **Диаграмма** .  
  
3.  В соответствующей таблице на панели **Таблицы** или **Диаграмма** щелкните правой кнопкой мыши столбец или столбцы, которые необходимо использовать для определения логического первичного ключа, а затем выберите **Задать логический первичный ключ**.  
  
     Параметр задания логического первичного ключа доступен только для таблиц без первичного ключа.  
  
     Обратите внимание, что после задания ключа первичные ключевые столбцы теперь отмечены значком ключа.  
  
## <a name="see-also"></a>См. также  
 [Представления источников данных в многомерных моделях](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Определение именованных вычислений в представлении источника данных & #40; Службы Analysis Services & #41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
