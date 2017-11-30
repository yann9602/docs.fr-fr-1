---
title: ISymUnmanagedWriter5, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="5082b-102">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="5082b-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="5082b-103">Isymunmanagedwriter5, interface.</span><span class="sxs-lookup"><span data-stu-id="5082b-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5082b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5082b-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="5082b-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5082b-105">Methods</span></span>  
 <span data-ttu-id="5082b-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5082b-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5082b-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="5082b-107">Method</span></span>|<span data-ttu-id="5082b-108">Description</span><span class="sxs-lookup"><span data-stu-id="5082b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5082b-109">Closemaptokenstosourcespans, méthode</span><span class="sxs-lookup"><span data-stu-id="5082b-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="5082b-110">Fermez la section des données personnalisées spécifiques pour l’étendue de jeton vers la source des informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="5082b-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="5082b-111">Après sa fermeture, aucun plus d’informations de mappage ne peut être ajouté.</span><span class="sxs-lookup"><span data-stu-id="5082b-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="5082b-112">Maptokentosourcespan, méthode</span><span class="sxs-lookup"><span data-stu-id="5082b-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="5082b-113">Mappages s’étendre sur le jeton de métadonnées donné à la ligne source donné dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="5082b-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="5082b-114">Doit être appelé entre les appels à [openmaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et [closemaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="5082b-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="5082b-115">Openmaptokenstosourcespans, méthode</span><span class="sxs-lookup"><span data-stu-id="5082b-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="5082b-116">Ouvrez une section spéciale de données personnalisé pour émettre des informations de mappage de span à source de jeton dans.</span><span class="sxs-lookup"><span data-stu-id="5082b-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="5082b-117">Ouverture de cette section lorsqu’une méthode est déjà ouverte, ou vice versa, est une erreur.</span><span class="sxs-lookup"><span data-stu-id="5082b-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5082b-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5082b-118">Requirements</span></span>  
 <span data-ttu-id="5082b-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5082b-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5082b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5082b-120">See Also</span></span>  
 [<span data-ttu-id="5082b-121">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="5082b-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="5082b-122">Isymunmanagedwriter4, Interface</span><span class="sxs-lookup"><span data-stu-id="5082b-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
