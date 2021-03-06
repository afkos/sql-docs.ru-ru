---
title: Настроить службу Azure Kubernetes для развертывания кластера SQL Server 2019 больших данных | Документация Майкрософт
description: Сведения о настройке службы Azure Kubernetes (AKS) для развернутых кластеров (Предварительная версия) SQL Server 2019 больших данных.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/06/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 07ee0ac0db742eca9a55decfcd78cb76b75e0160
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221660"
---
# <a name="configure-azure-kubernetes-service-for-sql-server-2019-preview-deployments"></a>Настроить службу Azure Kubernetes для развертываний SQL Server 2019 (Предварительная версия)

В этой статье описывается настройка службы Azure Kubernetes (AKS) для развертывания кластера (Предварительная версия) SQL Server 2019 больших данных. 

AKS позволяет легко создавать, настраивать и администрировать кластер виртуальных машин, настроенных с кластером Kubernetes для запуска контейнерных приложений. Это позволяет использовать имеющиеся навыки либо положиться большого и постоянно растущего сообщества опыт, развертывание и управление ими контейнерных приложений в Microsoft Azure.

В этой статье описаны шаги по развертыванию Kubernetes в AKS с помощью Azure CLI. Если у вас нет подписки Azure, создайте бесплатную учетную запись перед началом работы.

> [!TIP] 
> Пример скрипта python, выполняющий развертывание больших данных кластера AKS и SQL Server, см. в разделе [развертывание SQL Server, большие данные кластера в службе Azure Kubernetes (AKS)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="prerequisites"></a>предварительные требования

- Для среды AKS для оптимальной производительности при проверке основных сценариев мы рекомендуем по крайней мере три агента виртуальных машин (в дополнение к master), с помощью по крайней мере 4 виртуальных ЦП и оставить 32 ГБ памяти каждая. Инфраструктура Azure предлагает несколько вариантов размера для виртуальных машин, см. в разделе [здесь](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes) для выбранных элементов в регионе, который вы планируете развернуть.
  
- В этом разделе необходимо иметь Azure CLI версии 2.0.4 или более поздней версии. Если требуется выполнить установку или обновление, см. в разделе [Установка Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-azure-cli). Запустите `az --version` чтобы узнать версию, при необходимости.

- Установка [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) с как минимум версии 1.10 для сервера и клиента. Если вы хотите установить конкретную версию на клиент kubectl, см. в разделе [установки kubectl двоичных с помощью curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). Для AKS, необходимо использовать `--kubernetes-version` параметр, чтобы указать версию стандарта не по умолчанию.

> [!NOTE]
Обратите внимание, что это наклон версии клиента и сервера поддерживается +/-1 дополнительный номер версии. В документации по Kubernetes состояния «клиент должен быть неравномерно распределенных не более чем один дополнительный номер версии с главного сервера, что может привести образце, на один дополнительный номер версии. Например, версия 1.3 главной должны работать с версии 1.1, версия 1.2 и версия 1.3 узлов и должны работать с версии 1.2, версия 1.3 и клиентов версии 1.4.» Дополнительные сведения см. в разделе [Kubernetes поддерживаемые выпуски и наклона компонент](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/release/versioning.md#supported-releases-and-component-skew).

Кроме того, обратите внимание, что `az aks kubernetes install-cli` установит клиент kubectl с версией, снизить требуется 1.10. Выполните приведенные выше инструкции, чтобы установить правильную версию клиент kubectl.

## <a name="create-a-resource-group"></a>Создайте группу ресурсов

Группа ресурсов Azure — это логическая группа, в какие Azure развертываются и администрируются ресурсы. Следующие действия, вход в Azure и создайте группу ресурсов в кластере AKS.

> [!TIP]
> Если вы используете Windows, используйте PowerShell для дальнейших действий, описанных.

1. В командной строке выполните следующую команду и следуйте инструкциям на экране входа в подписку Azure:

    ```bash
    az login
    ```

1. Если у вас несколько подписок, всех подписок можно просмотреть, выполнив следующую команду:

   ```bash
   az account list
   ```

1. Если вы хотите изменить в другую подписку вы выполните следующую команду:

   ```bash
   az account set --subscription <subscription id>
   ```

1. Создайте группу ресурсов с помощью **Создание группы az** команды. В следующем примере создается группа ресурсов, с именем `sqlbigdatagroup` в `westus2` расположение.

   ```bash
   az group create --name sqlbigdatagroup --location westus2
   ```

## <a name="create-a-kubernetes-cluster"></a>Создание кластера Kubernetes

1. Создание кластера Kubernetes в AKS при помощи [создать az aks](https://docs.microsoft.com/cli/azure/aks) команды. В следующем примере создается кластер Kubernetes с именем *kubcluster* с Linux одного главного узла и двух узлов агентов Linux. Убедитесь, что вы создаете кластер AKS в той же группе ресурсов, который использовался в предыдущих разделах.

    ```bash
   az aks create --name kubcluster \
    --resource-group sqlbigdatagroup \
    --generate-ssh-keys \
    --node-vm-size Standard_E4s_v3 \
    --node-count 3 \
    --kubernetes-version 1.10.8
    ```

    Можно увеличить или уменьшить количество агентов по умолчанию, изменив `--node-count <n>` где `<n>` — количество узлов агентов, которые вы хотите иметь.

    Через несколько минут команда завершается и возвращает информацию о кластере в формате JSON.

1. Сохранение выходных данных JSON из предыдущей команды для последующего использования.

## <a name="connect-to-the-cluster"></a>Подключитесь к кластеру

1. Чтобы настроить kubectl для подключения к кластеру Kubernetes, выполните [az aks get-credentials](https://docs.microsoft.com/cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials) команды. Этот шаг скачиваются учетные данные и настройка интерфейса командной строки, чтобы их использовать kubectl.

   ```bash
   az aks get-credentials --resource-group=sqlbigdatagroup --name kubcluster
   ```

1. Чтобы проверить подключение к кластеру, используйте [kubectl get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) команду, чтобы получить список узлов кластера.  В приведенном ниже примере показаны выходные данные при 1 главный, а 3 узлов агентов.

   ```bash
   kubectl get nodes
   ```

## <a name="next-steps"></a>Следующие шаги

Действия, описанные в этой статье настроить кластер Kubernetes в AKS. Следующим шагом является развертывание SQL Server 2019 больших данных в кластере.

[Краткое руководство по Развертыванию кластера больших данных SQL Server в службе Azure Kubernetes (AKS)](quickstart-big-data-cluster-deploy.md)
