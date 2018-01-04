---
title: "ISymUnmanagedScope::GetLocals, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocals
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 07d42423d284da39d40268727de13b4605221b5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="18360-102">ISymUnmanagedScope::GetLocals, méthode</span><span class="sxs-lookup"><span data-stu-id="18360-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="18360-103">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="18360-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18360-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18360-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18360-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18360-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="18360-106">[in] A `ULONG32` qui indique la taille de la `locals` tableau.</span><span class="sxs-lookup"><span data-stu-id="18360-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="18360-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les variables locales.</span><span class="sxs-lookup"><span data-stu-id="18360-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="18360-108">[out] Tableau qui reçoit les variables locales.</span><span class="sxs-lookup"><span data-stu-id="18360-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18360-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="18360-109">Return Value</span></span>  
 <span data-ttu-id="18360-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="18360-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18360-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18360-111">Requirements</span></span>  
 <span data-ttu-id="18360-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18360-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18360-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18360-113">See Also</span></span>  
 [<span data-ttu-id="18360-114">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="18360-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
