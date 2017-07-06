---
title: "Контекстное соединение | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Контекстное соединение
Проблема внутреннего доступа к данным встречается довольно часто.  Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR.  Один из вариантов состоит в том, чтобы создать соединение с использованием <xref:System.Data.SqlClient.SqlConnection>, задать строку соединения, в которой указан локальный сервер, и открыть соединение.  В этом случае необходимо указать учетные данные для входа.  К тому же соединение устанавливается в другом сеансе базы данных \(по сравнению с хранимой процедурой или функцией\), может иметь другие параметры `SET`, находиться в отдельной транзакции, не позволять обнаруживать используемые временные таблицы и т. д.  Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что какой\-то пользователь подключился к этому серверу и выполнил инструкцию SQL для вызова соответствующего кода.  В этой ситуации можно обеспечить выполнение хранимой процедуры или функции в контексте данного соединения вместе с осуществляемой в нем транзакцией, параметрами `SET` и т. д.  В этом состоит так называемое контекстное соединение.  
  
 Контекстное соединение позволяет выполнять инструкции Transact\-SQL в том же контексте, в каком первоначально был вызван конкретный код.  Более подробные сведения см. в электронной документации по SQL Server для используемой версии SQL Server.  
  
 **Электронная документация по SQL Server**  
  
1.  [Подключение контекста](http://go.microsoft.com/fwlink/?LinkId=115395)  
  
## См. также  
 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/ru-ru/5358a825-e19b-49aa-8214-674ce5fed1da)   
 [Центр разработчиков, поставщики ADO.NET Managed Provider и набор данных](http://go.microsoft.com/fwlink/?LinkId=217917)