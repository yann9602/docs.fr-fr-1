---
title: "ISymUnmanagedMethod::GetNamespace, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2244229b50a9944cefb5804720198bf391fd0e6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="ea8bc-102">ISymUnmanagedMethod::GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="ea8bc-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="ea8bc-103">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="ea8bc-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea8bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea8bc-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea8bc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea8bc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ea8bc-106">[out] Un pointeur qui est défini à le [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="ea8bc-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea8bc-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea8bc-107">Return Value</span></span>  
 <span data-ttu-id="ea8bc-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ea8bc-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea8bc-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea8bc-109">Requirements</span></span>  
 <span data-ttu-id="ea8bc-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea8bc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8bc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea8bc-111">See Also</span></span>  
 [<span data-ttu-id="ea8bc-112">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="ea8bc-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
