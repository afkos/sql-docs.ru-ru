---
title: Шаг 3. Проверка пакета, созданного на занятии 6 | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: c184c92d-948f-4037-a502-5fabd909c84c
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9ddacdc7ede5d65132912783464250ff5f0db6bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122034"
---
# <a name="step-3-testing-the-lesson-6-package"></a>Шаг 3. Проверка пакета, созданного на занятии 6
  Во время выполнения пакет получит значение для свойства Directory из параметра VarFolderName.  
  
 Чтобы убедиться, что пакет обновляет свойство Directory новым значением во время выполнения, выполните пакет. Поскольку в новый каталог были скопированы только три файла образцов данных, поток данных будет запущен только три раза, а не 14 раз в соответствии с количеством файлов в исходном каталоге.  
  
## <a name="checking-the-package-layout"></a>Проверка макета пакета  
 Прежде чем тестировать пакет, следует убедиться, что поток управления и поток данных пакета, созданного на занятии 6, содержит объекты, показанные на следующих диаграммах. Поток управления должен быть таким же, как и поток управления в занятии 5. Поток данных должен быть идентичен потоку данных в занятии 5.  
  
 **Поток управления**  
  
 ![Поток управления](../../2014/tutorials/media/task3lesson6control.jpg "поток управления")  
  
 **Поток данных**  
  
 ![Поток данных](../../2014/tutorials/media/task3lesson6data.jpg "потока данных")  
  
### <a name="to-test-the-lesson-6-tutorial-package"></a>Тестирование пакета учебника Lesson 6  
  
1.  В меню Отладка выберите команду Начать отладку.  
  
2.  После окончания работы пакета выберите в меню Отладка пункт Остановить отладку.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 4. Развертывание пакета, созданного на занятии 6](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
  
