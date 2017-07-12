---
title: "Архитектура ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Архитектура ADO.NET
Обработка данных традиционно полагалась в основном на двухуровневую модель, основанную на сетевом соединении.  Так как при обработке данных все больше используется многоуровневая архитектура, программисты переходят на метод, не использующий подключение, чтобы обеспечить лучшую масштабируемость для их приложений.  
  
## Компоненты ADO.NET  
 Двумя основными компонентами [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] для доступа к данным и их обработки являются поставщики данных [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] и <xref:System.Data.DataSet>.  
  
### Поставщики данных .NET Framework  
 Поставщиками данных .NET Framework являются компоненты, которые специально сконструированы для обработки данных и быстрого, однопроходного доступа к данным только для чтения.  Объект `Connection` обеспечивает обмен данными с источником данных.  Объект `Command` позволяет обращаться к командам базы данных для возврата данных, изменения данных, выполнения хранимых процедур и передачи или получения сведений о параметрах.  `DataReader` обеспечивает высокопроизводительный поток данных из источника данных.  Наконец, `DataAdapter` предоставляет мост между объектом `DataSet` и источником данных.  `DataAdapter` использует объекты `Command` для выполнения команд SQL на источнике данных для загрузки `DataSet` с данными и согласования изменений данных, выполненных в `DataSet`, вновь с источником данных.  Дополнительные сведения см. в разделах [Поставщики данных .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) и [Получение и изменение данных в ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### DataSet  
 Класс `DataSet` в ADO.NET специально сконструирован для доступа к данным независимо от источника данных.  Поэтому он может быть использован со многими и разными источниками данных, с XML\-данными или для управления данными, локальными для приложения.  `DataSet` содержит коллекцию одного или нескольких объектов <xref:System.Data.DataTable>, состоящих из строк и столбцов данных, а также первичный ключ, внешний ключ, ограничение и связанные сведения о данных в объектах `DataTable`.  Для получения дополнительной информации см. [Объекты DataSet, DataTable и DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Следующая схема иллюстрирует связь между поставщиком данных [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] и `DataSet`.  
  
 ![Графика ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado\_1\_bpuedev11")  
Архитектура ADO.NET  
  
### Выбор между DataReader или DataSet  
 При решении вопроса о том, должно ли приложение использовать `DataReader` \(см. в разделе [Извлечение данных с помощью DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)\) или `DataSet` \(см. [Объекты DataSet, DataTable и DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)\), следует рассмотреть тип функциональности, который необходим для приложения.  `DataSet` предназначен для выполнения следующих задач.  
  
-   Локальное кэширование данных в приложении для последующей обработки.  Если нужно только считывать результаты запроса, класс `DataReader` подходит наилучшим образом.  
  
-   Удаленное взаимодействие с данными между уровнями или от веб\-службы XML.  
  
-   Динамическое взаимодействие с данными, например привязка к элементу управления Windows Forms или комбинирование и связывание данных из нескольких источников.  
  
-   Выполнение интенсивной обработки, не требующей открытого соединения с источником данных, что освобождает соединение для использования другими клиентами.  
  
 Если функциональность, предоставляемая классом `DataSet`, не нужна, можно повысить производительность приложения, используя класс `DataReader` для возврата данных в однопроходном режиме только для чтения.  Хотя класс `DataAdapter` использует класс `DataReader` для заполнения содержимого `DataSet` \(см. раздел [Заполнение набора данных с помощью адаптера данных DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)\), путем применения класса `DataReader` можно повысить производительность, т.к. будет экономиться память, которую потреблял бы объект `DataSet`, и избежать обработки, необходимой для создания и заполнения содержимого `DataSet`.  
  
## LINQ to DataSet  
 Технология LINQ to DataSet предоставляет возможности выполнения запросов и проверки типов во время компиляции для данных, кэшированных в объекте DataSet.  Эта технология позволяет писать запросы на одном из языков .NET Framework, например C\# или Visual Basic.  Для получения дополнительной информации см. [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## LINQ to SQL  
 LINQ to SQL поддерживает запросы к модели объектов, сопоставленной со структурами данных реляционной базы данных, без использования промежуточной концептуальной модели.  Каждая таблица представляется отдельным классом; таким образом, модель объектов тесно привязывается к схеме реляционной базы данных.  LINQ to SQL преобразует запросы LINQ из модели объектов в язык Transact\-SQL и передает их в базу данных для выполнения.  При возврате результатов базой данных LINQ to SQL преобразует результаты обратно в объекты.  Для получения дополнительной информации см. [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## ADO.NET Entity Framework  
 Платформа ADO.NET Entity Framework разработана, чтобы разработчики могли создавать приложения для доступа к данным путем программирования по концептуальной модели приложения, а не по реляционной схеме хранения.  Ее целью является уменьшение объема кода и затрат на сопровождение приложений, ориентированных на обработку данных.  Для получения дополнительной информации см. [Платформа ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## Службы данных WCF  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] используется для развертывания служб данных в Интернете или интрасети.  Данные структурируются как сущности и отношения согласно спецификациям модели EDM.  Данные, развертываемые в данной модели, адресуются по стандартному протоколу HTTP.  Для получения дополнительной информации см. [Службы WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## XML и ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] использует возможности XML для предоставления доступа к данным без сетевого соединения.  Разработка [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] производилась одновременно с XML\-классами платформы [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; оба они являются компонентами одной архитектуры.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] и классы XML в [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] сходятся в объекте `DataSet`.  Объект `DataSet` может заполняться данными из XML\-источника, будь то файл или поток XML\-данных.  Объект `DataSet` может быть записан в виде XML\-кода, соответствующего спецификациям консорциума W3C, который включает в себя схему в виде XSD, независимо от источника данных, находящихся в `DataSet`.  Так как в `DataSet` собственным форматом сериализации является XML, он является отличным способом перемещения данных между уровнями. Это делает `DataSet` оптимальным решением для удаленного взаимодействия с контекстом данных и схемы как в направлении к веб\-службе XML, так и в обратном направлении.  Для получения дополнительной информации см. [XML\-документы и данные](../../../../docs/standard/data/xml/index.md).  
  
## См. также  
 [Общие сведения об ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)   
 [Центр разработчиков, поставщики ADO.NET Managed Provider и набор данных](http://go.microsoft.com/fwlink/?LinkId=217917)