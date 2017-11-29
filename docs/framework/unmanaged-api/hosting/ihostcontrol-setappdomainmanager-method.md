---
title: "Метод IHostControl::SetAppDomainManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.SetAppDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97e853bc74babca5b5400953b63714a13419fcaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="8889a-102">Метод IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="8889a-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="8889a-103">Уведомляет узел, что домен приложения был создан.</span><span class="sxs-lookup"><span data-stu-id="8889a-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8889a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8889a-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8889a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="8889a-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="8889a-106">[in] Числовой идентификатор выбранного <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8889a-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="8889a-107">[in] Указатель на <xref:System.AppDomainManager> объект, реализующий узел как `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="8889a-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8889a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8889a-108">Return Value</span></span>  
  
|<span data-ttu-id="8889a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8889a-109">HRESULT</span></span>|<span data-ttu-id="8889a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="8889a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8889a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8889a-111">S_OK</span></span>|<span data-ttu-id="8889a-112">`SetAppDomainManager`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="8889a-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="8889a-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8889a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8889a-114">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="8889a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8889a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8889a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8889a-116">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="8889a-116">The call timed out.</span></span>|  
|<span data-ttu-id="8889a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8889a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8889a-118">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="8889a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8889a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8889a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8889a-120">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="8889a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8889a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8889a-121">E_FAIL</span></span>|<span data-ttu-id="8889a-122">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="8889a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8889a-123">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="8889a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8889a-124">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8889a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8889a-125">Примечания</span><span class="sxs-lookup"><span data-stu-id="8889a-125">Remarks</span></span>  
 <span data-ttu-id="8889a-126"><xref:System.AppDomainManager> Предоставляет механизм для начальной загрузки в управляемый код и управлять созданием и параметры для каждого узла <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="8889a-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="8889a-127"><xref:System.AppDomainManager> Загружается в каждом <xref:System.AppDomain> при, <xref:System.AppDomain> создается.</span><span class="sxs-lookup"><span data-stu-id="8889a-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="8889a-128">Если это предусмотрено, среда CLR Уведомляет основное приложение создания домена приложения, задав значение `pUnkAppDomainManager` параметра.</span><span class="sxs-lookup"><span data-stu-id="8889a-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="8889a-129">В своей реализации `SetAppDomainManager` метод, узел может задать имя сборки и тип для домена приложения.</span><span class="sxs-lookup"><span data-stu-id="8889a-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8889a-130">Требования</span><span class="sxs-lookup"><span data-stu-id="8889a-130">Requirements</span></span>  
 <span data-ttu-id="8889a-131">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8889a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8889a-132">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8889a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8889a-133">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8889a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8889a-134">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8889a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8889a-135">См. также</span><span class="sxs-lookup"><span data-stu-id="8889a-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="8889a-136">IHostControl-интерфейс</span><span class="sxs-lookup"><span data-stu-id="8889a-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)