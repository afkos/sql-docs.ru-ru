---
title: Столбцы с именем XPath-функции проверки узла | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 27b3e78f821dd2b2debe28647ced66c8919aeb0c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795022"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>Столбцы с именем XPath-функции проверки узла
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Если имя столбца является одной из XPath-функций проверки узла, сопоставление содержимого производится, как указано в следующей таблице. Когда имя столбца является XPath-функцией проверки узла, содержимое сопоставляется с соответствующим узлом. Если столбец имеет SQL-тип **xml**, возвращается ошибка.  
  
|Имя столбца|Поведение|  
|-----------------|--------------|  
|text()|Строковое значение столбца с именем text() добавляется в качестве текстового узла.|  
|comment()|Строковое значение столбца с именем text() добавляется в качестве комментария XML.|  
|node()|Для столбца с именем node() результат аналогичен результату, получаемому для столбца с символом-шаблоном (*) в качестве имени.|  
|processing-instruction(name)|Строковое значение столбца с именем инструкции по обработке добавляется в качестве значения инструкции для целевого имени инструкции по обработке.|  
  
 В следующем запросе показано использование проверочных узлов в качестве имен столбцов. При этом текстовые узлы и комментарии добавляются в результирующий XML-документ.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Результат:  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>См. также:  
 [Использование режима PATH совместно с FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
