---
title: Свойство MultiIpConfigurationSupport (класс ServerNetworkProtocol) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 49b98a6680ba05e13b9fe0ea76a1d445f0d57200
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217712"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>Свойство MultiIpConfigurationSupport (класс ServerNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает логическое свойство, определяющее, поддерживаются ли несколько IP-адресов сетевым протоколом сервера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [свойство ProtocolName (класс ServerNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/protocolname-property-servernetworkprotocol-class.md) , представляющий сетевой протокол, используемый экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Логическое значение, указывающее, поддерживает ли несколько IP-адресов сетевой протокол сервера: **true** Если поддерживается несколько IP-адресов сетевым протоколом сервера или **false** Если несколько IP-адресов не поддерживаются сетевой протокол сервера.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Настройка сетевых протоколов сервера и сетевых библиотек](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
