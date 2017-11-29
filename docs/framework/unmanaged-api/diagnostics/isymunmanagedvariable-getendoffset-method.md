---
title: "ISymUnmanagedVariable::GetEndOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="da186-102">ISymUnmanagedVariable::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="da186-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="da186-103">Obtient l’offset de fin de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="da186-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="da186-104">S’il s’agit d’une variable locale dans une portée, l’offset de fin est compris dans les offsets définis pour la portée.</span><span class="sxs-lookup"><span data-stu-id="da186-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da186-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da186-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da186-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da186-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="da186-107">[out] Un pointeur vers un `ULONG32` qui reçoit l’offset de fin.</span><span class="sxs-lookup"><span data-stu-id="da186-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da186-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="da186-108">Return Value</span></span>  
 <span data-ttu-id="da186-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="da186-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da186-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="da186-110">Requirements</span></span>  
 <span data-ttu-id="da186-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da186-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da186-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da186-112">See Also</span></span>  
 [<span data-ttu-id="da186-113">ISymUnmanagedVariable (Interface)</span><span class="sxs-lookup"><span data-stu-id="da186-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="da186-114">GetStartOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="da186-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
