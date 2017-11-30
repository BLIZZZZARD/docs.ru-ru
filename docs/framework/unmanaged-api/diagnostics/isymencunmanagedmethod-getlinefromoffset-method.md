---
title: "Метод ISymENCUnmanagedMethod::GetLineFromOffset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="bef05-102">Метод ISymENCUnmanagedMethod::GetLineFromOffset</span><span class="sxs-lookup"><span data-stu-id="bef05-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="bef05-103">Возвращает сведения о строке, связанной со смещением.</span><span class="sxs-lookup"><span data-stu-id="bef05-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="bef05-104">Если параметр смещения (`dwOffset`) не является точкой следования, этот метод возвращает сведения о строке, связанные с предыдущим смещением.</span><span class="sxs-lookup"><span data-stu-id="bef05-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bef05-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bef05-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bef05-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bef05-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="bef05-107">[in] Объект `ULONG32` , содержащий смещение.</span><span class="sxs-lookup"><span data-stu-id="bef05-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="bef05-108">[out] Указатель на `ULONG32` , принимающий строку.</span><span class="sxs-lookup"><span data-stu-id="bef05-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="bef05-109">[out] Указатель на `ULONG32` , получающий столбца.</span><span class="sxs-lookup"><span data-stu-id="bef05-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="bef05-110">[out] Указатель на `ULONG32` , получающий конца строки.</span><span class="sxs-lookup"><span data-stu-id="bef05-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="bef05-111">[out] Указатель на `ULONG32` , который получает конечный столбец.</span><span class="sxs-lookup"><span data-stu-id="bef05-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="bef05-112">[out] Указатель на `ULONG32` , получающий точка связанного последовательности.</span><span class="sxs-lookup"><span data-stu-id="bef05-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bef05-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="bef05-113">Return Value</span></span>  
 <span data-ttu-id="bef05-114">Значение S_OK, если метод выполнен успешно; в противном случае — значение E_FAIL или другим кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="bef05-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef05-115">Требования</span><span class="sxs-lookup"><span data-stu-id="bef05-115">Requirements</span></span>  
 <span data-ttu-id="bef05-116">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bef05-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef05-117">См. также</span><span class="sxs-lookup"><span data-stu-id="bef05-117">See Also</span></span>  
 [<span data-ttu-id="bef05-118">Интерфейс ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="bef05-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)