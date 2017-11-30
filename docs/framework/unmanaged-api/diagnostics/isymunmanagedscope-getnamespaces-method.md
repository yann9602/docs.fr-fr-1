---
title: "ISymUnmanagedScope::GetNamespaces, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 641ce6c4587f9f23743a3c1b5a1aeb6fb77edde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="69c95-102">ISymUnmanagedScope::GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="69c95-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="69c95-103">Obtient les espaces de noms qui sont utilisés dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="69c95-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69c95-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69c95-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69c95-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="69c95-106">[in] Taille du tableau `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="69c95-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="69c95-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="69c95-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="69c95-108">[out] Tableau qui reçoit les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="69c95-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69c95-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="69c95-109">Return Value</span></span>  
 <span data-ttu-id="69c95-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="69c95-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c95-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="69c95-111">Requirements</span></span>  
 <span data-ttu-id="69c95-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69c95-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c95-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69c95-113">See Also</span></span>  
 [<span data-ttu-id="69c95-114">ISymUnmanagedScope (Interface)</span><span class="sxs-lookup"><span data-stu-id="69c95-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
