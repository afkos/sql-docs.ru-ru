---
title: 'Настройка TLS 1.2 в Analytics Platform System | Документация Майкрософт '
description: Рекомендацию, чтобы настроить протокол TLS 1.2 в APS
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 10/29/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 638633a84721532ad05a52126aa7bcfd3f2bb6b7
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2018
ms.locfileid: "50237196"
---
# <a name="configure-tls-12-in-aps"></a>Настройка TLS 1.2 в APS

Чтобы защитить APS на использование только протокола TLS 1.2, необходимо явно отключить другой протокол на всех физических и виртуальных узлов. Отключение протоколов требуется изменения параметров реестра.

> [!WARNING]
> Настоящий раздел, метод или задача содержит шаги, в которых указано, как внести изменения в реестр. Тем не менее при изменении реестра неправильно, может привести к потере данных и необходимости переустановки операционной системы, могут возникнуть серьезные проблемы. Настоятельно рекомендуется создать резервную копию реестра перед внесением изменений. Тогда в случае возникновения проблем реестр можно будет восстановить. Дополнительные сведения о том, как резервное копирование и восстановление реестра щелкните следующий номер статьи базы знаний Майкрософт:<br>
[322756](https://support.microsoft.com/en-us/help/322756) как резервное копирование и восстановление реестра Windows

**Отключите:**
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.0\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1]
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Client]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.1\Server]
"Enabled"=dword:00000000
"DisabledByDefault"=dword:00000001
```

Также задайте следующие разделы на клиентском компьютере машин где установлены средства как адаптеры назначения APS служб SSIS.
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001 
```



