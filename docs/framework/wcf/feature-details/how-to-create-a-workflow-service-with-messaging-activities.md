---
title: "Как создать службу рабочего процесса с помощью действий обмена сообщениями"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 24456bbbefe305a3e9620e5396c8d300163e00d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Как создать службу рабочего процесса с помощью действий обмена сообщениями
В этом разделе приведены сведения о том, как создать простую службу рабочего процесса с помощью действий обмена сообщениями. В нем рассматривается механизм создания службы рабочего процесса, когда служба состоит только из действий обмена сообщениями. В реальных службах рабочий процесс содержит множество других действий. Служба реализует одну операцию с именем Echo, которая принимает строку и возвращает строку вызывающему коду. Это первый из двух разделов. Следующий раздел [How To: доступ к службе из приложения рабочего процесса](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) рассматривается процесс создания приложения рабочего процесса, который может вызывать службу, созданной в данном разделе.  
  
### <a name="to-create-a-workflow-service-project"></a>Создание проекта службы рабочего процесса  
  
1.  Запустите [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Нажмите кнопку **файл** последовательно выберите пункты **New**, а затем **проекта** для отображения **диалоговое окно нового проекта**. Выберите **рабочего процесса** из списка установленных шаблонов и **приложение службы рабочего процесса WCF** в списке типов проектов. Присвойте проекту имя `MyWFService` и использовать расположение по умолчанию, как показано на следующем рисунке.  
  
     Нажмите кнопку **ОК** кнопку, чтобы закрыть **диалоговое окно нового проекта**.  
  
3.  После создания проекта в конструкторе открывается файл Service1.xamlx, как показано на следующем рисунке.  
  
     ![Рабочий процесс по умолчанию, отображаемый в конструкторе](../../../../docs/framework/wcf/feature-details/media/defaultworkflowservice.JPG "DefaultWorkflowService")  
  
     Щелкните правой кнопкой мыши действие **последовательная служба** и выберите **удалить**.  
  
### <a name="to-implement-the-workflow-service"></a>Реализация службы рабочего процесса  
  
1.  Выберите **элементов** вкладка в левой части экрана, чтобы открыть панель элементов и щелкните вешку, чтобы оставить окно открытым. Разверните **обмен сообщениями** области элементов для отображения действий по обмену сообщениями и шаблоны действий обмена сообщениями, как показано на следующем рисунке.  
  
     ![Панель элементов с открытой вкладкой обмена сообщениями развернутой](../../../../docs/framework/wcf/feature-details/media/wfdesignertoolbox.JPG "WFDesignerToolbox")  
  
2.  Перетаскивание **ReceiveAndSendReply** шаблона в конструктор рабочих процессов. При этом создается <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` действие с **Receive** действия, за которым следует <xref:System.ServiceModel.Activities.SendReply> действия, как показано на следующем рисунке.  
  
     ![Шаблон ReceiveAndSendReply в конструкторе](../../../../docs/framework/wcf/feature-details/media/receiveandsendreply.JPG "ReceiveAndSendReply")  
  
     Обратите внимание, что у действия <xref:System.ServiceModel.Activities.SendReply> свойство <xref:System.ServiceModel.Activities.SendReply.Request%2A> имеет значение `Receive`, это имя действия <xref:System.ServiceModel.Activities.Receive>, на которое отвечает действие <xref:System.ServiceModel.Activities.SendReply>.  
  
3.  В <xref:System.ServiceModel.Activities.Receive> типа действия `Echo` в текстовое поле с меткой **Имя_операции**. Это задает имя операции, которую реализует служба.  
  
     ![Укажите имя операции](../../../../docs/framework/wcf/feature-details/media/defineoperation.JPG "DefineOperation")  
  
4.  С <xref:System.ServiceModel.Activities.Receive> действии, выбранном, откройте окно свойств Если он еще не открыт, щелкнув **представление** , выберите в меню **окно свойств**. В **окно свойств** прокрутите вниз, пока не увидите **CanCreateInstance** и установите флажок, как показано на следующем рисунке. Этот параметр позволяет службе рабочего процесса создавать новый экземпляр службы при получении сообщения (если это необходимо).  
  
     ![Свойство CanCreateInstance](../../../../docs/framework/wcf/feature-details/media/cancreateinstance.JPG "CanCreateInstance")  
  
5.  Выберите <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` действие и нажмите кнопку **переменных** кнопки в левом нижнем углу конструктора. Откроется редактор переменных. Нажмите кнопку **создания переменной** ссылку, чтобы добавить переменную для хранения строки, отправляемой операции. Имя переменной `msg` и задайте его **переменной** введите строку, как показано на следующем рисунке.  
  
     ![Добавьте переменную](../../../../docs/framework/wcf/feature-details/media/addvariable.JPG "AddVariable")  
  
     Нажмите кнопку **переменных** кнопку, чтобы закрыть редактор переменных.  
  
6.  Нажмите кнопку **определить...** связать **содержимого** текстовое поле в <xref:System.ServiceModel.Activities.Receive> действия для отображения **определение содержимого** диалогового окна. Выберите **параметры** переключатель, нажмите кнопку **добавьте параметр** , введите `inMsg` в **имя** текстовое поле, выберите **строка**в **тип** раскрывающемся списке и введите `msg` в **назначено** текстовое поле, как показано на следующем рисунке.  
  
     ![Добавление содержимого параметров](../../../../docs/framework/wcf/feature-details/media/parameterscontent.jpg "ParametersContent")  
  
     Это указывает, что действие Receive получает строковый параметр, а данные будут привязаны к переменной `msg`. Нажмите кнопку **ОК** закрыть **определение содержимого** диалогового окна.  
  
7.  Нажмите кнопку **определить...**  ссылку в **содержимого** поле <xref:System.ServiceModel.Activities.SendReply> действия для отображения **определение содержимого** диалогового окна. Выберите **параметры** переключатель, нажмите кнопку **добавьте параметр** , введите `outMsg` в **имя** текстового поля, выберите **строка**в **тип** раскрывающегося списка и `msg` в **значение** текстовое поле, как показано на следующем рисунке.  
  
     ![Добавление содержимого параметров](../../../../docs/framework/wcf/feature-details/media/parameterscontent2.jpg "ParametersContent2")  
  
     Это указывает, что действие <xref:System.ServiceModel.Activities.SendReply> отправляет сообщение или тип контракта сообщения, а данные привязаны к переменной `msg`. Поскольку это действие <xref:System.ServiceModel.Activities.SendReply>, данные в `msg` используются для заполнения сообщения, которое действие возвращает клиенту. Нажмите кнопку **ОК** закрыть **определение содержимого** диалогового окна.  
  
8.  Сохраните и постройте решение, нажав кнопку **построения** , выберите в меню **построить решение**.  
  
## <a name="configure-the-workflow-service-project"></a>Настройка проекта службы рабочего процесса  
 Служба рабочего процесса создана. В этом разделе приведены сведения о конфигурации решения службы рабочего процесса, чтобы упростить ее размещение и выполнение. Для размещения службы в этом решении используется сервер разработки ASP.NET.  
  
#### <a name="to-set-project-start-up-options"></a>Задание параметров запуска проекта  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyWFService** и выберите **свойства** для отображения **свойства проекта** диалогового окна.  
  
2.  Выберите **Web** и выберите **определенную страницу** под **действие при запуске** и тип `Service1.xamlx` в текстовом поле, как показано на следующем рисунке.  
  
     ![Диалоговое окно свойств проекта](../../../../docs/framework/wcf/feature-details/media/projectpropertiesdlg.JPG "ProjectPropertiesDlg")  
  
     Служба, которая определена в Service1.xamlx, будет размещена на сервере разработки ASP.NET.  
  
3.  Чтобы запустить службу, нажмите сочетание клавиш CTRL+F5. В нижней правой области рабочего стола появится значок сервера разработки ASP.NET, как показано на следующем рисунке.  
  
     ![Значок сервера разработки ASP.NET](../../../../docs/framework/wcf/feature-details/media/aspnetdevservericon.JPG "ASPNETDEVServerIcon")  
  
     Кроме того, в Internet Explorer для службы откроется справочная страница службы WCF.  
  
     ![Страница справки WCF](../../../../docs/framework/wcf/feature-details/media/wcfhelppate.JPG "WCFHelpPate")  
  
4.  Перейдите к [How To: доступ к службе из приложения рабочего процесса](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md) раздела, чтобы создать клиент рабочего процесса, вызывающий эту службу.  
  
## <a name="see-also"></a>См. также  
 [Службы рабочих процессов](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Общие сведения о размещении служб рабочих процессов](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [Действия обмена сообщениями](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
