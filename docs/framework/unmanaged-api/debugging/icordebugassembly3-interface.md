---
title: "Интерфейс ICorDebugAssembly3"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="9957d-102">Интерфейс ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="9957d-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="9957d-103">Логически расширяет интерфейс ICorDebugAssembly для обеспечения поддержки контейнерных сборок и их вложенных сборок.</span><span class="sxs-lookup"><span data-stu-id="9957d-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9957d-104">Методы</span><span class="sxs-lookup"><span data-stu-id="9957d-104">Methods</span></span>  
  
|<span data-ttu-id="9957d-105">Метод</span><span class="sxs-lookup"><span data-stu-id="9957d-105">Method</span></span>|<span data-ttu-id="9957d-106">Описание</span><span class="sxs-lookup"><span data-stu-id="9957d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9957d-107">Метод EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="9957d-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="9957d-108">Получает перечислитель для сборок, содержащихся в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="9957d-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="9957d-109">Метод GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="9957d-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="9957d-110">Возвращает контейнерную сборку этого объекта `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="9957d-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9957d-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="9957d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9957d-112">Этот интерфейс доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="9957d-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="9957d-113">Попытка вызова метода `QueryInterface` для получения указателя интерфейса возвращает `E_NOINTERFACE` для сценариев ICorDebug вне .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9957d-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9957d-114">Требования</span><span class="sxs-lookup"><span data-stu-id="9957d-114">Requirements</span></span>  
 <span data-ttu-id="9957d-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9957d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9957d-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9957d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9957d-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9957d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9957d-118">**Версии платформы .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9957d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9957d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="9957d-119">See Also</span></span>  
 [<span data-ttu-id="9957d-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9957d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9957d-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="9957d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)