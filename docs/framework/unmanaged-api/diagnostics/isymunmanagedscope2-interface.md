---
title: ISymUnmanagedScope2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2
helpviewer_keywords: ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d2ec846a34b2d3424f7bf8b54f1d4d12d4102e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="13124-102">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="13124-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="13124-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="13124-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="13124-104">Cette interface étend la [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface avec des méthodes qui obtiennent des informations sur les constantes définies dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="13124-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13124-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="13124-105">Methods</span></span>  
  
|<span data-ttu-id="13124-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="13124-106">Method</span></span>|<span data-ttu-id="13124-107">Description</span><span class="sxs-lookup"><span data-stu-id="13124-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13124-108">GetConstantCount, méthode</span><span class="sxs-lookup"><span data-stu-id="13124-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="13124-109">Obtient le nombre de l’une des constantes définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="13124-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="13124-110">GetConstants, méthode</span><span class="sxs-lookup"><span data-stu-id="13124-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="13124-111">Obtient les variables constantes définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="13124-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13124-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13124-112">Requirements</span></span>  
 <span data-ttu-id="13124-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13124-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13124-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13124-114">See Also</span></span>  
 [<span data-ttu-id="13124-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="13124-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="13124-116">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="13124-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
