---
title: "Практическое руководство. Реализация шаблона потока данных \"производитель-получатель\""
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1aba08e8364d8a21f70ab480d58041115a4849e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Практическое руководство. Реализация шаблона потока данных "производитель-получатель"
В этом документе описан способ использования библиотеки потоков данных TPL для реализации шаблона "производитель-получатель". В этом шаблоне *производитель* отправляет сообщения в блок сообщений, а *потребитель* считывает сообщения из этого блока.  
  
> [!TIP]
>  Библиотека потоков данных TPL (пространство имен <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) не поставляется с [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Чтобы установить <xref:System.Threading.Tasks.Dataflow> пространства имен, откройте проект в [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], выберите **управление пакетами NuGet** меню проекта и выполните поиск в Интернете `Microsoft.Tpl.Dataflow` пакета.  
  
## <a name="example"></a>Пример  
 В следующем примере показана базовая модель "производитель-получатель", которая использует поток данных. Метод `Produce` записывает массивы, содержащие случайные байты данных, в объект <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType>, а метод `Consume` выполняет чтение байтов из объекта <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>. Используя интерфейсы <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> и <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> вместо их производных типов, можно создавать пригодный для повторного использования код, который может работать с различными типами блоков потока данных. В этом примере используется класс <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>. Поскольку класс <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> действует и как блок источника, и как целевой блок, потребитель и производитель могут использовать общий объект для передачи данных.  
  
 Метод `Produce` вызывает метод <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> в цикле для синхронной записи данных в целевой блок. После того, как метод `Produce` записывает все данные в целевой блок, он вызывает метод <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A>, чтобы указать, что у этого блока никогда не будет дополнительных доступных данных. `Consume` Использует метод [async](~/docs/csharp/language-reference/keywords/async.md) и [await](~/docs/csharp/language-reference/keywords/await.md) операторы ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) и [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) для асинхронно вычислить общее количество байтов, полученных из <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> объекта. Для асинхронной работы метод `Consume` вызывает метод <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>, чтобы получать уведомления, если блок источника получит доступные данные и если у блока источника никогда не будет дополнительных доступных данных.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Скопируйте код примера и вставьте его в проект Visual Studio или в файл с именем `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` для [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), затем выполните в окне командной строки Visual Studio следующую команду.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 В этом примере используется только один получатель для обработки исходных данных. При наличии нескольких получателей в приложении следует использовать метод <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> для чтения данных из блока источника, как показано в следующем примере.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Метод <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> возвращает `False`, когда нет доступных данных. Когда несколько потребителей должны использовать блок источника параллельно, этот механизм гарантирует, что данные все еще будут доступны после вызова <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
