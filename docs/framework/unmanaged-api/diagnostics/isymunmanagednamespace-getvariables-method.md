---
title: "ISymUnmanagedNamespace::GetVariables, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fcfeba065bcdc996b5bc742dfea33b4417a29f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="31d46-102">ISymUnmanagedNamespace::GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="31d46-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="31d46-103">Retourne toutes les variables définies dans une portée globale au sein de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="31d46-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31d46-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31d46-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31d46-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="31d46-106">[in] A `ULONG32` qui indique la taille de la `pVars` tableau.</span><span class="sxs-lookup"><span data-stu-id="31d46-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="31d46-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="31d46-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="31d46-108">[out] Pointeur vers une mémoire tampon qui contient les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="31d46-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31d46-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31d46-109">Return Value</span></span>  
 <span data-ttu-id="31d46-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="31d46-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31d46-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="31d46-111">Requirements</span></span>  
 <span data-ttu-id="31d46-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="31d46-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d46-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d46-113">See Also</span></span>  
 [<span data-ttu-id="31d46-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="31d46-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
