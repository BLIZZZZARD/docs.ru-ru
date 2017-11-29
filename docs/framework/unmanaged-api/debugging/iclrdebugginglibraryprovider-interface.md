---
title: "Интерфейс ICLRDebuggingLibraryProvider"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82ed352e3f5fb83a2f464f2d82ff9a9885227fe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="7cd54-102">Интерфейс ICLRDebuggingLibraryProvider</span><span class="sxs-lookup"><span data-stu-id="7cd54-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="7cd54-103">Включает в себя [метод ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) метод, получающий интерфейс обратного вызова, который позволяет среды выполнения от версии библиотеки отладки находить и загружать по требованию библиотеки поставщика.</span><span class="sxs-lookup"><span data-stu-id="7cd54-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7cd54-104">Методы</span><span class="sxs-lookup"><span data-stu-id="7cd54-104">Methods</span></span>  
  
|<span data-ttu-id="7cd54-105">Метод</span><span class="sxs-lookup"><span data-stu-id="7cd54-105">Method</span></span>|<span data-ttu-id="7cd54-106">Описание</span><span class="sxs-lookup"><span data-stu-id="7cd54-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7cd54-107">Метод ProvideLibrary</span><span class="sxs-lookup"><span data-stu-id="7cd54-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="7cd54-108">Позволяет отладчику предоставить дескриптор модуля, который может использоваться для загрузки библиотеки отладки.</span><span class="sxs-lookup"><span data-stu-id="7cd54-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cd54-109">Требования</span><span class="sxs-lookup"><span data-stu-id="7cd54-109">Requirements</span></span>  
 <span data-ttu-id="7cd54-110">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cd54-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cd54-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cd54-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cd54-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cd54-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cd54-113">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cd54-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd54-114">См. также</span><span class="sxs-lookup"><span data-stu-id="7cd54-114">See Also</span></span>  
 [<span data-ttu-id="7cd54-115">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7cd54-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7cd54-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="7cd54-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)