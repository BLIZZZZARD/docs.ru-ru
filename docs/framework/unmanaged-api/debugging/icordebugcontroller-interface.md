---
title: "ICorDebugController интерфейс1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController
helpviewer_keywords: ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bde0ef86ff6304c696ad8c68fc81c0a339ed6e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontroller-interface1"></a>ICorDebugController интерфейс1
Представляет область (<xref:System.Diagnostics.Process> или <xref:System.AppDomain>), в которой можно осуществлять управление контекстом выполнения кода.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание:|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|Этот метод устарел.|  
|`ICorDebugController::CommitChanges`|Этот метод устарел.|  
|[Метод Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|Возобновление выполнения управляемых потоков после вызова [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).|  
|[Метод Detach](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|Отсоединяет отладчик от процесса или домена приложения.|  
|[Метод EnumerateThreads](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|Возвращает перечислитель для активных управляемых потоков в процессе.|  
|[Метод HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|Возвращает значение, указывающее ли любого управляемого обратных вызовов в настоящее время в очереди для заданного потока.|  
|[Метод IsRunning](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|Возвращает значение, указывающее, является ли потоки в процессе в данный момент выполнения свободно.|  
|[Метод SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|Задает состояние отладки все управляемые потоки в процессе.|  
|[Метод Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|Выполняет совместную остановку всех потоков, выполняющих управляемый код в процессе.|  
|[Метод Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|Завершает процесс с помощью указанного кода выхода.|  
  
## <a name="remarks"></a>Примечания  
 Если `ICorDebugController` является управление процессом, включает все потоки данного процесса. Если `ICorDebugController` — управление доменом приложения, включает только потоки данного конкретного домена приложений.  
  
> [!NOTE]
>  Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
