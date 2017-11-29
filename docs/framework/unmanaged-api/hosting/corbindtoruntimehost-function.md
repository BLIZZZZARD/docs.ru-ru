---
title: "Функция CorBindToRuntimeHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeHost
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeHost
helpviewer_keywords: CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type: apiref
caps.latest.revision: "28"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eff6fdf0294e3b1cc9830e58bc8103a64102d5b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimehost-function"></a><span data-ttu-id="b1aec-102">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="b1aec-102">CorBindToRuntimeHost Function</span></span>
<span data-ttu-id="b1aec-103">Позволяет узлам загружать в процесс заданную версию среды common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b1aec-103">Enables hosts to load a specified version of the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="b1aec-104">Эта функция рекомендуется к использованию в [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1aec-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1aec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1aec-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1aec-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b1aec-106">Parameters</span></span>  
 `pwszVersion`  
 <span data-ttu-id="b1aec-107">[in] Строка, описывающая версию среды CLR, которую требуется загрузить.</span><span class="sxs-lookup"><span data-stu-id="b1aec-107">[in] A string that describes the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="b1aec-108">Номер версии платформы .NET Framework состоит из четырех частей, разделенных точками: *major.minor.build.revision*.</span><span class="sxs-lookup"><span data-stu-id="b1aec-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="b1aec-109">Строка, переданная как `pwszVersion` должно начинаться с символа «v», следуют первые три части номера версии (например, «v1.0.1529»).</span><span class="sxs-lookup"><span data-stu-id="b1aec-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="b1aec-110">Некоторые версии среды CLR устанавливаются с помощью оператора политики, указывающее, совместимость с предыдущими версиями среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b1aec-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="b1aec-111">По умолчанию оболочка загрузки проверяет `pwszVersion` от инструкции политики и загружает последнюю версию среды выполнения, которая совместима со запрашиваемой.</span><span class="sxs-lookup"><span data-stu-id="b1aec-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="b1aec-112">Основное приложение может вынудить оболочку пропустить оценку политики и загрузить точное версия, указанная в `pwszVersion` , передавая значение STARTUP_LOADER_SAFEMODE для `startupFlags` параметра.</span><span class="sxs-lookup"><span data-stu-id="b1aec-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of STARTUP_LOADER_SAFEMODE for the `startupFlags` parameter.</span></span>  
  
 <span data-ttu-id="b1aec-113">Если `pwszVersion` — `null,` метод не загружает все версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b1aec-113">If `pwszVersion` is `null,` the method does not load any version of the CLR.</span></span> <span data-ttu-id="b1aec-114">Вместо этого он возвращает CLR_E_SHIM_RUNTIMELOAD, который указывает, что не удалось загрузить среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="b1aec-114">Instead, it returns CLR_E_SHIM_RUNTIMELOAD, which indicates that it failed to load the runtime.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="b1aec-115">[in] Строка, указывающая, следует ли загружать сервера или рабочей станции сборки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b1aec-115">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="b1aec-116">Допустимые значения: `svr` и `wks`.</span><span class="sxs-lookup"><span data-stu-id="b1aec-116">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="b1aec-117">Построение сервера оптимизировано для использования нескольких процессоров для сборки мусора, а построение рабочей станции оптимизировано для клиентских приложений на однопроцессорного компьютера.</span><span class="sxs-lookup"><span data-stu-id="b1aec-117">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="b1aec-118">Если `pwszBuildFlavor` имеет значение null, загружается построение рабочей станции.</span><span class="sxs-lookup"><span data-stu-id="b1aec-118">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="b1aec-119">На компьютере одним процессором всегда загружается построение рабочей станции, даже если `pwszBuildFlavor` равно `svr`.</span><span class="sxs-lookup"><span data-stu-id="b1aec-119">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="b1aec-120">Тем не менее если `pwszBuildFlavor` равно `svr` и указывается параллельная сборка мусора (см. в описании `startupFlags` параметра), загружается построение сервера.</span><span class="sxs-lookup"><span data-stu-id="b1aec-120">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `startupFlags` parameter), the server build is loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1aec-121">Параллельная сборка мусора не поддерживается в приложениях, выполняемых WOW64 x86 эмулятора на 64-разрядных системах, которые реализуют архитектуру Intel Itanium (прежнее название — IA-64).</span><span class="sxs-lookup"><span data-stu-id="b1aec-121">Concurrent garbage collection is not supported in applications running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="b1aec-122">Дополнительные сведения об использовании WOW64 в 64-разрядных систем Windows см. в разделе [под управлением 32-разрядных приложений](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="b1aec-122">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>  
  
 `pwszHostConfigFile`  
 <span data-ttu-id="b1aec-123">[in] Имя файла конфигурации узла, который указывает версию среды CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="b1aec-123">[in] The name of a host configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="b1aec-124">Если имя файла не включает полный путь, предполагается, что файл находится в том же каталоге, что исполняемый объект, который выполняет вызов.</span><span class="sxs-lookup"><span data-stu-id="b1aec-124">If the file name does not include a fully qualified path, the file is assumed to be in the same directory as the executable that is making the call.</span></span>  
  
 `pReserved`  
 <span data-ttu-id="b1aec-125">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="b1aec-125">[in] Reserved for future extensibility.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="b1aec-126">[in] Набор флагов, определяющих параллельная сборка мусора, независимый от домена код и поведение `pwszVersion` параметра.</span><span class="sxs-lookup"><span data-stu-id="b1aec-126">[in] A set of flags that controls concurrent garbage collection, domain-neutral code, and the behavior of the `pwszVersion` parameter.</span></span> <span data-ttu-id="b1aec-127">Значение по умолчанию — один домен, если не установлен флаг.</span><span class="sxs-lookup"><span data-stu-id="b1aec-127">The default is single domain if no flag is set.</span></span> <span data-ttu-id="b1aec-128">Список поддерживаемых значений см. в разделе [STARTUP_FLAGS-перечисление](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b1aec-128">For a list of supported values, see the [STARTUP_FLAGS enumeration](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b1aec-129">[in] `CLSID` Компонентного класса, который реализует или [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) или [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) интерфейса.</span><span class="sxs-lookup"><span data-stu-id="b1aec-129">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b1aec-130">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b1aec-130">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b1aec-131">[in] `IID` Интерфейса, для которого запрашивается.</span><span class="sxs-lookup"><span data-stu-id="b1aec-131">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="b1aec-132">Поддерживаемыми значениями являются IID_ICorRuntimeHost и IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="b1aec-132">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b1aec-133">[out] Указатель интерфейса на версию среды выполнения, который был загружен.</span><span class="sxs-lookup"><span data-stu-id="b1aec-133">[out] An interface pointer to the version of the runtime that was loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1aec-134">Требования</span><span class="sxs-lookup"><span data-stu-id="b1aec-134">Requirements</span></span>  
 <span data-ttu-id="b1aec-135">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1aec-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1aec-136">**Заголовок:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="b1aec-136">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="b1aec-137">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1aec-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1aec-138">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1aec-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1aec-139">См. также</span><span class="sxs-lookup"><span data-stu-id="b1aec-139">See Also</span></span>  
 [<span data-ttu-id="b1aec-140">Corbindtocurrentruntime-функция</span><span class="sxs-lookup"><span data-stu-id="b1aec-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="b1aec-141">CorBindToRuntime-функция</span><span class="sxs-lookup"><span data-stu-id="b1aec-141">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="b1aec-142">CorBindToRuntimeByCfg-функция</span><span class="sxs-lookup"><span data-stu-id="b1aec-142">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="b1aec-143">CorBindToRuntimeEx-функция</span><span class="sxs-lookup"><span data-stu-id="b1aec-143">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="b1aec-144">ICorRuntimeHost-интерфейс</span><span class="sxs-lookup"><span data-stu-id="b1aec-144">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="b1aec-145">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="b1aec-145">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)