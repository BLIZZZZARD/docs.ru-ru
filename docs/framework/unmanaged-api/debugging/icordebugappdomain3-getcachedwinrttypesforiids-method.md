---
title: "Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a7ce44dcfc709b4fea1952471cf31f5f07d4d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
Возвращает перечислитель для кэшированных [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типов в домене приложения на основе их интерфейс идентификаторов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cReqTypes`  
 [in] Количество требуемых типов.  
  
 `iidsToResolve`  
 [in] Указатель на массив, содержащий идентификаторы интерфейса, соответствующего управляемого представления [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типы должны быть получены.  
  
 `ppTypesEnum`  
 [out] Указатель на адрес объекта интерфейса «ICorDebugTypeEnum», позволяет использовать кэшированные перечисления управляемых представления [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типы, полученные на основе идентификаторов интерфейса в `iidsToResolve`.  
  
## <a name="remarks"></a>Примечания  
 Если метод не может получить сведения для идентификации определенного интерфейса, соответствующую запись в коллекции «ICorDebugTypeEnum» будет иметь тип `ELEMENT_TYPE_END` ошибок из-за проблемы извлечения данных, или `ELEMENT_TYPE_VOID` для Неизвестный интерфейс идентификаторы.  
  
## <a name="requirements"></a>Требования  
 **Платформы:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorDebugAppDomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
