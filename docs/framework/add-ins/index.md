---
title: "Надстройки и расширения среды"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd09d0da70869ba193b414d8a2ce6c25cbb6b38
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2017
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="27a3a-102">Надстройки и расширения среды</span><span class="sxs-lookup"><span data-stu-id="27a3a-102">Add-ins and Extensibility</span></span>
<span data-ttu-id="27a3a-103"><a name="top"></a> Надстройки предоставляют расширенные возможности или службы для ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="27a3a-103"><a name="top"></a> Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="27a3a-104">Платформа [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] предоставляет модель программирования, которую разработчики могут использовать для разработки надстроек и их активации в ведущем приложении.</span><span class="sxs-lookup"><span data-stu-id="27a3a-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="27a3a-105">Для этого создается конвейер взаимодействия между ведущим приложением и надстройкой.</span><span class="sxs-lookup"><span data-stu-id="27a3a-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="27a3a-106">Модель реализуется с помощью типов в пространствах имен <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>и <xref:System.AddIn.Contract> .</span><span class="sxs-lookup"><span data-stu-id="27a3a-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="27a3a-107">Обзор включает следующие разделы.</span><span class="sxs-lookup"><span data-stu-id="27a3a-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="27a3a-108">Модель надстроек</span><span class="sxs-lookup"><span data-stu-id="27a3a-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="27a3a-109">Отличия между надстройками и ведущими приложениями</span><span class="sxs-lookup"><span data-stu-id="27a3a-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="27a3a-110">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="27a3a-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="27a3a-111">Ссылки</span><span class="sxs-lookup"><span data-stu-id="27a3a-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="27a3a-112">Дополнительные примеры кода и CTP-версии средств для построения конвейеров надстроек можно найти на сайте [CodePlex в разделе, посвященном управлению расширениями и надстройками](http://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="27a3a-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="27a3a-113">Модель надстроек</span><span class="sxs-lookup"><span data-stu-id="27a3a-113">Add-in Model</span></span>  
 <span data-ttu-id="27a3a-114">Модель надстроек состоит из ряда сегментов, составляющих конвейер надстройки (также известный как конвейер взаимодействия), который отвечает за весь обмен данными между надстройкой и ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="27a3a-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="27a3a-115">Конвейер — это симметричная модель взаимодействия сегментов, служащих для обмена данными между надстройкой и ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="27a3a-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="27a3a-116">Разработка этих сегментов между ведущим приложением и надстройкой обеспечивает необходимые уровни абстракции, которые поддерживают управление версиями и изоляцию надстройки.</span><span class="sxs-lookup"><span data-stu-id="27a3a-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="27a3a-117">На рисунке ниже показан конвейер.</span><span class="sxs-lookup"><span data-stu-id="27a3a-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="27a3a-118">![Добавить &#45; в модель конвейера. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="27a3a-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="27a3a-119">Конвейер надстройки</span><span class="sxs-lookup"><span data-stu-id="27a3a-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="27a3a-120">Сборки для этих сегментов могут и не находиться в одном и том же домене приложения.</span><span class="sxs-lookup"><span data-stu-id="27a3a-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="27a3a-121">Вы можете загрузить надстройку в новый домен приложения, в существующий домен приложения или даже в домен приложения ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="27a3a-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="27a3a-122">Несколько надстроек можно загрузить в один домен приложения, что позволяет им совместно использовать ресурсы и контексты безопасности.</span><span class="sxs-lookup"><span data-stu-id="27a3a-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="27a3a-123">Модель надстроек поддерживает рекомендуемую, но необязательную границу между ведущим приложением и надстройкой, которая называется границей изоляции (или границей удаленного взаимодействия).</span><span class="sxs-lookup"><span data-stu-id="27a3a-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="27a3a-124">Эта граница может быть границей домена приложения или процесса.</span><span class="sxs-lookup"><span data-stu-id="27a3a-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="27a3a-125">Сегмент контракта в середине конвейера загружается в домен приложения ведущего приложения и в домен приложения надстройки.</span><span class="sxs-lookup"><span data-stu-id="27a3a-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="27a3a-126">Контракт определяет виртуальные методы, используемые ведущим приложением и надстройкой для обмена типами друг с другом.</span><span class="sxs-lookup"><span data-stu-id="27a3a-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="27a3a-127">Для передачи через границу изоляции типы должны быть контрактами или сериализуемыми типами.</span><span class="sxs-lookup"><span data-stu-id="27a3a-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="27a3a-128">Типы, не являющиеся контрактами или сериализуемыми типами, необходимо преобразовать в контракты с помощью сегментов адаптера в конвейере.</span><span class="sxs-lookup"><span data-stu-id="27a3a-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="27a3a-129">Сегменты представления конвейера являются абстрактными базовыми классами или интерфейсами, которые предоставляют ведущему приложению и надстройке представление совместно используемых ими методов, как определено в контракте.</span><span class="sxs-lookup"><span data-stu-id="27a3a-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="27a3a-130">Подробнее о разработке сегментов конвейера см. в разделе [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="27a3a-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="27a3a-131">В последующих разделах описаны возможности модели надстроек.</span><span class="sxs-lookup"><span data-stu-id="27a3a-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="27a3a-132">Независимое управление версиями</span><span class="sxs-lookup"><span data-stu-id="27a3a-132">Independent Versioning</span></span>  
 <span data-ttu-id="27a3a-133">Модель надстроек позволяет раздельно управлять версиями основных приложений и надстроек.</span><span class="sxs-lookup"><span data-stu-id="27a3a-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="27a3a-134">Соответственно, модель надстроек делает возможными следующие сценарии:</span><span class="sxs-lookup"><span data-stu-id="27a3a-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="27a3a-135">создание адаптера, который позволяет ведущему приложению использовать надстройку, созданную для предыдущей версии ведущего приложения;</span><span class="sxs-lookup"><span data-stu-id="27a3a-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="27a3a-136">создание адаптера, который позволяет ведущему приложению использовать надстройку, созданную для более поздней версии ведущего приложения;</span><span class="sxs-lookup"><span data-stu-id="27a3a-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="27a3a-137">создание адаптера, который позволяет ведущему приложению использовать надстройку, созданную для другого ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="27a3a-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="27a3a-138">Обнаружение и активация</span><span class="sxs-lookup"><span data-stu-id="27a3a-138">Discovery and Activation</span></span>  
 <span data-ttu-id="27a3a-139">Надстройку можно активировать с помощью токена из коллекции, которая представляет надстройки, обнаруженные в банке данных.</span><span class="sxs-lookup"><span data-stu-id="27a3a-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="27a3a-140">Надстройки обнаруживаются путем поиска типа, который определяет представление ведущего приложения надстройки.</span><span class="sxs-lookup"><span data-stu-id="27a3a-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="27a3a-141">Кроме того, определенную надстройку можно найти по типу, который ее определяет.</span><span class="sxs-lookup"><span data-stu-id="27a3a-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="27a3a-142">Банк данных состоит из двух файлов кэша: хранилища конвейеров и хранилища надстроек.</span><span class="sxs-lookup"><span data-stu-id="27a3a-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="27a3a-143">Подробнее об обновлении и повторной сборке банка данных см. в разделе [Обнаружение надстройки](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="27a3a-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="27a3a-144">Информацию об активации надстроек см. в разделах [Активация надстройки](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) и [Практическое руководство. Активация надстроек с другими параметрами изоляции и безопасности](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="27a3a-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="27a3a-145">Уровни изоляции и внешние процессы</span><span class="sxs-lookup"><span data-stu-id="27a3a-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="27a3a-146">Модель надстроек поддерживает несколько уровней изоляции между надстройкой и ведущим приложением или между несколькими надстройками. Ниже перечислены эти уровни, начиная с наименее изолированного.</span><span class="sxs-lookup"><span data-stu-id="27a3a-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="27a3a-147">Надстройка выполняется в том же домене приложения, что и ведущее приложение.</span><span class="sxs-lookup"><span data-stu-id="27a3a-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="27a3a-148">Эта схема не рекомендуется, так как утрачивается изоляция и возможности выгрузки, которые появляются при использовании разных доменов приложений.</span><span class="sxs-lookup"><span data-stu-id="27a3a-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="27a3a-149">Несколько надстроек загружаются в один домен приложения, который отличается от домена приложения, используемого ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="27a3a-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="27a3a-150">Каждая надстройка загружается отдельно в свой собственный домен приложения.</span><span class="sxs-lookup"><span data-stu-id="27a3a-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="27a3a-151">Это наиболее распространенный уровень изоляции.</span><span class="sxs-lookup"><span data-stu-id="27a3a-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="27a3a-152">Несколько надстроек загружаются в один домен приложения во внешнем процессе.</span><span class="sxs-lookup"><span data-stu-id="27a3a-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="27a3a-153">Каждая надстройка загружается отдельно в свой собственный домен приложения во внешнем процессе.</span><span class="sxs-lookup"><span data-stu-id="27a3a-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="27a3a-154">Это схема с максимальной изоляцией.</span><span class="sxs-lookup"><span data-stu-id="27a3a-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="27a3a-155">Подробнее об использовании внешних процессов см. в разделе [Практическое руководство. Активация надстроек с другими параметрами изоляции и безопасности](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="27a3a-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="27a3a-156">Управление жизненным циклом объекта</span><span class="sxs-lookup"><span data-stu-id="27a3a-156">Lifetime Management</span></span>  
 <span data-ttu-id="27a3a-157">Так как модель надстроек распространяется на границы домена приложения и процесса, сборки мусора самой по себе недостаточно для освобождения и восстановления объектов.</span><span class="sxs-lookup"><span data-stu-id="27a3a-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="27a3a-158">Модель надстроек предоставляет механизм управления жизненным циклом, в котором используются токены и подсчет ссылок. Этот механизм обычно не требует написания дополнительного кода.</span><span class="sxs-lookup"><span data-stu-id="27a3a-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="27a3a-159">Подробнее см. в разделе [Управление жизненным циклом](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="27a3a-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="27a3a-160">К началу</span><span class="sxs-lookup"><span data-stu-id="27a3a-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="27a3a-161">Отличия между надстройками и ведущими приложениями</span><span class="sxs-lookup"><span data-stu-id="27a3a-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="27a3a-162">Разница между надстройкой и ведущим приложением состоит единственно в том, что ведущее приложение активирует надстройку.</span><span class="sxs-lookup"><span data-stu-id="27a3a-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="27a3a-163">Ведущее приложение может быть больше надстройки, например в случае с текстовым редактором и его средством проверки орфографии, или меньше надстройки, например в случае с клиентом обмена мгновенными сообщениями, в который встроен проигрыватель.</span><span class="sxs-lookup"><span data-stu-id="27a3a-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="27a3a-164">Модель надстроек поддерживает надстройки в клиентских и серверных сценариях.</span><span class="sxs-lookup"><span data-stu-id="27a3a-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="27a3a-165">Примерами серверных надстроек служат надстройки, предоставляющие для почтовых серверов проверку на наличие вирусов, фильтрацию нежелательной почты и защиту протокола IP.</span><span class="sxs-lookup"><span data-stu-id="27a3a-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="27a3a-166">Примерами клиентских надстроек могут быть надстройки для текстовых редакторов, специальные функциональные возможности графических программ и игр, а также проверка на наличие вирусов в локальных почтовых клиентах.</span><span class="sxs-lookup"><span data-stu-id="27a3a-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local e-mail clients.</span></span>  
  
 [<span data-ttu-id="27a3a-167">К началу</span><span class="sxs-lookup"><span data-stu-id="27a3a-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="27a3a-168">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="27a3a-168">Related Topics</span></span>  
  
|<span data-ttu-id="27a3a-169">Заголовок</span><span class="sxs-lookup"><span data-stu-id="27a3a-169">Title</span></span>|<span data-ttu-id="27a3a-170">Описание</span><span class="sxs-lookup"><span data-stu-id="27a3a-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="27a3a-171">Pipeline Development</span><span class="sxs-lookup"><span data-stu-id="27a3a-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="27a3a-172">Описывается конвейер взаимодействия сегментов от ведущего приложения к надстройке.</span><span class="sxs-lookup"><span data-stu-id="27a3a-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="27a3a-173">Приводятся примеры кода в пошаговых руководствах, в которых описывается построение конвейера и развертывание сегментов в конвейере в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27a3a-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="27a3a-174">Домены приложений и сборки</span><span class="sxs-lookup"><span data-stu-id="27a3a-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="27a3a-175">Описывается связь между доменами приложений, образующими границу изоляции для обеспечения безопасности, надежности и управления версиями, и сборками.</span><span class="sxs-lookup"><span data-stu-id="27a3a-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="27a3a-176">К началу</span><span class="sxs-lookup"><span data-stu-id="27a3a-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="27a3a-177">Ссылки</span><span class="sxs-lookup"><span data-stu-id="27a3a-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="27a3a-178">К началу</span><span class="sxs-lookup"><span data-stu-id="27a3a-178">Back to top</span></span>](#top)