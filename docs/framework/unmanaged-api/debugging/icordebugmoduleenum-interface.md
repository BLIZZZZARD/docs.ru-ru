---
title: "ICorDebugModuleEnum интерфейс1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleEnum
helpviewer_keywords: ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 106c052c41962d4881ed88a9a7fa69a506119bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenum-interface1"></a><span data-ttu-id="94fbb-102">ICorDebugModuleEnum интерфейс1</span><span class="sxs-lookup"><span data-stu-id="94fbb-102">ICorDebugModuleEnum Interface1</span></span>
<span data-ttu-id="94fbb-103">Реализует методы ICorDebugEnum и выполняет перечисление массивов ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="94fbb-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94fbb-104">Методы</span><span class="sxs-lookup"><span data-stu-id="94fbb-104">Methods</span></span>  
  
|<span data-ttu-id="94fbb-105">Метод</span><span class="sxs-lookup"><span data-stu-id="94fbb-105">Method</span></span>|<span data-ttu-id="94fbb-106">Описание</span><span class="sxs-lookup"><span data-stu-id="94fbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94fbb-107">Метод Next</span><span class="sxs-lookup"><span data-stu-id="94fbb-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="94fbb-108">Возвращает заданное число `ICorDebugModule` экземпляров из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="94fbb-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94fbb-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="94fbb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94fbb-110">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="94fbb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94fbb-111">Требования</span><span class="sxs-lookup"><span data-stu-id="94fbb-111">Requirements</span></span>  
 <span data-ttu-id="94fbb-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94fbb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94fbb-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94fbb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94fbb-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94fbb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94fbb-115">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94fbb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94fbb-116">См. также</span><span class="sxs-lookup"><span data-stu-id="94fbb-116">See Also</span></span>  
 [<span data-ttu-id="94fbb-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="94fbb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)