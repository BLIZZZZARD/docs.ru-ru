---
title: "Метод ICorDebugDataTarget2::GetImageLocation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d35e35ecf4dfc62575e42a45a861ad685f3f26b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="402af-102">Метод ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="402af-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="402af-103">Возвращает путь для модуля из базового адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="402af-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="402af-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="402af-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="402af-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="402af-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="402af-106">[in] Объект [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) значение, представляющее базовый адрес модуля.</span><span class="sxs-lookup"><span data-stu-id="402af-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="402af-107">[входной] Число символов в буфере, которые должен получить путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="402af-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="402af-108">[выходной] Указатель на число символов, записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="402af-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="402af-109">[выходной] Путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="402af-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="402af-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="402af-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="402af-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="402af-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="402af-112">Требования</span><span class="sxs-lookup"><span data-stu-id="402af-112">Requirements</span></span>  
 <span data-ttu-id="402af-113">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="402af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="402af-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="402af-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="402af-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="402af-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="402af-116">**Версии платформы .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="402af-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="402af-117">См. также</span><span class="sxs-lookup"><span data-stu-id="402af-117">See Also</span></span>  
 [<span data-ttu-id="402af-118">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="402af-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="402af-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="402af-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)