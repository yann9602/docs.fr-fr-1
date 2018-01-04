---
title: "ISymENCUnmanagedMethod::GetLineFromOffset, méthode"
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
ms.workload: dotnet
ms.openlocfilehash: 535c0310a3220c5691f26c9081f6d2f747196e91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="3d5fb-102">ISymENCUnmanagedMethod::GetLineFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="3d5fb-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="3d5fb-103">Obtient les informations de ligne associées à un offset.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="3d5fb-104">Si le paramètre d’offset (`dwOffset`) n’est pas un point de séquence, cette méthode obtient les informations de ligne associées à l’offset précédent.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d5fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d5fb-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d5fb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d5fb-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="3d5fb-107">[in] Un `ULONG32` qui contient le décalage.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="3d5fb-108">[out] Un pointeur vers un `ULONG32` qui reçoit la ligne.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="3d5fb-109">[out] Un pointeur vers un `ULONG32` qui reçoit la colonne.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="3d5fb-110">[out] Un pointeur vers un `ULONG32` qui reçoit la ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="3d5fb-111">[out] Un pointeur vers un `ULONG32` qui reçoit la colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="3d5fb-112">[out] Un pointeur vers un `ULONG32` qui reçoit le point de séquence associé.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d5fb-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3d5fb-113">Return Value</span></span>  
 <span data-ttu-id="3d5fb-114">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3d5fb-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d5fb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d5fb-115">Requirements</span></span>  
 <span data-ttu-id="3d5fb-116">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3d5fb-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d5fb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d5fb-117">See Also</span></span>  
 [<span data-ttu-id="3d5fb-118">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="3d5fb-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
