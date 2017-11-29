---
title: "Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fabf42c16dc41e29ca3d14e00e76797fa8f2a9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a><span data-ttu-id="f5ded-102">Метод ICLRDomainManager::SetPropertiesForDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="f5ded-102">ICLRDomainManager::SetPropertiesForDefaultAppDomain Method</span></span>
<span data-ttu-id="f5ded-103">Задает свойства, которые будут использоваться для инициализации домена приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5ded-103">Sets properties that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5ded-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f5ded-104">Syntax</span></span>  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5ded-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f5ded-105">Parameters</span></span>  
 `nProperties`  
 <span data-ttu-id="f5ded-106">[in] Количество записей в `pwszPropertyNames` и `pwszPropertyValues`.</span><span class="sxs-lookup"><span data-stu-id="f5ded-106">[in] The number of entries in `pwszPropertyNames` and `pwszPropertyValues`.</span></span>  
  
 `pwszPropertyNames`  
 <span data-ttu-id="f5ded-107">[in] Массив имен свойств или значение null, если нет свойств.</span><span class="sxs-lookup"><span data-stu-id="f5ded-107">[in] An array of property names, or null if there are no properties.</span></span> <span data-ttu-id="f5ded-108">В настоящее время только одно свойство, принимаются этот метод называется «PARTIAL_TRUST_VISIBLE_ASSEMBLIES».</span><span class="sxs-lookup"><span data-stu-id="f5ded-108">Currently, the only property name that is recognized by this method is "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".</span></span>  
  
 `pwszPropertyValues`  
 <span data-ttu-id="f5ded-109">[in] Массив значений свойств, или значение null, если нет свойств.</span><span class="sxs-lookup"><span data-stu-id="f5ded-109">[in] An array of property values, or null if there are no properties.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5ded-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f5ded-110">Return Value</span></span>  
 <span data-ttu-id="f5ded-111">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="f5ded-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f5ded-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5ded-112">HRESULT</span></span>|<span data-ttu-id="f5ded-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f5ded-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5ded-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5ded-114">S_OK</span></span>|<span data-ttu-id="f5ded-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f5ded-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5ded-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span><span class="sxs-lookup"><span data-stu-id="f5ded-116">HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)</span></span>|<span data-ttu-id="f5ded-117">`pwszPropertyNames`содержит имя свойства, которое не распознается этим методом.</span><span class="sxs-lookup"><span data-stu-id="f5ded-117">`pwszPropertyNames` includes a property name that is not recognized by this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5ded-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="f5ded-118">Remarks</span></span>  
 <span data-ttu-id="f5ded-119">Значение свойства для «PARTIAL_TRUST_VISIBLE_ASSEMBLIES» приведен список сборок, содержащих условной <xref:System.Security.AllowPartiallyTrustedCallersAttribute> атрибут (APTCA) с <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> флаг, который будут сделаны видимыми для частично доверенным вызывающим объектам в приложении по умолчанию домен.</span><span class="sxs-lookup"><span data-stu-id="f5ded-119">The property value for "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" is a list of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute with the <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flag, which are to be made visible to partially trusted callers in the default application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5ded-120">Требования</span><span class="sxs-lookup"><span data-stu-id="f5ded-120">Requirements</span></span>  
 <span data-ttu-id="f5ded-121">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5ded-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5ded-122">**Заголовок:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f5ded-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f5ded-123">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5ded-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5ded-124">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5ded-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ded-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f5ded-125">See Also</span></span>  
 [<span data-ttu-id="f5ded-126">Размещение</span><span class="sxs-lookup"><span data-stu-id="f5ded-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="f5ded-127">Iclrdomainmanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="f5ded-127">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)