---
title: Определение конвертации валюты (мастер бизнес-аналитики) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.existingscriptpage.f1
ms.assetid: 37dd65b7-9d8d-44ad-b316-96a92c622472
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e7cca289615e94cd4ccfbcee038e002c33700be8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099244"
---
# <a name="define-currency-conversion-business-intelligence-wizard"></a>Определение конвертации валюты (мастер бизнес-аналитики)
  Страница **Определение конвертации валют** используется для просмотра скриптов многомерных выражений, содержащих функцию конвертации валюты, которая сформирована мастером бизнес-аналитики. После этого скрипт многомерных выражений, сформированный мастером, можно использовать для замены или дополнения ранее определенной функции конвертации валюты в скрипте многомерных выражений куба.  
  
> [!NOTE]  
>  Данная страница отображается, только если мастер бизнес-аналитики обнаруживает по крайней мере одну предварительно определенную конвертацию валюты в скрипте многомерных выражений для куба. В скрипте многомерных выражений для куба конвертации валют выделяются следующими комментариями:  
>   
>  `//<Currency conversion>`  
>   
>  `...`  
>   
>  `[MDX statements for the currency conversion]`  
>   
>  `...`  
>   
>  `//</Currency conversion>`  
>   
>  При изменении или удалении этих комментариев мастер бизнес-аналитики может быть неспособен обнаружить предварительно определенную конвертацию валюты.  
  
## <a name="options"></a>Параметры  
 **Новый скрипт конвертации валюты**  
 Отображает скрипт многомерных выражений, сформированный в текущем сеансе мастера бизнес-аналитики.  
  
 **Перезаписать существующий скрипт конвертации валюты**  
 Выберите, чтобы заменить скрипт многомерных выражений, отображаемый в окне **Существующий скрипт конвертации валюты** , скриптом многомерных выражений, отображаемым в окне **Новый скрипт конвертации валюты**.  
  
 **Добавьте после**  
 Выберите для добавления скрипта многомерных выражений, отображаемого в окне **Новый скрипт конвертации валюты** , к концу скрипта многомерных выражений, отображаемого в окне **Существующий скрипт конвертации валюты**. Добавленный скрипт отобразится в виде нового раздела.  
  
 **Существующий скрипт конвертации валюты**  
 Выберите раздел существующего скрипта многомерных выражений, содержащий ранее определенную функцию конвертации валюты, который необходимо заменить или дополнить.  
  
## <a name="see-also"></a>См. также  
 [Справка F1 мастера бизнес-аналитики](business-intelligence-wizard-f1-help.md)   
 [Конструктор кубов &#40;службы Analysis Services — многомерные данные&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Конструктор измерений &#40;службы Analysis Services — многомерные данные&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
