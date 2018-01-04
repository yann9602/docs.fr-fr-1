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
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a><span data-ttu-id="f979e-102">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="f979e-102">ISymUnmanagedWriter5 Interface</span></span>
<span data-ttu-id="f979e-103">Isymunmanagedwriter5, interface.</span><span class="sxs-lookup"><span data-stu-id="f979e-103">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f979e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f979e-104">Syntax</span></span>  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a><span data-ttu-id="f979e-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f979e-105">Methods</span></span>  
 <span data-ttu-id="f979e-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f979e-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="f979e-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="f979e-107">Method</span></span>|<span data-ttu-id="f979e-108">Description</span><span class="sxs-lookup"><span data-stu-id="f979e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f979e-109">CloseMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="f979e-109">CloseMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|<span data-ttu-id="f979e-110">Fermez la section des données personnalisées spécifiques pour l’étendue de jeton vers la source des informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="f979e-110">Close the special custom data section for token-to- source span mapping information.</span></span> <span data-ttu-id="f979e-111">Après sa fermeture, aucun plus d’informations de mappage ne peut être ajouté.</span><span class="sxs-lookup"><span data-stu-id="f979e-111">After it is closed, no more mapping information can be added.</span></span>|  
|[<span data-ttu-id="f979e-112">MapTokenToSourceSpan, méthode</span><span class="sxs-lookup"><span data-stu-id="f979e-112">MapTokenToSourceSpan Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|<span data-ttu-id="f979e-113">Mappages s’étendre sur le jeton de métadonnées donné à la ligne source donné dans le fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="f979e-113">Maps the given metadata token to the given source line span in the specified source file.</span></span><br /><br /> <span data-ttu-id="f979e-114">Doit être appelé entre les appels à [openmaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et [closemaptokenstosourcespans, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span><span class="sxs-lookup"><span data-stu-id="f979e-114">Must be called between calls to [OpenMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>|  
|[<span data-ttu-id="f979e-115">OpenMapTokensToSourceSpans, méthode</span><span class="sxs-lookup"><span data-stu-id="f979e-115">OpenMapTokensToSourceSpans Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|<span data-ttu-id="f979e-116">Ouvrez une section spéciale de données personnalisé pour émettre des informations de mappage de span à source de jeton dans.</span><span class="sxs-lookup"><span data-stu-id="f979e-116">Open a special custom data section to emit token-to- source span mapping information into.</span></span> <span data-ttu-id="f979e-117">Ouverture de cette section lorsqu’une méthode est déjà ouverte, ou vice versa, est une erreur.</span><span class="sxs-lookup"><span data-stu-id="f979e-117">Opening this section when a method is already open, or vice versa, is an error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f979e-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f979e-118">Requirements</span></span>  
 <span data-ttu-id="f979e-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f979e-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f979e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f979e-120">See Also</span></span>  
 [<span data-ttu-id="f979e-121">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="f979e-121">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="f979e-122">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="f979e-122">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
