---
title: "delegate (Справочник по C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a>delegate (Справочник по C#)
Объявление типа делегата аналогично сигнатуре метода. Оно имеет возвращаемое значение и любое число параметров любого типа:  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 Ключевое слово `delegate` имеет ссылочный тип, который можно использовать для инкапсуляции именованного или анонимного метода. Делегаты аналогичны используемым в языке C++ указателям функций, но являются типобезопасными и безопасными. Сведения о применении делегатов см. в разделах [Делегаты](../../../csharp/programming-guide/delegates/index.md) и [Универсальные делегаты](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## <a name="remarks"></a>Примечания  
 Делегаты являются основой [событий](../../../csharp/programming-guide/events/index.md).  
  
 Экземпляры делегата могут создаваться путем его связывания с именованным или анонимным методом. Дополнительные сведения см. в разделах [Именованные методы](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) и [Анонимные методы](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 Делегат должен быть создан при помощи метода или лямбда-выражения, имеющего совместимые возвращаемый тип и входные параметры. Дополнительные сведения о допустимой степени вариации сигнатур методов см. в разделе [Вариативность в делегатах](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Для использования с анонимными методами делегат и код, который должен быть связан с ним, должны быть объявлены вместе. В этом разделе рассматриваются оба способа создания экземпляров делегатов.  
  
## <a name="example"></a>Пример  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>Спецификация языка C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Справочник по C#](../../../csharp/language-reference/index.md)  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Ключевые слова в C#](../../../csharp/language-reference/keywords/index.md)  
 [Ссылочные типы](../../../csharp/language-reference/keywords/reference-types.md)  
 [Делегаты](../../../csharp/programming-guide/delegates/index.md)  
 [События](../../../csharp/programming-guide/events/index.md)  
 [Делегаты с именованными методами и делегаты с анонимными методами](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [Анонимные методы](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
