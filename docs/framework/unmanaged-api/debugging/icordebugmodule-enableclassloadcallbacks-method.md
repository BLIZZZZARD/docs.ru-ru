---
title: "Метод ICorDebugModule::EnableClassLoadCallbacks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa4add6dcaf662f1b5ec48b1243f012a6ae1f1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>Метод ICorDebugModule::EnableClassLoadCallbacks
Элементы управления ли [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) и [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) , называются обратные вызовы для этого модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bClassLoadCallbacks`  
 [in] Это значение равно `true` для включения общеязыковой среды выполнения (CLR) для вызова `ICorDebugManagedCallback::LoadClass` и `ICorDebugManagedCallback::UnloadClass` методов при возникновении связанные с ними события.  
  
 Значение по умолчанию — `false` для модулей, не являющегося динамическим. Это значение всегда равно `true` для динамических модулей и не может быть изменено.  
  
## <a name="remarks"></a>Примечания  
 `ICorDebugManagedCallback::LoadClass` И `ICorDebugManagedCallback::UnloadClass` обратные вызовы всегда включена для динамических модулей и не может быть отключена.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
    
 
