---
title: "Задание адреса конечной точки"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 403ff897de4dc9ee95a854d9658bdee344755d59
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="specifying-an-endpoint-address"></a>Задание адреса конечной точки
Вся связь со службой [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] осуществляется через ее конечные точки. Каждая конечная точка службы <xref:System.ServiceModel.Description.ServiceEndpoint> содержит адрес <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, привязку <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> и контракт <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. В контракте задается, какие операции доступны. Привязка определяет, как осуществлять взаимодействие со службой, а адрес показывает, где можно найти службу. Каждая конечная точка должна иметь уникальный адрес. Адрес конечной точки представляется классом <xref:System.ServiceModel.EndpointAddress>, содержащим универсальный код ресурса (URI), который, в свою очередь, обозначает адрес службы, <xref:System.ServiceModel.EndpointAddress.Identity%2A>, представляющий удостоверение безопасности службы и коллекцию необязательных заголовков <xref:System.ServiceModel.EndpointAddress.Headers%2A>. Необязательные заголовки содержат более подробную информацию для идентификации конечной точки и взаимодействия с ней. Например, в заголовках может содержаться информация о том, как следует обрабатывать входящее сообщение, куда конечная точка должна отправить ответное сообщение или какой экземпляр службы необходимо использовать для обработки входящего сообщения от конкретного пользователя, если доступно несколько экземпляров.  
  
## <a name="definition-of-an-endpoint-address"></a>Определение адреса конечной точки  
 В [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] адрес <xref:System.ServiceModel.EndpointAddress> моделирует ссылку на конечную точку (EPR) согласно определению в стандарте WS-Addressing.  
  
 Универсальный код ресурса (URI) адреса для большинства видов транспорта состоит из четырех частей. Например, код "http://www.fabrikam.com:322/mathservice.svc/secureEndpoint" состоит из следующих четырех частей.  
  
-   Схема: http:  
  
-   Компьютер: www.fabrikam.com  
  
-   (Необязательно) Порт: 322  
  
-   Путь: /mathservice.svc/secureEndpoint  
  
 Одной из особенностей модели EPR является то, что каждая ссылка на конечную точку может содержать некоторые ссылочные параметры, которые добавляют дополнительные идентификационные сведения. В [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] эти ссылочные параметры моделируются как экземпляры класса <xref:System.ServiceModel.Channels.AddressHeader>.  
  
 Адрес конечной точки службы можно задать императивно с помощью кода или декларативно с помощью конфигурации. Как правило, определять конечные точки в коде непрактично, поскольку привязки и адреса для развернутой службы чаще всего отличаются от привязок и адресов, используемых в процессе разработки службы. Обычно более целесообразно задать конечные точки службы в конфигурации, а не в коде. Если не указывать привязку и адрес в коде, их можно изменять без повторной компиляции и повторного развертывания приложения. Если конечные точки не заданы в коде или в конфигурации, то среда выполнения добавляет одну конечную точку по умолчанию для каждого базового адреса в каждом контракте службы, реализованном в службе.  
  
 В [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] существует два способа задания адресов конечных точек для службы. Можно задать абсолютный адрес для каждой конечной точки, связанной со службой, или указать базовый адрес для узла службы <xref:System.ServiceModel.ServiceHost>, а затем задать адрес для каждой связанной с этой службой конечной точки, которая определяется относительно этого базового адреса. Любой из этих методов можно использовать для задания адресов конечных точек для службы как в конфигурации, так и в коде. Если не указывать относительный адрес, служба использует базовый адрес. Можно указать несколько базовых адресов для службы, однако для каждого транспорта каждая служба может иметь только один базовый адрес. Если имеется несколько конечных точек, настроенных по разным привязкам, каждая из них должна иметь уникальный адрес. Конечные точки, использующие одну привязку, но разные контракты, могут иметь один и тот же адрес.  
  
 При размещении в службах IIS управление экземпляром <xref:System.ServiceModel.ServiceHost> не осуществляется пользователем. При размещении в службах IIS базовый адрес - это всегда адрес службы, указанный в файле SVC. Следовательно, для конечных точек служб, размещенных в IIS, следует использовать относительные адреса. Указание полного адреса конечной точки может привести к ошибкам при развертывании службы. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Развертывание службы WCF, размещенной в IIS](../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="defining-endpoint-addresses-in-configuration"></a>Определение адреса конечной точки в конфигурации  
 Для определения конечной точки в файле конфигурации, используйте [ \<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) элемента.  
  
 [!code-xml[S_UEHelloWorld#5](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp2.config#5)]  
  
 Когда <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> вызова (то есть, когда ведущее приложение пытается запустить службу), система выполняет поиск [ \<службы >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) элемент с атрибутом name, указывающее «UE. Samples.HelloService». Если [ \<службы >](../../../docs/framework/configure-apps/file-schema/wcf/service.md) найден элемент, система загружает указанный класс и создает конечные точки, с помощью конечных точек, содержащиеся в файле конфигурации. Благодаря такому механизму можно загружать и запускать службу с двумя строками кода, при этом не указывая привязку и адрес в коде. Преимуществом этого подхода является отсутствие необходимости в повторной компиляции или повторном развертывании приложения при внесении этих изменений.  
  
 Необязательные заголовки, объявляются в [ \<заголовки >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md). Ниже приведен пример элементов, используемых для задания конечных точек службы в файле конфигурации, различающем два заголовка: клиентов типа "Gold" из «http://tempuri1.org/» и клиентов типа "Standard" из «http://tempuri2.org/». Вызов этой службы клиент должен иметь соответствующую [ \<заголовки >](../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md) в файле конфигурации.  
  
 [!code-xml[S_UEHelloWorld#1](../../../samples/snippets/common/VS_Snippets_CFX/s_uehelloworld/common/serviceapp.config#1)]  
  
 Можно настроить заголовки для отдельных сообщений конечной точки, а не всех одновременно (как показано выше). В этом случае для создания нового контекста в клиентском приложении для добавления пользовательского заголовка в исходящее сообщение используется <xref:System.ServiceModel.OperationContextScope>, как показано в следующем примере.  
  
 [!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
 [!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]  
  
## <a name="endpoint-address-in-metadata"></a>Адрес конечной точки в метаданных  
 Адрес конечной точки представляется на языке описания веб-служб (WSDL) в виде элемента ссылки на конечную точку EPR WS-Addressing `EndpointReference` в элементе `wsdl:port` соответствующей конечной точки. Ссылка на конечную точку (EPR) содержит адрес конечной точки и любые свойства адреса. Обратите внимание, что EPR в элементе `wsdl:port` заменяет `soap:Address`, как показано в следующем примере.  
  
  
  
## <a name="defining-endpoint-addresses-in-code"></a>Определение адреса конечной точки в коде  
 Адрес конечной точки можно создать в коде с помощью класса <xref:System.ServiceModel.EndpointAddress>. URI, заданный для адреса конечной точки, может представлять собой полный путь или путь относительно базового адреса службы. В следующем фрагменте кода показано создание экземпляра класса <xref:System.ServiceModel.EndpointAddress> и его добавление в экземпляр <xref:System.ServiceModel.ServiceHost>, в котором размещается служба.  
  
 В следующем примере показано, как задавать полный адрес конечной точки в коде.  
  
 [!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]  
  
 В следующем примере показано, как добавлять относительный адрес ("MyService") в базовый адрес узла службы.  
  
 [!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]  
  
> [!NOTE]
>  Свойства объекта <xref:System.ServiceModel.Description.ServiceDescription> в приложении службы нельзя изменять после вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> для объекта <xref:System.ServiceModel.ServiceHostBase>. Некоторые члены, такие как свойство <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> и методы `AddServiceEndpoint` классов <xref:System.ServiceModel.ServiceHostBase> и <xref:System.ServiceModel.ServiceHost>, создают исключение, если их изменить после вызова этого метода. Другие члены можно изменять без появления исключения, но результат при этом будет неопределенным.  
>   
>  Аналогично, на стороне клиента нельзя изменять значения <xref:System.ServiceModel.Description.ServiceEndpoint> после вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> для объекта <xref:System.ServiceModel.ChannelFactory>. Если после вызова этого метода изменить свойство <xref:System.ServiceModel.ChannelFactory.Credentials%2A>, создается исключение. Изменение других значений описания клиента происходит без ошибок, но результат изменения в этом случае является неопределенным.  
>   
>  Как для службы, так и для клиента, рекомендуется изменять описание до вызова метода <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="using-default-endpoints"></a>Использование конечных точек по умолчанию  
 Если конечные точки не заданы в коде или в конфигурации, то среда выполнения предоставляет конечные точки по умолчанию, добавляя одну конечную точку по умолчанию для каждого базового адреса в каждом контракте службы, реализованном в службе. Базовый адрес можно указывать в коде или в конфигурации, а конечные точки по умолчанию добавляются, когда вызывается метод <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> в объекте <xref:System.ServiceModel.ServiceHost>.  
  
 Если конечные точки предоставляются явно, то конечные точки по умолчанию можно добавить, вызвав метод <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> класса <xref:System.ServiceModel.ServiceHost> перед вызовом <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) и [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>См. также  
 <xref:System.ServiceModel.EndpointAddress>  
 [Идентификация и проверка подлинности службы](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Общие сведения о создании конечных точек](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Размещение](../../../docs/framework/wcf/feature-details/hosting.md)
