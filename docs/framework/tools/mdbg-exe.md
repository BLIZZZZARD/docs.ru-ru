---
title: "MDbg.exe (отладчик командной строки для .NET Framework) | Документы Майкрософт"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
caps.latest.revision: 27
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 99cf844513e7264d9542cd3502613b5e2b90da76
ms.contentlocale: ru-ru
ms.lasthandoff: 06/02/2017

---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (отладчик командной строки для .NET Framework)
Отладчик командной строки для платформы NET Framework помогает разработчикам программ и приложений в поиске и исправлении ошибок в программах, работающих в среде CLR платформы .NET Framework. Этот инструмент использует отладочный API-интерфейс среды выполнения. Программа MDbg.exe может использоваться только для отладки управляемого кода, отладка неуправляемого кода не поддерживается.  
  
 Это средство можно получить с помощью NuGet. Сведения по установке см. в разделе [MDbg 0.1.0](http://www.nuget.org/packages/MDbg/0.1.0). Для запуска средства используйте консоль диспетчера пакетов. Дополнительные сведения том, как использовать консоль диспетчера пакетов, см. в разделе [Использование консоли диспетчера пакетов](http://docs.nuget.org/docs/start-here/Using-the-Package-Manager-Console).  
  
 В командной строке диспетчера пакетов введите следующее:  
  
## <a name="syntax"></a>Синтаксис  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Команды  
 Открыв отладчик (как указано в командной строке **mdbg>**), введите одну из команд, описанных в следующем разделе.  
  
 **команда** [*аргументы*]  
  
 Команды MDbg.exe вводятся с учетом регистра.  
  
|Команда|Описание|  
|-------------|-----------------|  
|**ap**[**rocess**] [*number*]|Переключается на другой отлаживаемый процесс или распечатывает доступные процессы. Числа являются не реальными идентификаторами процесса (PID), а номерами в списке с индексом, начинающимся с нуля.|  
|**a**[**ttach**] [*pid*]|Присоединяется к процессу или распечатывает доступные процессы.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo*]|Устанавливает точку останова в указанном методе. Модули сканируются последовательно.<br /><br /> -   **break** *FileName:LineNo* устанавливает точку останова в требуемом месте в источнике.<br />-   **break** *~number* устанавливает точку останова на символе, ранее отображенном с помощью команды **x**.<br />-   **break** *module!ClassName.Method+IlOffset* устанавливает точку останова в полностью определенном месте.|  
|**block**[**ingObjects**]|Отображает блокировки монитора, которые блокируют потоки.|  
|**ca**[**tch**] [*exceptionType*]|Вызывает останов отладчика при любых исключениях, а не только в случае необработанных исключений.|  
|**cl**[**earException**]|Отмечает текущее исключение как обработанное, чтобы можно было продолжить выполнение. Если не устранить причину исключения, оно может возникнуть повторно.|  
|**conf**[**ig**] [*option value*]|Отображает все настраиваемые параметры и способ вызова параметров без необязательных значений. Если параметр указан, задает `value` как текущий параметр. В настоящее время доступны следующие параметры.<br /><br /> -   `extpath` задает путь, по которому выполняется поиск расширений при использовании команды `load`.<br />-   `extpath+` добавляет путь для загрузки расширений.|  
|**del**[**ete**]|Удаляет точку останова.|  
|**de**[**tach**]|Отсоединяется от отлаживаемого процесса.|  
|**d**[**own**] [*frames*]|Перемещает активный кадр стека вниз.|  
|**echo**|Выводит сообщение на консоль.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Включает (1) или отключает (0) пользовательские уведомления для указанного типа.|  
|**ex**[**it**] [*код_завершения*]|Выполняет выход из оболочки MDbg.exe и при необходимости указывает код завершения процесса.|  
|**fo**[**reach**] [*OtherCommand*]|Выполняет команду во всех потоках. *OtherCommand* — это допустимая команда, работающая в одном потоке; **foreach** *OtherCommand* выполняет эту же команду во всех потоках.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*args ...* ]|Выполняет вычисление функции в текущем активном потоке, где вычисляемая функция — *functionName*. Имя функции должно быть полным, включая пространства имен.<br /><br /> Параметр `-ad` определяет домен приложения, который должен использоваться для разрешения функции. Если параметр `-ad` не указан, домен приложения для разрешения по умолчанию устанавливается в домен приложения, в котором расположен поток, используемый для вычисления функции.<br /><br /> Если вычисляемая функция не статическая, первый передаваемый параметр должен быть указателем `this`. Поиск аргументов для вычисления функции выполняется во всех доменах приложения.<br /><br /> Чтобы запросить значение из домена приложения, установите префикс переменной с модулем и именем домена приложения; например, `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. При выполнении этой команды вычисляется функция `System.Object.ToString` в домене приложения `0`. Поскольку метод `ToString` является функцией экземпляра, первым параметром должен быть указатель `this`.|  
|**g**[**o**]|Программа продолжается, пока не будет обнаружена точка останова, не произойдет выход из программы, или какое-либо событие (например, необработанное исключение) не приведет к останову программы.|  
|**h**[**elp**] [*command*]<br /><br /> -или-<br /><br /> **?** [*command*]|Отображает описание всех команд или подробное описание указанной команды.|  
|**ig**[**nore**] [*event*]|Вызывает останов отладчика только при обнаружении необработанных исключений.|  
|**int**[**ercept**] *FrameNumber*|Возвращает отладчик к указанному номеру кадра.<br /><br /> Если отладчик обнаруживает исключение, с помощью этой команды можно вернуть отладчик к указанному номеру кадра. Можно изменить состояние программы с помощью команды **set** и продолжить выполнение с помощью команды **go**.|  
|**k**[**ill**]|Останавливает активный процесс.|  
|**l**[**ist**] [*modules* &#124; *appdomains* &#124; *assemblies*]|Отображает загруженные модули, домены приложений или сборки.|  
|**lo**[**ad**] *assemblyName*|Загружает расширение следующим образом: загружается указанная сборка и выполняется попытка запустить статический метод `LoadExtension` из типа `Microsoft.Tools.Mdbg.Extension.Extension`.|  
|**log** [*eventType*]|Задает или отображает события, которые вносятся в журнал.|  
|**mo**[**de**] [*option on/off*]|Задает различные параметры отладчика. Используйте команду `mode` без параметров, чтобы получить список режимов отладки и их текущих параметров.|  
|**mon**[**itorInfo**] *monitorReference*|Отображает сведения о блокировке монитора объекта.|  
|**newo**[**bj**] *typeName* [*arguments...*]|Создает объект типа *typeName*.|  
|**n**[**ext**]|Запускает код и переходит к следующей строке (даже если следующая строка содержит несколько вызовов функций).|  
|**Opendump** *pathToDumpFile*|Открывает указанный файл дампа для отладки.|  
|**o**[**ut**]|Перемещается в конец текущей функции.|  
|**pa**[**th**] [*pathName*]|Выполняет поиск указанного пути для исходных файлов, если расположение в двоичных файлах недоступно.|  
|**p**[**rint**] [*var*] &#124; [`-d`]|Распечатывает все переменные в области (**print**), распечатывает определенную переменную (**print** *var*) либо распечатывает переменные отладчика (**print**`-d`).|  
|**printe**[**xception**] [*-r*]|Распечатывает последнее исключение в текущем потоке. Используйте параметр `–r` (рекурсивного) для просмотра свойства `InnerException` в объекте исключения, чтобы получить сведения обо всей цепочке исключений.|  
|**pro**[**cessenum**]|Отображает активные процессы.|  
|**q**[**uit**] [*exitcode*]|Выходит из оболочки MDbg.exe, по выбору указывая код завершения процесса.|  
|**re**[**sume**] [`*` &#124; [`~`]*threadNumber*]|Возобновляет текущий поток или поток, указанный параметром *threadNumber*.<br /><br /> Если параметр *threadNumber* указан как `*` или если номер потока начинается с `~`команда относится ко всем потокам, кроме потока, указанного параметром *threadNumber*.<br /><br /> Возобновление неприостановленного потока не имеет никакого результата.|  
|**r**[**un**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124;`-enc`] [[*path_to_exe*] [*args_to_exe*]]|Останавливает текущий процесс (если есть) и начинает новый процесс. Если не передан аргумент исполняемого файла, эта команда запускает программу, которая ранее запускалась командой `run`. Если аргумент исполняемого файла передан, указанная программа будет запущена с указанными дополнительными аргументами.<br /><br /> Если события загрузки классов и модулей и запуска потоков игнорируются (как это делается по умолчанию), программа будет остановлена на первой исполняемой инструкции основного потока.<br /><br /> Можно принудительно установить отладчик в режим JIT-компиляции кода с помощью любого из трех флагов.<br /><br /> -   `-d` *(* `ebug` *)* отключает оптимизацию. Это значение по умолчанию для MDbg.exe.<br />-   `-o` *(* `ptimize` *)* принудительно включает режим работы кода, более похожий на работу вне отладчика, но несколько осложняющий отладку. Это вариант по умолчанию для использования вне отладчика.<br />-   `-enc` активирует функцию "Изменить и продолжить", но снижает производительность.|  
|**Set** *variable*=*value*|Изменяет значение любой переменной в области.<br /><br /> Также можно создать собственные переменные отладчика и присвоить им значения ссылки из самого приложения. Эти значения действуют как дескрипторы для исходного значения, даже если исходное значение находится вне области. Все переменные отладчика должны начинаться с `$` (например, `$var`). Очистите эти дескрипторы, не задавая для них значение с помощью следующей команды.<br /><br /> `set $var=`|  
|**Setip** [`-il`] *number*|Ставит указатель текущей инструкции (IP) в файле на указанную позицию. Если указывается параметр `-il`, число представляет смещение языка CIL в методе. В противном случае число представляет номер строки источника.|  
|**sh**[**ow**] [*lines*]|Задает число отображаемых строк.|  
|**s**[**tep**]|Переносит выполнение в следующую функцию в текущей строке либо переходит в следующую строку, если нет функции для перехода.|  
|**su**[**spend**] [\* &#124; [~]*threadNumber*]|Приостанавливает выполнение текущего потока или потока, заданного параметром *threadNumber*.  Если значение *threadNumber* задано как `*`, команда относится ко всем потокам. Если номер потока начинается с `~`, команда относится ко всем потокам, кроме потока, указанного параметром *threadNumber*. Приостановленные потоки исключаются из выполнения при запуске процесса командой **go** или **step**. Если в процессе нет неприостановленных потоков и выполняется команда **go**, процесс не будет продолжен. В этом случае нажмите сочетание клавиш CTRL+C, чтобы войти в процесс.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Задает одну из следующих команд.<br /><br /> -   `symbol path` [`"``value``"`] — отображает или задает текущий путь к символам.<br />-   `symbol addpath` `"` `value` `"` — добавляет к текущему пути к символам.<br />-   `symbol reload` [`"``module``"`] — перезагружает либо все символы, либо символы для указанного модуля.<br />-   `symbol list` [`module`] — отображает текущие загруженные символы либо для всех модулей, либо для указанного модуля.|  
|**t**[**hread**] [*newThread*] [-*nick nickname*`]`|При выполнении команды потока без параметров отображаются все управляемые потоки текущего процесса. Потоки обычно обозначаются номерами потоков. Однако если потоку присвоен псевдоним, вместо номера отображается псевдоним. Потоку присваивается псевдоним с помощью параметра `-nick`.<br /><br /> -   **thread** `-nick` *threadName* присваивает псевдоним выполняемому в настоящее время потоку.<br /><br /> Псевдонимы не могут быть числами. Если в текущем потоке уже есть назначенный псевдоним, старый псевдоним заменяется на новый. Если новый псевдоним — пустая строка (""), псевдоним текущего потока удаляется и потоку назначается новый псевдоним.|  
|**u**[**p**]|Перемещает активный кадр стека вверх.|  
|**uwgc**[**handle**] [*var*] &#124; [*address*]|Распечатывает переменную, отслеживаемую дескриптором. Для указания дескриптора можно использовать имя или адрес.|  
|**when**|Отображает активные в данный момент операторы `when`.<br /><br /> **when** **delete all** &#124; `num` [`num` [`num` …]] — удаляет оператор `when` с указанным номером или все операторы `when`, если указано `all`.<br /><br /> **when** `stopReason` [`specific_condition`] **do**`cmd` [`cmd` [`cmd` …] ] — параметр *stopReason* может иметь одно из следующих значений.<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> Параметр *specific_condition* может иметь одно из следующих значений.<br /><br /> -   *number* — инициирует действие для `ThreadCreated` и `BreakpointHit` только при остановке по идентификатору потока или номеру точки останова с тем же значением.<br />[`!`]*name* — инициирует действие для `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown` и `UnhandledExceptionThrown`, только если имя соответствует имени *stopReason*.<br /><br /> Параметр *specific_condition* должен быть пустым для других значений *stopReason*.|  
|**w**[**here**] [`-v`] [`-c` *depth*] [*threadID*]|Отображает отладочную информацию о кадрах стека.<br /><br /> Параметр `-v` предоставляет подробную информацию о каждом отображаемом кадре стека.<br />Числовое значение для `depth` ограничивает количество отображаемых кадров. С помощью команды **all** можно вывести все кадры. Значение по умолчанию — 100.<br />Если указать параметр *threadID*, можно определить, какой поток связан со стеком. Значение по умолчанию — только текущий поток. С помощью команды **all** можно получить все потоки.|  
|**x** [`-c`*numSymbols*] [*module*[`!`*pattern*]]|Отображает функции, соответствующие параметру `pattern` для модуля.<br /><br /> Если указан параметр *numSymbols*, выводится только указанный номер. Если для *pattern* не указано значение `!` (обозначающее регулярное выражение), отображаются все функции. Если значение для *module* не указано, отображаются все загруженные модули. Символы (*~#*) могут использоваться для установки точек останова с помощью команды **break**.|  
  
## <a name="remarks"></a>Примечания  
 Скомпилируйте приложение для отладки, используя относящиеся к компилятору флаги, с помощью которых компилятор создаст символы отладки. Дополнительные сведения об этих флагах см. в документации по компилятору. Отладка оптимизированных приложений возможна, но часть отладочной информации будет недоступна. Например, многие локальные переменные будут недоступны, а строки исходного кода будут неточны.  
  
 После компиляции приложения введите в командной строке команду **mdbg**, чтобы начать сеанс отладчика (см. следующий пример).  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 Сообщение `mdbg>` означает, что идет работа с отладчиком.  
  
 После входа в отладчик используйте команды и аргументы, описанные в предыдущем разделе.  
  
## <a name="examples"></a>Примеры  
  
## <a name="see-also"></a>См. также  
 [Инструменты](../../../docs/framework/tools/index.md)   
 [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md)