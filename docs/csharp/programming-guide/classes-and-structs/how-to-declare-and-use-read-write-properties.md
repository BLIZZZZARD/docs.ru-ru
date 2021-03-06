---
title: "Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c17bdd05196f834b491c69f648bec0b7cb6e3cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>Практическое руководство. Объявление и использование свойств чтения и записи (руководство по программированию на C#)
Свойства имеют все преимущества открытых членов данных, но не связаны с рисками незащищенного, неконтролируемого и несанкционированного доступа к данным объекта. Это достигается благодаря применению *методов доступа*, которые представляют собой особые методы для присвоения и извлечения значений базового члена данных. Метод доступа [set](../../../csharp/language-reference/keywords/set.md) присваивает значения членам данных, а метод доступа [get](../../../csharp/language-reference/keywords/get.md) извлекает их.  
  
 Это можно продемонстрировать на примере класса `Person`, который содержит два свойства: `Name` (string) и `Age` (int). Для обоих свойств реализованы методы доступа `get` и `set`, благодаря чему они доступны и для чтения, и для записи.  
  
## <a name="example"></a>Пример  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 В предыдущем примере свойства `Name` и `Age` являются [открытыми](../../../csharp/language-reference/keywords/public.md) и содержат одновременно методы доступа `get` и `set`. Благодаря этому объект может считывать эти свойства и записывать их. Тем не менее в некоторых случаях необходимо исключить один из методов доступа. Например, свойство без метода доступа `set` будет доступно только для чтения:  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 Кроме того, можно сделать один метод доступа открытым, а другой оставить частным или защищенным. Дополнительные сведения см. в разделе [Асимметричные методы доступа](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
 После объявления свойств их можно использовать так же, как поля класса. Это позволяет получить естественный синтаксис извлечения и установки значения свойства, как показано на примере следующих операторов:  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 Обратите внимание, что в методе `set` свойства доступна специальная переменная `value`. Она содержит значение, заданное пользователем, например:  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 Обратите внимание на простой синтаксис приращения свойства `Age` для объекта `Person`:  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 Если для моделирования свойств использовать отдельные методы `set` и `get`, аналогичный код может иметь следующий вид:  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 В этом примере переопределяется метод `ToString`:  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 Обратите внимание, что метод `ToString` не используется в этой программе явно. Он вызывается по умолчанию при вызове `WriteLine`.  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Свойства](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Классы и структуры](../../../csharp/programming-guide/classes-and-structs/index.md)
