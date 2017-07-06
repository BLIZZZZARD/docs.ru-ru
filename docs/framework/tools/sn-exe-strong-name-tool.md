---
title: "Sn.exe (средство строгих имен) | Документы Майкрософт"
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
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
caps.latest.revision: 44
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 18a8df92bac23e417cc1b78fdb8099413d284baa
ms.contentlocale: ru-ru
ms.lasthandoff: 06/02/2017

---
# <a name="snexe-strong-name-tool"></a>Sn.exe (средство строгих имен)
Программа строгих имен (Sn.exe) позволяет подписывать сборки [строгими именами](../../../docs/framework/app-domains/strong-named-assemblies.md). Программа Sn.exe предусматривает параметры для управления ключами, создания подписи и ее проверки.  
  
 Дополнительные сведения о строгом именовании и сборках со строгими именами см. в разделах [Сборки со строгими именами](../../../docs/framework/app-domains/strong-named-assemblies.md) и [Практическое руководство. Подписание сборки строгим именем](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Программа строгих имен автоматически устанавливается вместе с Visual Studio. Программу можно запустить из командной строки разработчика (или из командной строки Visual Studio в Windows 7). Дополнительные сведения см. в разделе [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  На 64-разрядных компьютерах можно запустить 32-разрядную версию программы Sn.exe через командную строку Visual Studio и 64-разрядную версию через командную строку Visual Studio x64 Win64.  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Создает данные <xref:System.Reflection.AssemblySignatureKeyAttribute> для переноса из файла ключа удостоверения в ключ подписи.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Создает данные <xref:System.Reflection.AssemblySignatureKeyAttribute> для переноса из контейнера ключей ключа удостоверения в ключ подписи.|  
|**-c** [*csp*]|Задается поставщик служб шифрования (CSP), используемый по умолчанию для подписывания строгим именем. Этот параметр применяется к компьютеру в целом. Если имя поставщика служб шифрования не задано, программа Sn.exe удалит текущее значение.|  
|**-d** *container*|Удаляет указанный контейнер ключей из поставщика служб шифрования со строгими именами.|  
|**-D**  *assembly1 assembly2*|Проверяет, что две сборки отличаются только подписью. Данный подход часто используется как средство проверки после того, как сборка была повторно подписана с помощью другой пары ключей.|  
|**-e**  *assembly outfile*|Извлекает открытый ключ из сборки *assembly* и записывает его в файл *outfile*.|  
|**-h**|Отображает синтаксис команд и параметров программы.|  
|**-i** *infile container*|Устанавливает в указанный контейнер ключей пару ключей из файла *infile*. Контейнер ключей располагается в поставщике служб шифрования со строгими именами.|  
|**-k** [*keysize*] *outfile*|Создает новый ключ <xref:System.Security.Cryptography.RSACryptoServiceProvider> указанного размера и записывает его в указанный файл.  В файл записываются и открытый, и закрытый ключи.<br /><br /> Если размер ключа не задан, по умолчанию создается 1024-разрядный ключ при условии, что установлен усовершенствованный поставщик служб шифрования (Microsoft); в противном случае создается 512-разрядный ключ.<br /><br /> Параметр *keysize* поддерживает ключи длиной от 384 до 16 384 бит с приращениями по 8 бит, если установлен усовершенствованный поставщик служб шифрования (Майкрософт).  Он поддерживает ключи длиной от 384 до 512 бит с приращениями по 8 бит, если установлен базовый поставщик служб шифрования (Microsoft).|  
|**-m** [**y** *|* **n**]|Задает зависимость контейнеров ключей от компьютера или пользователя. Если задано значение *y*, контейнеры ключей зависят от компьютера. Если задано значение *n*, контейнеры ключей зависят от пользователя.<br /><br /> Если не задан ни один из параметров, этот параметр отобразит текущее значение.|  
|**-o**  *infile* [*outfile*]|Извлекает открытый ключ из файла *infile* и сохраняет его в CSV-файле. Байты открытого ключа разделяются запятыми. Этот формат удобно применять для жесткого задания в исходном коде ссылок на ключи в виде инициализированных массивов. Если параметр *outfile* не указан, выходные данные будут помещены в буфер обмена. **Примечание.** Данный параметр не проверяет, содержится ли во входном файле что-либо, помимо открытого ключа. Если `infile` содержит пару ключей, в том числе закрытый ключ, последний также извлекается.|  
|**-p** *infile outfile* [*hashalg*]|Извлекает открытый ключ из пары ключей в файле *infile* и сохраняет его в файле *outfile*, при необходимости используя алгоритм RSA, указанный в параметре *hashalg*. Полученный открытый ключ можно использовать для отложенной подписи сборки с помощью параметров **/delaysign+** и **/keyfile** [компоновщика сборок (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Если применяется отложенная подпись сборки, во время компиляции задается только открытый ключ, а в файле выделяется место для подписи, которая будет добавлена позднее, когда станет известен закрытый ключ.|  
|**-pc**  *container* *outfile* [*hashalg*]|Извлекает открытый ключ из пары ключей, хранящейся в параметре *container*, и записывает его в файл *outfile*. Если указан параметр *hashalg*, для извлечения открытого ключа используется алгоритм RSA.|  
|**-Pb** [**y** *|* **n**]|Указывает, применяется ли политика пропускания строгих имен. Если задан параметр *y*, строгие имена сборок с полным доверием не проверяются при загрузке в объект <xref:System.AppDomain> с полным доверием. Если задан параметр *n*, проверяется правильность строгих имен, но не проверяется их соответствие конкретному строгому имени. Класс <xref:System.Security.Permissions.StrongNameIdentityPermission> не применяется к сборкам с полным доверием. Проверку на соответствие строгих имен необходимо выполнять отдельно.<br /><br /> Если не задан ни один параметр `y` и `n`, отображается текущее значение. Значение по умолчанию — `y`. **Примечание.** На 64-разрядных компьютерах значение этого параметра необходимо задавать и в 32-разрядном, и в 64-разрядном экземплярах программы Sn.exe.|  
|**-q**[**uiet**]|Задает тихий режим и отключает отображение сообщений об успешно выполненных операциях.|  
|**-R**[**a**] *assembly* *infile*|Повторно подписывает ранее подписанную сборку или сборку с отложенной подписью с помощью пары ключей, содержащейся в файле *infile*.<br /><br /> Если указан параметр **-Ra**, для всех файлов в сборке заново вычисляются хэши.|  
|**-Rc**[**a**] *assembly container*|Повторно подписывает ранее подписанную сборку или сборку с отложенной подписью с помощью пары ключей, содержащихся в контейнере *container*.<br /><br /> Если указан параметр **-Rca**, для всех файлов в сборке заново вычисляются хэши.|  
|**-Rh** *assembly*|Повторно вычисляет хэши для всех файлов сборки.|  
|**-t**[**p**] *infile*|Отображает токен открытого ключа, который хранится в файле *infile*. Файл *infile* должен содержать открытый ключ, который был ранее создан из файла пары ключей с использованием параметра **-p**.  Не используйте параметр **-t[p]** для непосредственного извлечения токена из файла пары ключей.<br /><br /> Программа Sn.exe вычисляет токен с помощью функции хэширования открытого ключа. В целях экономии места среда CLR сохраняет токены открытого ключа в манифесте как часть ссылки на другую сборку при записи зависимости от сборки со строгим именем. При указании параметра **-tp** наряду с токеном отображается открытый ключ. Если атрибут <xref:System.Reflection.AssemblySignatureKeyAttribute> был применен к сборке, токен предназначается для ключа удостоверения, и отображаются имя алгоритма хэширования и ключ удостоверения.<br /><br /> Следует иметь в виду, что данный параметр не проверяет подпись сборки, и его не следует использовать для принятия решений о доверии.  Этот параметр лишь отображает необработанные данные токена открытого ключа.|  
|**-T**[**p**] *assembly*|Отображает токен открытого ключа для сборки *assembly*. Параметр *assembly* должен содержать имя файла, который содержит манифест сборки.<br /><br /> Программа Sn.exe вычисляет токен с помощью функции хэширования открытого ключа. В целях экономии места среда выполнения сохраняет токены открытого ключа в манифесте как часть ссылки на другую сборку при записи зависимости от сборки со строгим именем. При указании параметра **-Tp** наряду с токеном отображается открытый ключ. Если атрибут <xref:System.Reflection.AssemblySignatureKeyAttribute> был применен к сборке, токен предназначается для ключа удостоверения, и отображаются имя алгоритма хэширования и ключ удостоверения.<br /><br /> Следует иметь в виду, что данный параметр не проверяет подпись сборки, и его не следует использовать для принятия решений о доверии.  Этот параметр лишь отображает необработанные данные токена открытого ключа.|  
|`-TS` `assembly` `infile`|Выполняет пробное подписание полностью или частично подписанной сборки `assembly` с использованием пары ключей из файла `infile`.|  
|-`TSc``assembly``container`|Выполняет пробное подписание полностью или частично подписанной сборки `assembly` с использованием пары ключей из контейнера ключей `container`.|  
|**-v** *assembly*|Проверяет строгое имя в сборке *assembly*, где *assembly* представляет собой имя файла, содержащего манифест сборки.|  
|**-vf**  *assembly*|Проверяет строгое имя в сборке *assembly*. В отличие от параметра **-v**, при использовании параметра **-vf** проверка производится, даже если она отключена с помощью параметра **-Vr**.|  
|**-Vk**  *regfile.reg* *assembly* [*userlist*] [*infile*]|Создает файл регистрационных записей (файл с расширением REG), который можно использовать для регистрации указанной сборки для пропуска проверки. Правила присвоения имен сборкам, которые применяются к параметру **-Vr**, также применяются к параметру **-Vk**. Дополнительные сведения о параметрах *userlist* и *infile* см. в описании параметра **–Vr**.|  
|**-Vl**|Отображает список текущих параметров проверки строгих имен на данном компьютере.|  
|**-Vr**  *assembly* [*userlist*] [*infile*]|Регистрирует сборку *assembly* для пропуска проверки. При необходимости можно указать разделенный запятыми список имен пользователей, для которых проверка должна пропускаться. Если задан файл *infile*, проверка будет выполняться, но в ней будет использоваться открытый ключ, находящийся в файле *infile*. Параметр *assembly* может быть задан в формате *\*, strongname*, чтобы зарегистрировать все сборки с указанным строгим именем. Для параметра *strongname* должна быть задана строка шестнадцатеричных цифр, представляющих открытый ключ в форме токена. Сведения об отображении токена открытого ключа см. в описании параметров **-t** и **-T**. **Внимание!** Используйте этот параметр только во время разработки. При добавлении сборки в список непроверяемых сборок создается уязвимость в системе безопасности. Вредоносная сборка может использовать полное имя сборки (имя сборки, версия, язык и региональные параметры, маркер открытого ключа), добавленное в список непроверяемых, с целью подделки ее идентификации. Данный подход позволяет вредоносной сборке также избежать проверки.|  
|||  
|**-Vu**  *assembly*|Отменяет регистрацию сборки *assembly* для пропуска проверки. Правила присвоения имен сборкам, которые применяются для параметра **-Vr**, также применяются к параметру **-Vu**.|  
|**-Vx**|Удаляет все записи о пропуске проверки.|  
|**-?**|Отображает синтаксис команд и параметров программы.|  
  
> [!NOTE]
>  Все параметры программы Sn.exe зависят от регистра и должны вводиться в точном соответствии с инструкциями выше, чтобы программа их правильно распознала.  
  
## <a name="remarks"></a>Примечания  
 Параметры **-R** и **–Rc** можно использовать для сборок с отложенной подписью. При этом во время компиляции задается только открытый ключ, а подпись выполняется позднее, когда становится известен закрытый ключ.  
  
> [!NOTE]
>  Для параметров (например, -**Vr)**, которые осуществляют запись в защищенные ресурсы, такие как реестр, программу SN.exe следует запускать от имени администратора.  
  
## <a name="examples"></a>Примеры  
 Следующая команда создает новую пару случайных ключей, которая сохраняется в файле `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Следующая команда сохраняет ключ из файла `keyPair.snk` в контейнере `MyContainer` поставщика служб шифрования со строгими именами.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Следующая команда извлекает открытый ключ из файла `keyPair.snk` и сохраняет его в файле `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Следующая команда отображает открытый ключ и его токен, которые содержатся в файле `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Следующая команда проверяет сборку `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Следующая команда удаляет `MyContainer` из поставщика служб шифрования со строгими именами, используемого по умолчанию.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>См. также  
 [Инструменты](../../../docs/framework/tools/index.md)   
 [Al.exe (компоновщик сборок)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [Сборки со строгими именами](../../../docs/framework/app-domains/strong-named-assemblies.md)   
 [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
