---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f8a89532999f599c8ec595fa709044b7d13a53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a><span data-ttu-id="1a673-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="1a673-102">ISymUnmanagedWriter5::CloseMapTokensToSourceSpans Method</span></span>
<span data-ttu-id="1a673-103">Fermez la section des données personnalisées spécifiques pour l’étendue de jeton vers la source des informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="1a673-103">Close the special custom data section for token-to-source span mapping information.</span></span> <span data-ttu-id="1a673-104">Après sa fermeture, aucun plus d’informations de mappage ne peut être ajouté.</span><span class="sxs-lookup"><span data-stu-id="1a673-104">After it is closed, no more mapping information can be added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a673-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a673-105">Syntax</span></span>  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1a673-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a673-106">Return Value</span></span>  
 <span data-ttu-id="1a673-107">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1a673-107">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a673-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a673-108">Requirements</span></span>  
 <span data-ttu-id="1a673-109">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1a673-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a673-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a673-110">See Also</span></span>  
 [<span data-ttu-id="1a673-111">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="1a673-111">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
