---
title: "Каналы WCF с поддержкой ReceiveContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765efb43efc0ea60ebb71bc8cdb5bd8edf973c2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a>Каналы WCF с поддержкой ReceiveContext
Данный образец демонстрирует применение каналов WCF с поддержкой <xref:System.ServiceModel.Channels.ReceiveContext>. Образец реализует службу для нахождения произведения двух чисел с помощью канала NetMSMQ.  
  
 Класс <xref:System.ServiceModel.Channels.ReceiveContext> позволяет приложению решить, обратиться ли к сообщению или оставить его в очереди для дальнейшей обработки, даже если содержимое сообщения уже было проверено. В данном образце клиент отправляет в транзакционную очередь случайные числа. Служба `ProductCalculator` получает сообщения, анализирует их содержимое (целые числа) и определяет, можно ли вычислить произведение. Если операция службы не вычисляет произведение, сообщение отправляется обратно в очередь и может быть получено вновь службой, прослушивающей очередь.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Примеры Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) , чтобы скачать все примеры [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Этот образец находится в следующем каталоге:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Использование этого образца  
  
1.  Убедитесь, что установлена служба очередей сообщений (Майкрософт) (MSMQ).  
  
    1.  Установка службы MSMQ под управлением [!INCLUDE[lserver](../../../../includes/lserver-md.md)].  
  
        1.  В **диспетчера сервера**, нажмите кнопку **функции**.  
  
        2.  В правой панели в разделе **Сводка компонентов**, нажмите кнопку **добавить компоненты**.  
  
        3.  В появившемся окне разверните **очереди сообщений**.  
  
        4.  Разверните **службы очереди сообщений**.  
  
        5.  Нажмите кнопку **интеграция со службами каталогов** (для компьютеров, присоединенных к домену), а затем нажмите кнопку **поддержка HTTP**.  
  
        6.  Нажмите кнопку **Далее**, а затем нажмите кнопку **установить**.  
  
    2.  Установка службы MSMQ под управлением [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
        1.  Откройте **панель управления**.  
  
        2.  Нажмите кнопку **программы** и затем в разделе **программы и компоненты**, нажмите кнопку **Включение и отключение компонентов Windows**.  
  
        3.  Разверните **сервер очереди сообщений Microsoft (MSMQ)**, разверните **ядро сервера очереди сообщений Microsoft (MSMQ)**, а затем установите флажки для следующих функций очереди сообщений для установки:  
  
            -   Сервер службы очередей сообщений  
  
            -   Интеграция со службами доменов MSMQ Active Directory (для компьютеров, подключенных к домену)  
  
            -   Поддержка MSMQ HTTP  
  
        4.  Нажмите кнопку **ОК**.  
  
        5.  При появлении запроса на перезагрузку компьютера нажмите кнопку **ОК** для завершения установки.  
  
2.  Убедитесь, что на компьютере установлена среда [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
3.  Откройте в среде [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] файл решения ReceiveContextProductGenerator.sln.  
  
4.  Для построения решения нажмите CTRL+SHIFT+B.  
  
5.  Чтобы запустить решение, нажмите клавиши CTRL+F5.
