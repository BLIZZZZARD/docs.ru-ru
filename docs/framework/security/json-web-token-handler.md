---
title: "Обработчик веб-токенов JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a822e87f03c4fa7e1ce7449f09efd178b87cc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="json-web-token-handler"></a>Обработчик веб-токенов JSON
Расширение обработчика веб-токенов JSON для Windows Identity Foundation позволяет создавать и проверять веб-токены JSON (JWT) в ваших приложениях. Обработчик токена JWT можно настроить для запуска в конвейере WIF, как и другие встроенные обработчики токенов безопасности, однако данный обработчик также можно использовать независимо для выполнения проверки токенов в облегченных версиях приложений. Обработчик токенов JWT особенно эффективен при использовании схемы токенов носителя OAuth 2.0, например аутентификации в Microsoft Azure Active Directory.  
  
 Обработчик токенов JWT доступен как пакет NuGet. Дополнительные сведения см. в разделе [Загрузка пакета обработчика веб-токенов JSON](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md).  
  
## <a name="scenarios"></a>Сценарии  
 Обработчик токенов JWT включает следующие ключевые сценарии:  
  
-   **Проверка токена JWT в серверном приложении**: в этом сценарии компания, которая называется Litware, имеет серверное приложение, использующее WIF для обработки веб-запросов на вход. Litware хочет разрешить использование в приложении токенов JWT для аутентификации. В приложение заносится обработчик токенов JWT, а затем конфигурация приложения обновляется путем добавления обработчика токенов JWT в конвейер WIF. По завершении обновления и после поступления новых запросов в конвейер WIF токен JWT проверяется при помощи нового обработчика, и аутентификация успешно выполняется.  
  
-   **Проверка токена JWT в веб-службе REST**: в этом сценарии компания, которая называется Litware, имеет веб-службу REST, защищенную Microsoft Azure Active Directory. Запросы к данной веб-службе должны пройти аутентификацию в каталоге Microsoft Azure AD, который создает токен JWT после успешной аутентификации. Litware имеет клиентское приложение, которое необходимо для получения доступа к веб-службе. Клиент отправляет в веб-службу запрос и представляет свой токен JWT из Microsoft Azure AD, который затем проверяется веб-службой при помощи обработчика токенов JWT. После того, как обработчик токенов JWT проверит токен, нужный ресурс будет возвращен клиенту веб-службой.  
  
## <a name="features"></a>Функции  
 Обработчик токенов JWT выполняет следующие возможности:  
  
-   **Проверка токена JWT**: токены JWT несложно проверить с помощью логики проверки данного обработчика токенов, даже в составе конвейера WIF приложения или независимо от WIF  
  
-   **Создание токена JWT**: обработчик токенов JWT можно использовать для создания токенов JWT в целях авторизации в службах более низкого уровня
