---
title: Создание атрибута даты (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1da9ecf9ec7278b91e16a6c91a95aa09473ca023
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100125"
---
# <a name="create-a-date-attribute-master-data-services"></a>Создание атрибута даты (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]атрибут даты создается, если нужно, чтобы пользователи вводили даты как значения атрибута.  
  
> [!NOTE]  
>  Атрибут называется DateTime, но значения времени не поддерживаются.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
-   Должна существовать сущность, для которой создается атрибут. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-create-a-date-attribute"></a>Создание атрибута даты  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Выберите строку сущности, для которой необходимо создать атрибут.  
  
5.  Щелкните **Изменить выбранную сущность**.  
  
6.  На странице **Изменение сущности** :  
  
    -   если атрибут предназначен для конечных элементов, выберите команду **Добавить конечный атрибут** на панели **Атрибуты конечных элементов**;  
  
    -   если атрибут предназначен для объединенных элементов, выберите команду **Добавить объединенный атрибут** на панели **Атрибуты консолидированных элементов**;  
  
    -   если атрибут предназначен для коллекций, выберите команду **Добавить атрибут коллекции** на панели **Атрибуты коллекций**.  
  
7.  Выберите параметр **В свободной форме** на странице **Добавить атрибут** .  
  
8.  Введите имя атрибута в поле **Имя** . Список слов, которые не должны использоваться как имена атрибутов, см. в разделе [Зарезервированные слова (службы Master Data Services)](../../2014/master-data-services/reserved-words-master-data-services.md).  
  
9. В поле **Ширина отображаемой области (в пикселях)** введите ширину столбца атрибута для отображения в сетке **обозревателя** .  
  
10. В списке **Тип данных** выберите **DateTime**.  
  
11. Выберите из списка **Маска ввода** формат дат.  
  
12. По желанию установите флажок **Включить отслеживание изменений** , чтобы отслеживать изменения в группах атрибутов. Дополнительные сведения см. в разделе [Добавление атрибутов в группу отслеживания изменений (службы Master Data Services)](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Нажмите кнопку **Сохранить атрибут**.  
  
14. На странице **Обслуживание сущности** нажмите кнопку **Сохранить сущность**.  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a>Отображение части времени значения типа datetime  
 Чтобы пользовательский интерфейс отображал время из значения типа datetime, необходимо выбрать подходящую маску ввода для этого атрибута. Для этого не подходит ни одна из встроенных масок для атрибутов значения типа Datetime, но вы можете добавить новую маску, которая позволит отобразить значение времени. Для этого добавьте строку в таблицу mdm.tblList базы данных MDS, где будут храниться встроенные маски. Строка должна иметь следующие значения:  
  
|||  
|-|-|  
|ListCode|lstInputMask|  
|ListName|Маска ввода|  
|Seq|19|  
|List Option|dd/MM/yyyy hh:mm:ss tt|  
|Option ID|19|  
|IsVisible|1|  
|Group_ID|3|  
  
 После ввода строки с приведенными выше значениями в таблицу mdm.tblList маска dd/MM/yyyy hh:mm:ss tt становится доступной в списке масок ввода. Теперь вы можете выбрать эту маску для отображения даты и времени в столбце атрибутов datetime сущности в обозревателе MDS.  
  
 Маска ввода — это настраиваемая строка форматирования даты и времени .NET. Дополнительную информацию см. в разделе [Настраиваемые строки формата даты и времени](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)  
  
## <a name="see-also"></a>См. также  
 [Атрибуты (службы Master Data Services)](../../2014/master-data-services/attributes-master-data-services.md)   
 [Изменение имени атрибута &#40;службы Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md)   
 [Создание атрибута на основе домена (службы Master Data Services)](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Создание файлового атрибута (службы Master Data Services)](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
