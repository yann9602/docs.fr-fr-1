---
title: "ISymUnmanagedScope::GetStartOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e24924607cad1922f2d1b5a816dc635eb6c7820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="f35ea-102">ISymUnmanagedScope::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="f35ea-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="f35ea-103">Obtient l’offset de début pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="f35ea-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f35ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f35ea-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f35ea-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f35ea-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f35ea-106">[out] Un pointeur vers un `ULONG32` qui contient l’offset de démarrage.</span><span class="sxs-lookup"><span data-stu-id="f35ea-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f35ea-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f35ea-107">Return Value</span></span>  
 <span data-ttu-id="f35ea-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f35ea-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f35ea-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f35ea-109">Requirements</span></span>  
 <span data-ttu-id="f35ea-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f35ea-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35ea-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f35ea-111">See Also</span></span>  
 [<span data-ttu-id="f35ea-112">ISymUnmanagedScope (Interface)</span><span class="sxs-lookup"><span data-stu-id="f35ea-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="f35ea-113">GetEndOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="f35ea-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
