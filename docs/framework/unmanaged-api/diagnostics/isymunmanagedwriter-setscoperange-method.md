---
title: "Метод ISymUnmanagedWriter::SetScopeRange"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b86df423d53c9fa3a738c603d6cc575add594cae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="e20dd-102">Метод ISymUnmanagedWriter::SetScopeRange</span><span class="sxs-lookup"><span data-stu-id="e20dd-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="e20dd-103">Определяет диапазон смещений для заданной лексической области видимости.</span><span class="sxs-lookup"><span data-stu-id="e20dd-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="e20dd-104">Область становится новой текущей областью и помещается в стек областей.</span><span class="sxs-lookup"><span data-stu-id="e20dd-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="e20dd-105">Области должны образовывать иерархию.</span><span class="sxs-lookup"><span data-stu-id="e20dd-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="e20dd-106">Перекрытие элементов с общим родителем запрещено.</span><span class="sxs-lookup"><span data-stu-id="e20dd-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20dd-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e20dd-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e20dd-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="e20dd-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="e20dd-109">[in] Идентификатор области для области.</span><span class="sxs-lookup"><span data-stu-id="e20dd-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="e20dd-110">[in] Смещение в байтах первой инструкции в лексической области видимости от начала метода.</span><span class="sxs-lookup"><span data-stu-id="e20dd-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="e20dd-111">[in] Смещение в байтах последней инструкции в лексической области видимости от начала метода.</span><span class="sxs-lookup"><span data-stu-id="e20dd-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e20dd-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e20dd-112">Return Value</span></span>  
 <span data-ttu-id="e20dd-113">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="e20dd-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e20dd-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="e20dd-114">Remarks</span></span>  
 <span data-ttu-id="e20dd-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) возвращает непрозрачный идентификатор области, можно использовать с `ISymUnmanagedWriter::SetScopeRange` для определения области начального и конечного смещения в дальнейшем.</span><span class="sxs-lookup"><span data-stu-id="e20dd-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="e20dd-116">В этом случае смещения, переданные методам `ISymUnmanagedWriter::OpenScope` и [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) игнорируются.</span><span class="sxs-lookup"><span data-stu-id="e20dd-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="e20dd-117">Идентификаторы областей действительны только в текущем методе.</span><span class="sxs-lookup"><span data-stu-id="e20dd-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e20dd-118">Требования</span><span class="sxs-lookup"><span data-stu-id="e20dd-118">Requirements</span></span>  
 <span data-ttu-id="e20dd-119">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e20dd-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20dd-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e20dd-120">See Also</span></span>  
 [<span data-ttu-id="e20dd-121">ISymUnmanagedWriter-интерфейс</span><span class="sxs-lookup"><span data-stu-id="e20dd-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)