---
title: "Применение атрибутов"
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
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e23649c5d833bef8b74ec5d3b9c22235756580e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="applying-attributes"></a>Применение атрибутов
Чтобы применить атрибут к элементу кода, выполните указанные ниже действия.  
  
1.  Определите новый атрибут или используйте уже существующий, импортировав его пространство имен из .NET Framework.  
  
2.  Примените атрибут к элементу кода, поместив его непосредственно перед элементом.  
  
     Каждый язык имеет собственный синтаксис атрибутов. В C++ и C# атрибут заключается в квадратные скобки и отделяется от элемента пробелами (к которым относится и разрыв строк). В Visual Basic атрибут заключается в угловые скобки и должен находиться на той же логической строке; если строку необходимо разбить, можно использовать символ продолжения строки.
  
3.  Укажите позиционные и именованные параметры атрибута.  
  
     Позиционные параметры обязательны и должны быть указаны перед именованными параметрами; они соответствуют параметрам одного из конструкторов атрибута. Именованные параметры необязательны и соответствуют свойствам чтения и записи атрибута. В C++ и C#, укажите `name` = `value` для каждого необязательного параметра, где `name` имя свойства. В Visual Basic укажите `name`:=`value`.  
  
 При компиляции кода атрибут передается в метаданные и становится доступным для среды CLR, а также пользовательских средств и приложений через службы отражения среды выполнения.  
  
 Как правило, все имена атрибутов заканчиваются словом Attribute. В то же время несколько языков, предназначенных для среды выполнения, таких как Visual Basic и C#, не требуют указывать полное имя атрибута. Например, если требуется инициализировать <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, необходимо сослаться на него как **Obsolete**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Применение атрибута к методу  
 В следующем примере кода показано, как объявить атрибут **System.ObsoleteAttribute**, помечающий код как устаревший. Строка `"Will be removed in next version"` передается атрибуту. Атрибут вызывает предупреждение компилятора, которое отображает переданную строку при вызове кода, описываемого этим атрибутом.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Применение атрибутов на уровне сборки  
 Если необходимо применять атрибут на уровне сборки, используйте ключевое слово **assembly** (`Assembly` в Visual Basic). В следующем коде показан атрибут **AssemblyTitleAttribute**, применяемый на уровне сборки.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Если атрибут применяется, строка `"My Assembly"` помещается в манифест сборки в раздел метаданных файла. Для просмотра атрибута можно воспользоваться [дизассемблером MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) или создать пользовательскую программу для извлечения атрибута.  
  
## <a name="see-also"></a>См. также  
 [Атрибуты](../../../docs/standard/attributes/index.md)  
 [Извлечение информации, сохраненной в атрибуте](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Основные понятия](/cpp/windows/attributed-programming-concepts)  
 [Атрибуты](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
