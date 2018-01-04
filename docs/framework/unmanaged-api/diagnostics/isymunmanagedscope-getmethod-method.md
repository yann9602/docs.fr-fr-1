---
title: "ISymUnmanagedScope::GetMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4756ff1f373f09a96daa64c1fb01875274a6d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="18c76-102">ISymUnmanagedScope::GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="18c76-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="18c76-103">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="18c76-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18c76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18c76-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18c76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18c76-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="18c76-106">[out] Un pointeur vers retourné [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="18c76-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18c76-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="18c76-107">Return Value</span></span>  
 <span data-ttu-id="18c76-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="18c76-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18c76-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="18c76-109">Requirements</span></span>  
 <span data-ttu-id="18c76-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="18c76-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c76-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18c76-111">See Also</span></span>  
 [<span data-ttu-id="18c76-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="18c76-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
