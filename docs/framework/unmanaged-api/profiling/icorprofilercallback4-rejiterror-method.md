---
title: "Метод ICorProfilerCallback4::ReJITError"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8b1f3c5b206b2e6a108e784a206d597b69fd662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="b4339-102">Метод ICorProfilerCallback4::ReJITError</span><span class="sxs-lookup"><span data-stu-id="b4339-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="b4339-103">Уведомляет профилировщик, что компилятор just-in-time (JIT) произошла ошибка в процессе повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="b4339-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4339-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4339-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4339-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b4339-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="b4339-106">[in] `ModuleID` В которой была предпринята попытка сбой повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="b4339-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="b4339-107">[in] `MethodDef` Метода, в которой была предпринята попытка сбой повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="b4339-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="b4339-108">[in] Экземпляр функции, для которого создается перекомпилированные или отмечено для повторной компиляции.</span><span class="sxs-lookup"><span data-stu-id="b4339-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="b4339-109">Это значение может быть `NULL` Если ошибка для каждого метода в отдельности вместо отдельно для каждого экземпляра (например, если профилировщик указанный маркер недопустимые метаданные для повторной компиляции метода).</span><span class="sxs-lookup"><span data-stu-id="b4339-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b4339-110">[in] Значение HRESULT, указывающее причину сбоя.</span><span class="sxs-lookup"><span data-stu-id="b4339-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="b4339-111">В разделе значения HRESULT для состояния список значений.</span><span class="sxs-lookup"><span data-stu-id="b4339-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4339-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b4339-112">Return Value</span></span>  
 <span data-ttu-id="b4339-113">Значения, возвращаемые из этого обратного вызова, игнорируются.</span><span class="sxs-lookup"><span data-stu-id="b4339-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="b4339-114">Значения HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="b4339-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="b4339-115">Массив значений HRESULT для состояния</span><span class="sxs-lookup"><span data-stu-id="b4339-115">Status array HRESULT</span></span>|<span data-ttu-id="b4339-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b4339-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b4339-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b4339-117">E_INVALIDARG</span></span>|<span data-ttu-id="b4339-118">`moduleID` Или `methodDef` маркер `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b4339-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="b4339-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="b4339-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="b4339-120">Модуль еще не полностью загружен или находится в процессе выгрузки.</span><span class="sxs-lookup"><span data-stu-id="b4339-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="b4339-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="b4339-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="b4339-122">Указанный модуль был создан динамически (например, с `Reflection.Emit`) и поэтому не поддерживается этим методом.</span><span class="sxs-lookup"><span data-stu-id="b4339-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="b4339-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="b4339-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="b4339-124">Метод создается в собираемой сборке и таким образом, не может быть перекомпилирован.</span><span class="sxs-lookup"><span data-stu-id="b4339-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="b4339-125">Обратите внимание, что типы и функции, определенные в контексте, отличном от отражения (например, `List<MyCollectibleStruct>`) могут быть созданы в собираемая сборка.</span><span class="sxs-lookup"><span data-stu-id="b4339-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="b4339-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b4339-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b4339-127">Среда CLR не хватило памяти при попытке пометить указанный метод для перекомпиляции JIT.</span><span class="sxs-lookup"><span data-stu-id="b4339-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="b4339-128">Другой</span><span class="sxs-lookup"><span data-stu-id="b4339-128">Other</span></span>|<span data-ttu-id="b4339-129">Операционная система возвратила сбой за пределами среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b4339-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="b4339-130">Например сбой системного вызова изменения защиты доступа к странице памяти отображается ошибка операционной системы.</span><span class="sxs-lookup"><span data-stu-id="b4339-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4339-131">Требования</span><span class="sxs-lookup"><span data-stu-id="b4339-131">Requirements</span></span>  
 <span data-ttu-id="b4339-132">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4339-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4339-133">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4339-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4339-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4339-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4339-135">**Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4339-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4339-136">См. также</span><span class="sxs-lookup"><span data-stu-id="b4339-136">See Also</span></span>  
 [<span data-ttu-id="b4339-137">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="b4339-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b4339-138">Интерфейс ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="b4339-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)