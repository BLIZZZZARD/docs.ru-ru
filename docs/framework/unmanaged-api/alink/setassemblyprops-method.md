---
title: "Метод SetAssemblyProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0245b6b1e30174bb3496d3d6ab674ccc00fb9fee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="e57f1-102">Метод SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="e57f1-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="e57f1-103">Назначает свойства на уровне сборки.</span><span class="sxs-lookup"><span data-stu-id="e57f1-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57f1-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e57f1-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e57f1-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="e57f1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e57f1-106">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="e57f1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e57f1-107">Файл, определяющий свойство.</span><span class="sxs-lookup"><span data-stu-id="e57f1-107">File that defines the property.</span></span> <span data-ttu-id="e57f1-108">Может иметь значение NULL, если `AssemblyID` не указывает на несвязанный NETMODULE-файл.</span><span class="sxs-lookup"><span data-stu-id="e57f1-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="e57f1-109">Указывает возможность изменить.</span><span class="sxs-lookup"><span data-stu-id="e57f1-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="e57f1-110">Новое значение параметра.</span><span class="sxs-lookup"><span data-stu-id="e57f1-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e57f1-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e57f1-111">Return Value</span></span>  
 <span data-ttu-id="e57f1-112">Возвращает значение S_OK, если метод выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="e57f1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e57f1-113">Требования</span><span class="sxs-lookup"><span data-stu-id="e57f1-113">Requirements</span></span>  
 <span data-ttu-id="e57f1-114">Требуется alink.h.</span><span class="sxs-lookup"><span data-stu-id="e57f1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57f1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="e57f1-115">See Also</span></span>  
 [<span data-ttu-id="e57f1-116">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="e57f1-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e57f1-117">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="e57f1-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e57f1-118">ALink-интерфейс API</span><span class="sxs-lookup"><span data-stu-id="e57f1-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)