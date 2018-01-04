---
title: "ISymUnmanagedScope::GetEndOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64990dc2785a3804e683e281c823f459ec48e8a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="373c5-102">ISymUnmanagedScope::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="373c5-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="373c5-103">Obtient l’offset de fin pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="373c5-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="373c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="373c5-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="373c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="373c5-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="373c5-106">[out] Un pointeur vers un `ULONG32` qui reçoit l’offset de fin.</span><span class="sxs-lookup"><span data-stu-id="373c5-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="373c5-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="373c5-107">Return Value</span></span>  
 <span data-ttu-id="373c5-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="373c5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="373c5-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="373c5-109">Requirements</span></span>  
 <span data-ttu-id="373c5-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="373c5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="373c5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="373c5-111">See Also</span></span>  
 [<span data-ttu-id="373c5-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="373c5-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="373c5-113">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="373c5-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
