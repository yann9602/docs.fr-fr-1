---
title: "ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4987aeff8a5006bad93db72a04c4195b40ab1a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="ec3c0-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="ec3c0-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="ec3c0-103">Obtient la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ec3c0-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec3c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec3c0-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec3c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec3c0-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="ec3c0-106">[out] Pointeur vers la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="ec3c0-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec3c0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ec3c0-107">Return Value</span></span>  
 <span data-ttu-id="ec3c0-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ec3c0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec3c0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec3c0-109">Requirements</span></span>  
 <span data-ttu-id="ec3c0-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ec3c0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3c0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec3c0-111">See Also</span></span>  
 [<span data-ttu-id="ec3c0-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="ec3c0-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
