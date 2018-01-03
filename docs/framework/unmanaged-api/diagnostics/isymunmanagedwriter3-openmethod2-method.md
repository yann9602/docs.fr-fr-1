---
title: "ISymUnmanagedWriter3::OpenMethod2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="b6b5c-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="b6b5c-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="b6b5c-103">Ouvre une méthode et fournit sa vraie section compensée dans l’image.</span><span class="sxs-lookup"><span data-stu-id="b6b5c-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b5c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6b5c-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6b5c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6b5c-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="b6b5c-106">[in] Le jeton de métadonnées pour la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="b6b5c-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="b6b5c-107">[in] Le décalage de la section dans l’image.</span><span class="sxs-lookup"><span data-stu-id="b6b5c-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="b6b5c-108">[in] Le décalage de l’image.</span><span class="sxs-lookup"><span data-stu-id="b6b5c-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6b5c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6b5c-109">Return Value</span></span>  
 <span data-ttu-id="b6b5c-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b6b5c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b5c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b6b5c-111">Requirements</span></span>  
 <span data-ttu-id="b6b5c-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b6b5c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b5c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6b5c-113">See Also</span></span>  
 [<span data-ttu-id="b6b5c-114">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="b6b5c-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="b6b5c-115">OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="b6b5c-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
