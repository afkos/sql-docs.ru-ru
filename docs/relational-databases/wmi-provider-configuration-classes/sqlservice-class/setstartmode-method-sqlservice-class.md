---
title: Метод SetStartMode (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 9d1720bc8aba384b4a3b10969abbcc4cfb5cf3fc
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217462"
---
# <a name="setstartmode-method-sqlservice-class"></a>Метод SetStartMode (класс SqlService)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Изменяет режим запуска экземпляра службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SqlService](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , представляющий службу.  
  
#### <a name="parameters"></a>Параметры  
 *StartMode*  
 Значение **uint32** , определяющее режим запуска экземпляра службы.  
  
 Допустимы следующие значения.  
  
 Значение = 0. Загрузка — драйвер устройства запускается загрузчиком операционной системы. Это значение допустимо только для служб драйверов.  
  
 Значение = 1. Загрузка — драйвер устройства запускается методом **IoInitSystem** . Это значение допустимо только для служб драйверов.  
  
 Значение = 2. Автоматически — служба запускается автоматически диспетчером управления службами во время запуска системы.  
  
 Значение = 3. Вручную — служба запускается оснасткой «Управление компьютером», когда процесс вызывает метод **StartService** .  
  
 Значение = 4. Отключена — служба больше не запускается.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение **uint32** , равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Запуск и остановка служб](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
