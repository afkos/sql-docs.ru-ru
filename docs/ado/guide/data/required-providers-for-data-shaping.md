---
title: Необходимые поставщики для формирования данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 482139f8aa3dc42bbd17593b58fcc8510f1fc9a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713842"
---
# <a name="required-providers-for-data-shaping"></a>Обязательные поставщики для формирования данных
Обычно для формирования данных требуется два поставщика. Поставщик услуг [службы Data Shaping Service для OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), предоставляет формирования функции и поставщика данных, таких как поставщик OLE DB для SQL Server данных, передает строки данных, чтобы заполнить форму [набора записей ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 В качестве значения можно указать имя поставщика услуг (MSDataShape) [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объект [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) свойство или ключевое слово строки подключения «поставщик = MSDataShape;».  
  
 Можно указать имя поставщика данных для параметра **поставщик данных** динамическое свойство, добавляемое к **подключения** объект [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции с помощью службы Data Shaping Service для OLE DB или ключевое слово строки подключения «**поставщик данных = *** поставщика*«.  
  
 Поставщик данных не является обязательным, если **записей** не заполняется (например, в которое **записей** где столбцы создаются с помощью ключевого слова NEW). В этом случае указывается "**поставщик данных =** none;».  
  
## <a name="example"></a>Пример  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формального формирования данных](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
