---
title: "ISymUnmanagedVariable::GetStartOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="31432-102">ISymUnmanagedVariable::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="31432-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="31432-103">Obtient l’offset de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="31432-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="31432-104">S’il s’agit d’une variable locale dans une portée, l’offset de début est compris dans les offsets définis pour la portée.</span><span class="sxs-lookup"><span data-stu-id="31432-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31432-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31432-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31432-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31432-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="31432-107">[out] Un pointeur vers un `ULONG32` qui reçoit l’offset de début.</span><span class="sxs-lookup"><span data-stu-id="31432-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31432-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31432-108">Return Value</span></span>  
 <span data-ttu-id="31432-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="31432-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31432-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="31432-110">Requirements</span></span>  
 <span data-ttu-id="31432-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31432-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31432-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31432-112">See Also</span></span>  
 [<span data-ttu-id="31432-113">ISymUnmanagedVariable (Interface)</span><span class="sxs-lookup"><span data-stu-id="31432-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="31432-114">GetEndOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="31432-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
