---
title: "ISymUnmanagedDispose::Destroy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDispose.Destroy
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d418bbb476fea306bf9ad92ce2b30d558627009
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="690a9-102">ISymUnmanagedDispose::Destroy, méthode</span><span class="sxs-lookup"><span data-stu-id="690a9-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="690a9-103">Provoque l’objet sous-jacent libérer toutes les références internes et retourne un échec sur tous les appels de méthode suivants.</span><span class="sxs-lookup"><span data-stu-id="690a9-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="690a9-104">Syntax</span></span>  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="690a9-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="690a9-105">Return Value</span></span>  
 <span data-ttu-id="690a9-106">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="690a9-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690a9-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="690a9-107">Requirements</span></span>  
 <span data-ttu-id="690a9-108">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="690a9-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690a9-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="690a9-109">See Also</span></span>  
 [<span data-ttu-id="690a9-110">ISymUnmanagedDispose, interface</span><span class="sxs-lookup"><span data-stu-id="690a9-110">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)
