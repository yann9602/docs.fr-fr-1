---
title: "ISymUnmanagedReader::GetVariables, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86a0f8ed0a73661b80a9a196682e9539a3b97141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="645a3-102">ISymUnmanagedReader::GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="645a3-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="645a3-103">Retourne une variable non locale, en fonction de son parent et son nom.</span><span class="sxs-lookup"><span data-stu-id="645a3-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="645a3-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="645a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="645a3-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="645a3-106">[in] Le parent de la variable.</span><span class="sxs-lookup"><span data-stu-id="645a3-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="645a3-107">[in] Taille du tableau `pVars`.</span><span class="sxs-lookup"><span data-stu-id="645a3-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="645a3-108">[out] Un pointeur vers la variable qui reçoit le nombre de variables retournées dans `pVars`.</span><span class="sxs-lookup"><span data-stu-id="645a3-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="645a3-109">[out] Pointeur vers la variable qui reçoit les variables.</span><span class="sxs-lookup"><span data-stu-id="645a3-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="645a3-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="645a3-110">Return Value</span></span>  
 <span data-ttu-id="645a3-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="645a3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="645a3-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="645a3-112">Requirements</span></span>  
 <span data-ttu-id="645a3-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="645a3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645a3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="645a3-114">See Also</span></span>  
 [<span data-ttu-id="645a3-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="645a3-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
