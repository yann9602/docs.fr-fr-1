---
title: ISymUnmanagedScope, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d25d62dd42e3e93124c9a3bd8945be265f192663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="887c5-102">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="887c5-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="887c5-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="887c5-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="887c5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="887c5-104">Methods</span></span>  
  
|<span data-ttu-id="887c5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="887c5-105">Method</span></span>|<span data-ttu-id="887c5-106">Description</span><span class="sxs-lookup"><span data-stu-id="887c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="887c5-107">GetChildren (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="887c5-108">Obtient les enfants de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="887c5-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="887c5-109">GetEndOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="887c5-110">Obtient l’offset de fin pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="887c5-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="887c5-111">GetLocalCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="887c5-112">Obtient le nombre de variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="887c5-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="887c5-113">GetLocals (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="887c5-114">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="887c5-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="887c5-115">GetMethod (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="887c5-116">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="887c5-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="887c5-117">GetNamespaces (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="887c5-118">Obtient les espaces de noms qui sont utilisés dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="887c5-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="887c5-119">GetParent (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="887c5-120">Obtient la portée parent de cette étendue.</span><span class="sxs-lookup"><span data-stu-id="887c5-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="887c5-121">GetStartOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="887c5-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="887c5-122">Obtient l’offset de début pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="887c5-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="887c5-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="887c5-123">Requirements</span></span>  
 <span data-ttu-id="887c5-124">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="887c5-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887c5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="887c5-125">See Also</span></span>  
 [<span data-ttu-id="887c5-126">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="887c5-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="887c5-127">ISymUnmanagedScope2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="887c5-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
