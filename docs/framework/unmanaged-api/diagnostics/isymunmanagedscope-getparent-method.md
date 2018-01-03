---
title: "ISymUnmanagedScope::GetParent, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetParent
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1defb0f95ed38d8dbe5d47d804e340b3ca35a79c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="2d5d6-102">ISymUnmanagedScope::GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="2d5d6-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="2d5d6-103">Obtient la portée parent de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="2d5d6-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d5d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d5d6-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d5d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d5d6-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2d5d6-106">[out] Un pointeur vers retourné [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="2d5d6-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d5d6-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d5d6-107">Return Value</span></span>  
 <span data-ttu-id="2d5d6-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2d5d6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d5d6-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d5d6-109">Requirements</span></span>  
 <span data-ttu-id="2d5d6-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2d5d6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5d6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d5d6-111">See Also</span></span>  
 [<span data-ttu-id="2d5d6-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="2d5d6-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="2d5d6-113">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="2d5d6-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
