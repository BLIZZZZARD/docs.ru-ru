---
title: "Marshaling Classes, Structures, and Unions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "data marshaling, classes"
  - "marshaling, unions"
  - "marshaling, structures"
  - "marshaling, samples"
  - "data marshaling, structures"
  - "platform invoke, marshaling data"
  - "marshaling, classes"
  - "data marshaling, unions"
  - "data marshaling, samples"
  - "data marshaling, platform invoke"
  - "marshaling, platform invoke"
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Marshaling Classes, Structures, and Unions
Классы и структуры в .NET Framework похожи.  И те и другие могут иметь поля, свойства и события.  Они также могут иметь статические и нестатические методы.  Примечательным отличием является то, что структуры являются типами значений, а классы — ссылочными типами.  
  
 В таблице ниже представлены варианты маршалинга классов, структур и объединений, описывается их применение и приводятся ссылки на соответствующие примеры вызова неуправляемого кода.  
  
|Тип|Описание|Пример|  
|---------|--------------|------------|  
|Класс по значению.|Передает класс с целочисленными членами в качестве параметра In или Out \(как и в случае управляемого класса\).|Пример SysTime|  
|Структура по значению.|Передает структуры в качестве параметров In.|Пример структур|  
|Структура по ссылке.|Передает структуры в качестве параметров In и Out.|Пример OSInfo|  
|Структура с вложенными структурами \(выровненная\).|Передает класс, представляющий структуру с вложенными структурами, в неуправляемую функцию.  Структура выравнивается в одну большую структуру в управляемом прототипе.|Пример FindFile|  
|Структура с указателем на другую структуру.|Передает структуру, содержащую указатель на другую структуру в качестве члена.|Пример структур|  
|Массив структур с целочисленными значениями по значению.|Передает массив структур, содержащих только целые числа, в виде параметра In или Out.  Элементы массива можно изменять.|Примеры использования массивов|  
|Массив структур с целочисленными значениями и строками по ссылке.|Передает массив структур, содержащих целые числа и строки, в качестве параметра Out.  Вызываемая функция выделяет память под массив.|Пример OutArrayOfStructs|  
|Объединения с типами значений.|Передает объединения с типами значений \(целочисленными и двойной точности\).|Пример Unions|  
|Объединения со смешанными типами.|Передает объединения со смешанными типами \(целое число и строка\).|Пример Unions|  
|Значения Null в структуре.|Передает пустую ссылку \(**Nothing** в Visual Basic\) вместо ссылки на тип значения.|Пример HandleRef|  
  
## Пример структур  
 В этом примере показан способ передачи структуры, указывающей на вторую структуру, передачи структуры с внедренной структурой и передачи структуры с внедренным массивом.  
  
 В примере используются следующие неуправляемые функции, показанные с исходными объявлениями:  
  
-   функция **TestStructInStruct**, экспортированная из PinvokeLib.dll;  
  
    ```  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
-   функция **TestStructInStruct3**, экспортированная из PinvokeLib.dll;  
  
    ```  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
-   функция **TestArrayInStruct**, экспортированная из PinvokeLib.dll.  
  
    ```  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/ru-ru/5d1438d7-9946-489d-8ede-6c694a08f614) — это пользовательская неуправляемая библиотека, которая содержит реализации перечисленных выше функций и четыре структуры: **MYPERSON**, **MYPERSON2**, **MYPERSON3** и **MYARRAYSTRUCT**.  Эти структуры содержат следующие элементы:  
  
```  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON, *LP_MYPERSON;  
  
typedef struct _MYPERSON2  
{  
   MYPERSON* person;  
   int age;   
} MYPERSON2, *LP_MYPERSON2;  
  
typedef struct _MYPERSON3  
{  
   MYPERSON person;  
   int age;   
} MYPERSON3;  
  
typedef struct _MYARRAYSTRUCT  
{  
   bool flag;  
   int vals[ 3 ];   
} MYARRAYSTRUCT;  
```  
  
 Управляемые структуры `MyPerson`,  `MyPerson2`, `MyPerson3` и `MyArrayStruct` имеют указанные ниже характеристики.  
  
-   Структура `MyPerson` содержит только члены\-строки.  При передаче строк в неуправляемую функцию в поле [CharSet](../../../docs/framework/interop/specifying-a-character-set.md) для них задается формат ANSI.  
  
-   Структура `MyPerson2` содержит указатель **IntPtr** на структуру `MyPerson`.  Тип **IntPtr** заменяет исходный указатель на неуправляемую структуру, так как приложения .NET Framework не используют указатели, если код не помечен как **небезопасный**.  
  
-   Структура `MyPerson3` содержит структуру `MyPerson` в качестве внедренной.  Внедренную структуру можно выровнять путем помещения ее элементов прямо в основную структуру, или ее можно оставить внедренной, как показано в примере.  
  
-   Структура `MyArrayStruct` содержит массив целочисленных значений.  Атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> задает для перечисления <xref:System.Runtime.InteropServices.UnmanagedType> значение **ByValArray**, которое используется для указания количества элементов в массиве.  
  
 Для всех структур в этом примере применяется атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute>, гарантирующий последовательное размещение элементов в памяти в порядке их появления.  
  
 Класс `LibWrap` содержит управляемые прототипы методов `TestStructInStruct`, `TestStructInStruct3` и `TestArrayInStruct`, вызываемые классом `App`.  Каждый прототип объявляет один параметр указанным ниже способом.  
  
-   `TestStructInStruct` объявляет в качестве своего параметра ссылку на тип `MyPerson2`.  
  
-   `TestStructInStruct3` в качестве своего параметра объявляет тип `MyPerson3` и передает параметр по значению.  
  
-   `TestArrayInStruct` объявляет в качестве своего параметра ссылку на тип `MyArrayStruct`.  
  
 Если параметр не содержит ключевого слова **ref** \(**ByRef** в Visual Basic\), структуры, выступающие в роли аргументов методов, передаются по значению.  Например, метод `TestStructInStruct` передает в неуправляемый код ссылку \(значение адреса\) на объект типа `MyPerson2`.  Для работы со структурой, на которую указывает `MyPerson2`, в примере с помощью методов <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=fullName> и <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> создается буфер заданного размера и возвращается его адрес.  Далее в неуправляемый буфер копируется содержимое управляемой структуры.  Наконец, используются метод <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=fullName> для маршалинга данных из неуправляемого буфера в управляемый объект и метод <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=fullName> для освобождения неуправляемого блока памяти.  
  
### Объявление прототипов  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### Вызов функций  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## Пример FindFile  
 В этом примере показан способ передачи структуры, содержащей другую, внедренную структуру, в неуправляемую функцию.  Также показано, как с помощью атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute> объявить массив фиксированной длины внутри структуры.  В этом примере элементы внедренной структуры добавляются в родительскую структуру.  Пример внедренной структуры \(не выровненной\) см. в разделе [Пример структур](http://msdn.microsoft.com/ru-ru/96a62265-dcf9-4608-bc0a-1f762ab9f48e).  
  
 В примере FindFile используются следующие неуправляемые функции, показанные с исходными объявлениями:  
  
-   функция **FindFirstFile**, экспортированная из Kernel32.dll.  
  
    ```  
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 Исходная структура, переданная в функцию, содержит следующие элементы:  
  
```  
typedef struct _WIN32_FIND_DATA   
{  
  DWORD    dwFileAttributes;   
  FILETIME ftCreationTime;   
  FILETIME ftLastAccessTime;   
  FILETIME ftLastWriteTime;   
  DWORD    nFileSizeHigh;   
  DWORD    nFileSizeLow;   
  DWORD    dwReserved0;   
  DWORD    dwReserved1;   
  TCHAR    cFileName[ MAX_PATH ];   
  TCHAR    cAlternateFileName[ 14 ];   
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;  
```  
  
 В этом примере класс `FindData` содержит члены данных, соответствующие каждому элементу исходной и внедренной структур.  Вместо двух исходных символьных буферов класс подставляет строки.  Атрибут **MarshalAsAttribute** задает для перечисления <xref:System.Runtime.InteropServices.UnmanagedType> значение **ByValTStr**, которое используется для идентификации встроенных символьных массивов фиксированной длины внутри неуправляемых структур.  
  
 Класс `LibWrap` содержит управляемый прототип метода `FindFirstFile`, передающий класс `FindData` в качестве параметра.  Этот параметр должен быть объявлен с атрибутами <xref:System.Runtime.InteropServices.InAttribute> и <xref:System.Runtime.InteropServices.OutAttribute>, так как классы, являющиеся ссылочными типами, по умолчанию передаются как параметры In.  
  
### Объявление прототипов  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### Вызов функций  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## Пример Unions  
 В этом примере показан способ передачи структур, содержащих только типы значений, а также структур, содержащих тип значения и строку, в качестве параметров в неуправляемую функцию, ожидающую объединения.  Объединение представляет собой ячейку памяти, которая может совместно использоваться двумя и более переменными.  
  
 В примере используются следующие неуправляемые функции, показанные с исходными объявлениями:  
  
-   функция **TestUnion**, экспортированная из PinvokeLib.dll.  
  
    ```  
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/ru-ru/5d1438d7-9946-489d-8ede-6c694a08f614) — это пользовательская неуправляемая библиотека, содержащая реализацию указанной выше функции и два объединения: **MYUNION** и **MYUNION2**.  Объединение содержит следующие элементы:  
  
```  
union MYUNION  
{  
    int number;  
    double d;  
}  
  
union MYUNION2  
{  
    int i;  
    char str[128];  
};  
```  
  
 В управляемом коде объединения определяются как структуры.  Структура `MyUnion` в качестве своих членов содержит два типа значений: целочисленный и число двойной точности.  Для управления точным положением каждого члена данных задается атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute>.  Атрибут <xref:System.Runtime.InteropServices.FieldOffsetAttribute> предоставляет физическое положение полей внутри неуправляемого представления объединения.  Обратите внимание, что значения смещения у обоих членов одинаковы, что позволяет членам определять один и тот же участок памяти.  
  
 Объединения `MyUnion2_1` и `MyUnion2_2` содержат тип значения \(целое число\) и строку соответственно.  В управляемом коде типы значений и ссылочные типы не могут перекрываться.  Чтобы при вызове одной и той же неуправляемой функции вызывающий объект мог использовать оба типа, в этом примере применяется перегрузка метода.  Структура `MyUnion2_1` задана явным образом и имеет точное значение смещения.  Напротив, `MyUnion2_2` имеет последовательную структуру, так как структуры, заданные явным образом, нельзя использовать со ссылочными типами.  Атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> задает для перечисления <xref:System.Runtime.InteropServices.UnmanagedType> значение **ByValTStr**, которое используется для идентификации встроенных символьных массивов фиксированной длины, появляющихся в неуправляемом представлении объединения.  
  
 Класс `LibWrap` содержит прототипы для методов `TestUnion` и `TestUnion2`.  `TestUnion2` перегружается для объявления `MyUnion2_1` или `MyUnion2_2` в качестве параметров.  
  
### Объявление прототипов  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### Вызов функций  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## Пример SysTime  
 В этом примере показано, как передать указатель на класс в неуправляемую функцию, ожидающую указатель на структуру.  
  
 В примере используется следующая неуправляемая функция, показанная с исходным объявлением:  
  
-   функция **GetSystemTime**, экспортированная из Kernel32.dll.  
  
    ```  
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 Исходная структура, переданная в функцию, содержит следующие элементы:  
  
```  
typedef struct _SYSTEMTIME {   
    WORD wYear;   
    WORD wMonth;   
    WORD wDayOfWeek;   
    WORD wDay;   
    WORD wHour;   
    WORD wMinute;   
    WORD wSecond;   
    WORD wMilliseconds;   
} SYSTEMTIME, *PSYSTEMTIME;  
```  
  
 В этом примере класс `SystemTime` содержит элементы исходной структуры, представленные в виде членов класса.  Чтобы гарантировать последовательное размещение членов в памяти в порядке их появления, применяется атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute>.  
  
 Класс `LibWrap` содержит управляемый прототип метода `GetSystemTime`, который по умолчанию передает класс `SystemTime` в качестве параметра In или Out.  Этот параметр должен быть объявлен с атрибутами <xref:System.Runtime.InteropServices.InAttribute> и <xref:System.Runtime.InteropServices.OutAttribute>, так как классы, являющиеся ссылочными типами, по умолчанию передаются как параметры In.  Чтобы вызывающий объект получал результаты, необходимо явным образом применить [атрибуты направления](http://msdn.microsoft.com/ru-ru/241ac5b5-928e-4969-8f58-1dbc048f9ea2).  Класс `App` создает экземпляр класса `SystemTime` и осуществляет доступ к его полям данных.  
  
### Примеры кода  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## Пример OutArrayOfStructs  
 В этом примере показано, как передать в неуправляемую функцию массив структур, содержащий целочисленные значения и строки, в виде параметров Out.  
  
 В этом примере демонстрируется, как вызывать собственную функцию с помощью класса <xref:System.Runtime.InteropServices.Marshal> и небезопасного кода.  
  
 В примере используются функции\-оболочки и вызовы неуправляемого кода, определенные в библиотеке [PinvokeLib.dll](http://msdn.microsoft.com/ru-ru/5d1438d7-9946-489d-8ede-6c694a08f614) и содержащиеся в исходных файлах.  В нем используется функция `TestOutArrayOfStructs` и структура `MYSTRSTRUCT2`.  Структура содержит следующие элементы:  
  
```  
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 Класс `MyStruct` содержит строковый объект из символов ANSI.  Поле <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> определяет формат ANSI.  `MyUnsafeStruct` — это структура, содержащая тип <xref:System.IntPtr> вместо строки.  
  
 Класс `LibWrap` содержит перегруженный метод прототипа `TestOutArrayOfStructs`.  Если в качестве параметра метод объявляет указатель, класс должен быть помечен зарезервированным словом `unsafe`.  Так как в [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] нельзя использовать небезопасный код, перегруженный метод, модификатор unsafe и структура `MyUnsafeStruct` оказываются ненужными.  
  
 Класс `App` реализует метод `UsingMarshaling`, который выполняет все задачи, необходимые для передачи массива.  Чтобы указать, что данные передаются от вызываемого объекта к вызывающему, массив помечается зарезервированным словом `out` \(`ByRef` в Visual Basic\).  Реализация использует следующие методы класса <xref:System.Runtime.InteropServices.Marshal>:  
  
-   метод <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> для маршалинга данных из неуправляемого буфера в управляемый объект;  
  
-   метод <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> для освобождения памяти, зарезервированной для строк структуры;  
  
-   метод <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> для освобождения памяти, зарезервированной для массива.  
  
 Как упоминалось выше, в C\# разрешено использовать небезопасный код, а в [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] — нет.  В примере кода C\# `UsingUnsafePointer` является альтернативной реализацией метода, в которой для обратной передачи массива, содержащего структуру `MyUnsafeStruct`, вместо класса <xref:System.Runtime.InteropServices.Marshal> используются указатели.  
  
### Объявление прототипов  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### Вызов функций  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## См. также  
 [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/ru-ru/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [Marshaling Strings](../../../docs/framework/interop/marshaling-strings.md)   
 [Marshaling Arrays of Types](http://msdn.microsoft.com/ru-ru/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)