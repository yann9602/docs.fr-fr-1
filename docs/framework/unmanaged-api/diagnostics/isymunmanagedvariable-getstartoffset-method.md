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
ms.workload: dotnet
ms.openlocfilehash: b3fa0c710eb5de8b9a92970002336de22adb2458
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="d9c08-102">ISymUnmanagedVariable::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="d9c08-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="d9c08-103">Obtient l’offset de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="d9c08-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="d9c08-104">S’il s’agit d’une variable locale dans une portée, l’offset de début est compris dans les offsets définis pour la portée.</span><span class="sxs-lookup"><span data-stu-id="d9c08-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c08-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9c08-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9c08-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9c08-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d9c08-107">[out] Un pointeur vers un `ULONG32` qui reçoit l’offset de début.</span><span class="sxs-lookup"><span data-stu-id="d9c08-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9c08-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d9c08-108">Return Value</span></span>  
 <span data-ttu-id="d9c08-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d9c08-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9c08-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d9c08-110">Requirements</span></span>  
 <span data-ttu-id="d9c08-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d9c08-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c08-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9c08-112">See Also</span></span>  
 [<span data-ttu-id="d9c08-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="d9c08-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="d9c08-114">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="d9c08-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
