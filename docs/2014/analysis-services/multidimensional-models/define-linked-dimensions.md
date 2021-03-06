---
title: Определение связанных измерений | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 409cdbaa10dc93c5cb659961f084d76bc3370bde
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114239"
---
# <a name="define-linked-dimensions"></a>Определите связанные измерения
  Связанное измерение основано на измерении, созданном и хранящемся в другой базе данных служб Analysis Services с той же версией и уровнем совместимости. С помощью связанного измерения можно создавать, хранить и поддерживать измерения в одной базе данных, при этом данное измерение будет доступно для пользователей нескольких баз данных. Для пользователей связанное измерение ничем не отличается от других измерений.  
  
 Связанные измерения доступны только для чтения. Если необходимо изменить измерение или создать новые связи, необходимо изменить исходное измерение, а затем удалить и повторно создать связанное измерение и его связи. Обновлять связанное измерение, чтобы получить изменения из исходного объекта, нельзя.  
  
 Все связанные группы мер и измерения должны находиться в одной и той же базе данных-источнике. Нельзя создавать связи между локальными группами мер и связанными измерениями, добавленными в куб. После добавления связанных измерений и групп мер к текущему кубу связи между ними должны поддерживаться в их базе данных-источнике.  
  
> [!NOTE]  
>  Поскольку обновление недоступно, большинство разработчиков служб Analysis Services предпочитают копировать измерения, а не связать их. Можно копировать измерения между проектами в рамках одного решения. Дополнительные сведения см. в разделе [Обновление связанных измерений в службах SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx).  
  
## <a name="prerequisites"></a>предварительные требования  
 База данных, предоставляющая измерение, и текущая база данных, использующая его в данный момент, должны иметь одну и ту же версию и уровень совместимости. Дополнительные сведения см. в разделе [установить уровень совместимости многомерной базы данных &#40;служб Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
 База данных-источник должна быть развернута и находиться в режиме «в сети». Серверы, публикующие или использующие связанные объекты, должны быть настроены на разрешение операции (см. ниже).  
  
 Используемое измерение не может быть связанным измерением.  
  
## <a name="configure-server-to-allow-linked-objects"></a>Настройте сервер на разрешение связанных объектов  
  
1.  Установите соединение с сервером служб Analysis Services в SQL Server Management Studio. В обозревателе объектов щелкните правой кнопкой мыши имя сервера и выберите пункт **Аспекты**.  
  
2.  Установите для параметра **LinkedObjectsLinksFromOtherInstancesEnabled** значение **TRUE** , чтобы разрешить серверу выполнять запросы к связанным объектам, которые расположены в базах данных, выполняющихся на других экземплярах.  
  
3.  Установите для параметра **LinkedObjectsLinksToOtherInstances** значение **TRUE** , чтобы разрешить серверу запрашивать данные для связанных объектов в базах данных, работающих на других экземплярах.  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a>Создайте связанное измерение в SQL Server Data Tools  
  
1.  Запустите мастер. В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]щелкните правой кнопкой мыши папку **Измерения** в базе данных или проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , а затем выберите **Создать связанное измерение**.  
  
2.  Установите соединение с базой данных Analysis Services, предоставляющей измерение. На странице **Выбор источника данных** мастера связанных объектов выберите источник данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] или создайте новый.  
  
3.  На странице **Выбор объектов** мастера выберите измерения, которые необходимо связать с удаленной базой данных.  
  
4.  На странице **Завершение работы мастера** можно предварительно просмотреть связанные объекты. При связывании измерения, имеющего имя, которое уже существует, к этому имени будет добавлен порядковый номер (начиная с 1 для первого дублирующегося имени). После завершения работы мастера измерение добавляется к папке **Измерения** .  
  
##  <a name="bkmk_CreateNew"></a> Создайте новое соединение с источником данных, подключившись к базе данных служб Analysis Services.  
 Используйте мастер создания источников данных, чтобы добавить в проект сведения о соединении с базой данных служб Analysis Services, предоставляющей измерение. Мастер можно запустить, нажав кнопку **Создать новый источник данных** на странице «Выбор источника данных» мастера связанных объектов.  
  
1.  В мастере источников данных на странице «Выбор метода определения соединения» нажмите кнопку **Создать**.  
  
2.  В диспетчере соединений проверьте, что установлен поставщик **Собственный поставщик OLE DB\Поставщик OLE DB для служб Analysis Services 11.0 (Майкрософт)**.  
  
3.  Введите имя сервера (использовать *servername*\\*instancename* для именованного экземпляра)<sup>1</sup> или тип **localhost** для Подключитесь к серверу служб Analysis Services, на котором выполняется на одном компьютере.  
  
4.  Используйте проверку подлинности Windows для соединения.  
  
5.  В **исходном каталоге**нажмите стрелку вниз, чтобы выбрать базу данных на этом сервере.  
  
6.  В мастере источников данных нажмите кнопку **Далее** , чтобы продолжить.  
  
7.  На странице «Сведения об олицетворении» выберите **Использовать учетную запись службы**. Нажмите кнопку **Далее**и завершите работу мастера. Созданное соединение будет выбрано в мастере связанных объектов.  
  
## <a name="next-steps"></a>Следующие шаги  
 Структуру связанного измерения изменить нельзя, поэтому она не отображается на вкладке **Структура измерения** конструктора измерений. После обработки связанного измерения его можно просмотреть на вкладке **Браузер** . Также можно изменить его имя и создать перевод для имени.  
  
## <a name="see-also"></a>См. также  
 [Уровень совместимости многомерной базы данных &#40;служб Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Связанные группы мер](linked-measure-groups.md)   
 [Связи измерений](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
