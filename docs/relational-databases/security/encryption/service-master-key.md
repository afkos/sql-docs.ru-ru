---
title: Главный ключ службы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server]
- service master key [SQL Server], about service master key
ms.assetid: 85f2095d-2590-4f59-8a29-7e100edd02bb
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: fdf2165b76c7c3d9526995b00a608b0017a0c065
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837142"
---
# <a name="service-master-key"></a>главный ключ службы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Главный ключ службы является корнем иерархии шифрования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Он создается автоматически, как только он впервые понадобится для шифрования другого ключа. По умолчанию главный ключ службы шифруется с помощью API-интерфейса защиты данных Windows и ключа локального компьютера. Главный ключ службы может быть открыт только учетной записью службы Windows, под которой он был создан, либо участником, имеющим доступ к имени и паролю учетной записи службы.  
  
 Для повторного создания или восстановления из копии главного ключа службы необходимо дешифровать и снова зашифровать всю иерархию шифрования. Если только ключ не был похищен, данную ресурсоемкую операцию следует планировать на то время, когда количество обращений к серверу минимальное.  
  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] использует для защиты главного ключа службы и главного ключа базы данных алгоритм шифрования AES. AES — это новый алгоритм шифрования, отличный от алгоритма 3DES, используемого в более ранних версиях. После обновления экземпляра компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] до [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] необходимо заново сформировать главный ключ службы и главный ключ базы данных, чтобы обновить главные ключи до алгоритма AES. Дополнительные сведения о повторном создании главного ключа базы данных см. в статьях [ALTER SERVICE MASTER KEY (Transact-SQL)](../../../t-sql/statements/alter-service-master-key-transact-sql.md) и [ALTER MASTER KEY (Transact-SQL)](../../../t-sql/statements/alter-master-key-transact-sql.md).  
  
## <a name="best-practice"></a>Рекомендации  
 Создайте резервную копию главного ключа службы и храните ее на безопасном автономном компьютере.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [BACKUP SERVICE MASTER KEY (Transact-SQL)](../../../t-sql/statements/backup-service-master-key-transact-sql.md)  
  
 [RESTORE SERVICE MASTER KEY (Transact-SQL)](../../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
 [ALTER SERVICE MASTER KEY (Transact-SQL)](../../../t-sql/statements/alter-service-master-key-transact-sql.md)  
  
## <a name="see-also"></a>См. также:  
 [Иерархия средств шифрования](../../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
