---
title: "Буферы фиксированного размера (Руководство по программированию на C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Буферы фиксированного размера (Руководство по программированию на C#)
В языке C# для создания буфера с массивом фиксированного размера в структуре данных можно использовать оператор [fixed](../../../csharp/language-reference/keywords/fixed-statement.md). Это полезно при работе с существующим кодом, например с кодом, написанным на других языках, ранее созданными библиотеками DLL или проектами COM. Фиксированный массив может принимать любые атрибуты или модификаторы, допустимые для обычных членов структуры. Единственным ограничением является то, что массив должен иметь тип `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` или `double`.  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>Примечания  
 В предыдущих версиях языка C# объявление структуры фиксированного размера в стиле C++ было затруднительным, так как структура C# с массивом не содержит элементов массива. Вместо этого в ней присутствуют ссылки на элементы.  
  
 В языке C# версии 2.0 появилась возможность внедрения массива фиксированного размера в [структуру](../../../csharp/language-reference/keywords/struct.md), если он используется в блоке [небезопасного](../../../csharp/language-reference/keywords/unsafe.md) кода.  
  
 Например, в версиях языка C# до версии 2.0 размер следующего ключевого слова `struct` будет равен 8 байтам. Массив `pathName` является ссылкой на массив с выделением в куче.  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 Начиная с версии C# 2.0 `struct` может содержать внедренный массив. В приведенном ниже примере массив `fixedBuffer` имеет фиксированный размер. Для доступа к элементам такого массива используется оператор `fixed`, устанавливающий указатель на первый элемент. Оператор `fixed` закрепляет экземпляр `fixedBuffer` в определенном месте в памяти.  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 Размер массива из 128 элементов `char` составляет 256 байт. В буферах типа [char](../../../csharp/language-reference/keywords/char.md) фиксированного размера на один символ всегда приходится два байта независимо от кодировки. Это справедливо даже в том случае, когда буферы char маршалируются в методы API или структуры с `CharSet = CharSet.Auto` или `CharSet = CharSet.Ansi`. Для получения дополнительной информации см. <xref:System.Runtime.InteropServices.CharSet>.  
  
 Еще одним распространенным массивом фиксированного размера является массив [bool](../../../csharp/language-reference/keywords/bool.md). Элементы в массиве `bool` всегда имеют размер в один байт. Массивы `bool` не подходят для создания битовых массивов или буферов.  
  
> [!NOTE]
>  За исключением памяти, созданной с помощью [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), компилятор C# и среда CLR не выполняют проверку переполнения буфера безопасности. Как и при работе с любым небезопасным кодом, следует проявлять осторожность.  
  
 Небезопасные буферы отличаются от обычных массивов указанными ниже особенностями.  
  
-   Небезопасные буферы можно использовать в небезопасном контексте.  
  
-   Небезопасные буферы — это всегда векторы или одномерные массивы.  
  
-   В объявлении массива всегда должен присутствовать счетчик, такой как `char id[8]`. При этом `char id[]` нельзя использовать.  
  
-   Небезопасные буферы могут быть только полями экземпляров структур в небезопасном контексте.  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Небезопасный код и указатели](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Оператор fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Взаимодействие](../../../csharp/programming-guide/interop/index.md)
