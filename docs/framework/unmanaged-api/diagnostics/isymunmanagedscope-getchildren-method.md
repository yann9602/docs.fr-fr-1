---
title: "ISymUnmanagedScope::GetChildren, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetChildren
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2259eccc3be68f562a0c5b00ffe7fd47bad9a238
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="61565-102">ISymUnmanagedScope::GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="61565-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="61565-103">Obtient les enfants de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="61565-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61565-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61565-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61565-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61565-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="61565-106">[in] A `ULONG32` qui indique la taille de la `children` tableau.</span><span class="sxs-lookup"><span data-stu-id="61565-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="61565-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les enfants.</span><span class="sxs-lookup"><span data-stu-id="61565-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="61565-108">[out] Le tableau retourné d’enfants.</span><span class="sxs-lookup"><span data-stu-id="61565-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61565-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="61565-109">Return Value</span></span>  
 <span data-ttu-id="61565-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="61565-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61565-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61565-111">Requirements</span></span>  
 <span data-ttu-id="61565-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61565-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61565-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61565-113">See Also</span></span>  
 [<span data-ttu-id="61565-114">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="61565-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="61565-115">GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="61565-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)
