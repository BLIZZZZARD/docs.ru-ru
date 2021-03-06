---
title: "Практическое руководство. Выполнение действий при получении данных блоком потоков данных"
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
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d049d20f5e685096a72857cd18a89688633883c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Практическое руководство. Выполнение действий при получении данных блоком потоков данных
Типы *блоков выполнения потоков данных* вызывают предоставленный пользователем делегат при получении данных. Классы <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> и <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> являются типами блоков выполнения потока данных. Можно использовать ключевое слово `delegate` (`Sub` в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), <xref:System.Action%601>, <xref:System.Func%602> или лямбда-выражение при предоставлении рабочей функции блоку выполнения потока данных. В этом документе описано, как использовать <xref:System.Func%602> и лямбда-выражения для выполнения действий в блоках выполнения.  
  
> [!TIP]
>  Библиотека потоков данных TPL (пространство имен <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) не поставляется с [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Чтобы установить <xref:System.Threading.Tasks.Dataflow> пространства имен, откройте проект в [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], выберите **управление пакетами NuGet** меню проекта и выполните поиск в Интернете `Microsoft.Tpl.Dataflow` пакета.  
  
## <a name="example"></a>Пример  
 В следующем примере используется поток данных для считывания файла с диска и вычисления количества равных нулю байтов в этом файле. Здесь используется <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> для считывания файла и вычисления числа нулевых байтов и <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> для вывода числа нулевых байтов на консоль. Объект <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> определяет объект <xref:System.Func%602> для выполнения работы, когда блоки получают данные. Объект <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> использует лямбда-выражение для печати на консоль числа прочитанных нулевых байтов.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Хотя можно предоставить объекту <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> лямбда-выражение, в этом примере используется <xref:System.Func%602>, чтобы позволить использовать метод `CountBytes` другому коду. Объект <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> использует лямбда-выражение, потому что работа, которую следует выполнить, специфична для этой задачи и вряд ли будет полезна для использования из другого кода. Дополнительные сведения о работе лямбда-выражений в библиотеке параллельных задач см. в разделе [Лямбда-выражения в PLINQ и библиотеке параллельных задач](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 В подразделе Сводка делегировать типы в [потока данных](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) документе кратко описаны типы делегатов, которые можно предоставлять <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, и <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> объектов. В таблице также указано, работает ли делегат данного типа синхронно или асинхронно.  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Скопируйте код примера и вставьте его в проект Visual Studio или в файл с именем `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` для [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), затем выполните в окне командной строки Visual Studio следующую команду.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Этот пример предоставляет делегат типа <xref:System.Func%602> объекту <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> для синхронного выполнения задачи блока потока данных. Чтобы позволить блоку потока данных работать асинхронно, предоставьте блоку потока данных делегат типа <xref:System.Func%601>. Если блок потока данных работает асинхронно, задача блока потока данных завершается, только когда завершается возвращенный объект <xref:System.Threading.Tasks.Task%601>. В следующем примере изменяется метод `CountBytes` и используются операторы [async](~/docs/csharp/language-reference/keywords/async.md) и [await](~/docs/csharp/language-reference/keywords/await.md) ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) и [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) для асинхронного подсчета общего количества нулевых байтов в предоставленном файле. Метод <xref:System.IO.FileStream.ReadAsync%2A> выполняет операции чтения файла асинхронно.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Можно также использовать асинхронные лямбда-выражения для выполнения действий в блоке выполнения потока данных. В следующем примере изменяется объект <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, используемый в предыдущем примере, чтобы он использовал лямбда-выражение для выполнения работы в асинхронном режиме.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>См. также  
 [Поток данных](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
