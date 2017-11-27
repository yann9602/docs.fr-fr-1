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
ms.openlocfilehash: 1124eac951e32dbf1cedb7926f582ec6abb99007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="6d864-102">ISymUnmanagedWriter3::OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="6d864-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="6d864-103">Ouvre une méthode et fournit sa vraie section compensée dans l’image.</span><span class="sxs-lookup"><span data-stu-id="6d864-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d864-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d864-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d864-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d864-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="6d864-106">[in] Le jeton de métadonnées pour la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="6d864-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="6d864-107">[in] Le décalage de la section dans l’image.</span><span class="sxs-lookup"><span data-stu-id="6d864-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="6d864-108">[in] Le décalage de l’image.</span><span class="sxs-lookup"><span data-stu-id="6d864-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d864-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6d864-109">Return Value</span></span>  
 <span data-ttu-id="6d864-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6d864-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d864-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6d864-111">Requirements</span></span>  
 <span data-ttu-id="6d864-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6d864-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d864-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d864-113">See Also</span></span>  
 [<span data-ttu-id="6d864-114">ISymUnmanagedWriter3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="6d864-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="6d864-115">OpenMethod (méthode)</span><span class="sxs-lookup"><span data-stu-id="6d864-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
