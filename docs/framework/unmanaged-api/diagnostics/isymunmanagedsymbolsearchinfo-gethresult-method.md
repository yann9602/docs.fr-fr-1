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
ms.openlocfilehash: 42f2e0053a83d4ef7414791626ec204671429a3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="0d8a5-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="0d8a5-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="0d8a5-103">Obtient la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0d8a5-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d8a5-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d8a5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0d8a5-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="0d8a5-106">[out] Pointeur vers la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0d8a5-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d8a5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0d8a5-107">Return Value</span></span>  
 <span data-ttu-id="0d8a5-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0d8a5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d8a5-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0d8a5-109">Requirements</span></span>  
 <span data-ttu-id="0d8a5-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0d8a5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8a5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d8a5-111">See Also</span></span>  
 [<span data-ttu-id="0d8a5-112">ISymUnmanagedSymbolSearchInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="0d8a5-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
