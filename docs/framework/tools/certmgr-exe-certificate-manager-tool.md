---
title: "Certmgr.exe (средство диспетчера сертификатов) | Документы Майкрософт"
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
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: cf9cc6db470d85d765d95a1aba2fd205764ee3b3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/02/2017

---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (средство диспетчера сертификатов)
Диспетчер сертификатов (Certmgr.exe) предназначен для управления сертификатами, списками доверия сертификатов (CTL) и списками отзыва сертификатов (CRL).  
  
 Диспетчер сертификатов устанавливается автоматически вместе с Visual Studio. Для запуска программы используйте [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Диспетчер сертификатов (Certmgr.exe) является служебной программой командной строки, в то время как сертификаты (Certmgr.msc) — это оснастка консоли управления (MMC). Поскольку файл Certmgr.msc обычно находится в системном каталоге Windows, при вводе `certmgr` в командной строке может загрузиться оснастка консоли управления (MMC) "Сертификаты", даже если открыта командная строка Visual Studio. Это происходит потому, что путь к оснастке предшествует пути к диспетчеру сертификатов в переменной среды PATH. При возникновении этой проблемы команды Certmgr.exe можно выполнить, указав путь к исполняемому файлу.  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика (или командной строкой Visual Studio в Windows 7). Дополнительные сведения см. в разделе [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Общие сведения о сертификатах X.509 см. в разделе [Работа с сертификатами](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|*sourceStorename*|Хранилище сертификатов, содержащее существующие сертификаты, списки доверия сертификатов (CTL) и списки отзыва сертификатов (CRL) для добавления, удаления, сохранения или отображения. Это может быть файл хранилища или хранилище систем.|  
|*destinationStorename*|Конечное хранилище сертификатов или файл.|  
  
|Параметр|Описание|  
|------------|-----------------|  
|**/add**|Добавляет сертификаты, CTL и CRL в хранилище сертификатов.|  
|**/all**|Добавляет все записи при использовании параметра **/add**. Удаляет все записи при использовании параметра **/del**. Отображает все записи при использовании без параметров **/add** или **/del**. Параметр **/all** нельзя использовать вместе с параметром **/put**.|  
|**/c**|Добавляет сертификаты при использовании параметра **/add**. Удаляет сертификаты при использовании параметра **/del**. Сохраняет сертификаты при использовании параметра **/put**. Отображает сертификаты при использовании без параметра **/add**, **/del** или **/put**.|  
|**/CRL**|При использовании с параметром **/add** добавляет списки отзыва сертификатов (CRL). При использовании с параметром **/del** удаляет списки отзыва сертификатов (CRL). Сохраняет списки CRL при использовании с параметром **/put**. Отображает списки отзыва сертификатов (CRL) при использовании без параметра **/add**, **/del** или **/put**.|  
|**/CTL**|При использовании с параметром **/add** добавляет списки доверия сертификатов (CTL). При использовании с параметром **/del** удаляет списки доверия сертификатов (CTL). Сохраняет списки CTL при использовании с параметром **/put**. Отображает списки доверия сертификатов (CTL) при использовании без параметра **/add**, **/del** или **/put**.|  
|**/del**|Удаляет сертификаты, CTL и CRL из хранилища сертификатов.|  
|**/e** *encodingType*|Указывает тип шифрования сертификата. Значение по умолчанию — `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Задает открытый флаг хранилища. Это параметр *dwFlags*, передаваемый методу **CertOpenStore**. По умолчанию используется значение CERT_SYSTEM_STORE_CURRENT_USER. Этот параметр обрабатывается, только если задан параметр **/y**.|  
|**/h**[**elp**]|Отображает синтаксис команд и параметров программы.|  
|**/n** *nam*|Задает общее имя добавляемого, удаляемого или сохраняемого сертификата. Этот параметр может применяться только для сертификатов, его нельзя задавать для CTL и CRL.|  
|**/put**|Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов. Файл сохраняется в формате X.509. Чтобы сохранить файл в формате PKCS #7, можно использовать параметр **/7** с параметром **/put**. За параметром **/put** должен следовать параметр **/c**, **/CTL** или **/CRL**. Параметр **/all** нельзя использовать вместе с параметром **/put**.|  
|**/r** *location*|Указывает расположение системного хранилища в реестре. Этот параметр обрабатывается, только если задан параметр **/s**. Параметр *location* должен иметь одно из следующих значений.<br /><br /> -   `currentUser` означает, что хранилище сертификатов находится в разделе HKEY_CURRENT_USER. Это значение по умолчанию.<br />-   `localMachine` означает, что хранилище сертификатов находится в разделе HKEY_LOCAL_MACHINE.|  
|**/s**|Означает, что хранилище сертификатов является системным. Если этот параметр не задан, хранилищем считается **StoreFile**.|  
|**/sha1** *sha1Hash*|Задает хэш SHA1 добавляемого, удаляемого или сохраняемого сертификата, CTL или CRL.|  
|**/v**|Включает отображение подробных сведений о сертификатах, CTL и CRL. Этот параметр невозможно использовать с параметрами **/add**, **/del** или **/put**.|  
|**/y** *provider*|Задает имя поставщика хранилища.|  
|**/7**|Сохраняет конечное хранилище как объект PKCS #7.|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
  
## <a name="remarks"></a>Примечания  
 Основные функции программы Certmgr.exe.  
  
-   Отображение сведений о сертификатах, CTL и CRL на консоли.  
  
-   Добавляет сертификаты, CTL и CRL в хранилище сертификатов.  
  
-   Удаляет сертификаты, CTL и CRL из хранилища сертификатов.  
  
-   Сохраняет в файл сертификат X.509, CTL или CRL из хранилища сертификатов.  
  
 Программа Certmgr.exe работает с двумя типами хранилищ сертификатов: системным и **StoreFile**. Указывать тип хранилища необязательно, поскольку программа Cedrtmgr.exe может автоматически определить тип хранилища и выполнить соответствующие действия.  
  
 При запуске программы Certmgr.exe без параметров выполняется оснастка "certmgr.msc" с графическим интерфейсом пользователя, облегчающим управление сертификатами, что также можно сделать из командной строки. В графическом интерфейсе пользователя имеется мастер импорта, копирующий сертификаты, CTL и CRL с диска в хранилище сертификатов.  
  
 Чтобы найти имена хранилищ X509Certificate для параметров `sourceStorename` и `destinationStorename`, можно скомпилировать и выполнить следующий код.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)] [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Дополнительные сведения см. в разделе [Работа с сертификатами](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Примеры  
 Следующая команда выводит подробные сведения о содержимом системного хранилища `my`, используемого по умолчанию.  
  
```  
certmgr /v /s my  
```  
  
 Следующая команда добавляет все сертификаты из файла `myFile.ext` в новый файл `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Следующая команда добавляет сертификат в файле `testcert.cer` в хранилище системы `my`.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Следующая команда добавляет сертификат в файле `TrustedCert.cer` в хранилище корневых сертификатов.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Следующая команда сохраняет сертификат с общим именем `myCert` в системном хранилище `my` в файл `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Следующая команда удаляет все CTL из системного хранилища `my` и сохраняет полученное хранилище в файл `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Следующая команда сохраняет сертификат в системном хранилище `my` в файл `newFile`. Программа запросит у пользователя номер сертификата из хранилища `my`, который следует поместить в файл `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>См. также  
 [Инструменты](../../../docs/framework/tools/index.md)   
 [Makecert.exe (средство создания сертификатов)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)   
 [Командные строки](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
