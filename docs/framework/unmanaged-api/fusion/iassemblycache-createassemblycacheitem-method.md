---
title: "Метод IAssemblyCache::CreateAssemblyCacheItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.CreateAssemblyCacheItem
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84291d3dea34aba43889baeb1f6e3d501f71b782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="77667-102">Метод IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="77667-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="77667-103">Возвращает ссылку на новый [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) объекта.</span><span class="sxs-lookup"><span data-stu-id="77667-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77667-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77667-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77667-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="77667-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="77667-106">[in] Флаги, определенные в Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="77667-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="77667-107">Поддерживаются следующие значения:</span><span class="sxs-lookup"><span data-stu-id="77667-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="77667-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="77667-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="77667-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="77667-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="77667-110">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="77667-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="77667-111">`pvReserved`должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="77667-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="77667-112">[out] Возвращенный `IAssemblyCacheItem` указателя.</span><span class="sxs-lookup"><span data-stu-id="77667-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="77667-113">[in, необязательно] Uncanonicalized, разделенных запятыми `name=value` пары.</span><span class="sxs-lookup"><span data-stu-id="77667-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77667-114">Требования</span><span class="sxs-lookup"><span data-stu-id="77667-114">Requirements</span></span>  
 <span data-ttu-id="77667-115">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77667-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77667-116">**Заголовок:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="77667-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="77667-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77667-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77667-118">См. также</span><span class="sxs-lookup"><span data-stu-id="77667-118">See Also</span></span>  
 [<span data-ttu-id="77667-119">Интерфейс IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="77667-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="77667-120">IAssemblyCacheItem-интерфейс</span><span class="sxs-lookup"><span data-stu-id="77667-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)