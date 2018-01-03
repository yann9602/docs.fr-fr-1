---
title: ISymUnmanagedAsyncMethodPropertiesWriter, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d61fdb9f7e3eb2bc10de7584061d8922bf9285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="1c8ce-102">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="1c8ce-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="1c8ce-103">Permet de définir les informations de méthode async facultatif pour chaque symbole de méthode.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="1c8ce-104">Toujours utiliser avec une méthode ouverte ; Autrement dit, entre les appels à la [OpenMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) et le [CloseMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="1c8ce-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8ce-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c8ce-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="1c8ce-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1c8ce-106">Methods</span></span>  
 <span data-ttu-id="1c8ce-107">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c8ce-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="1c8ce-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="1c8ce-108">Method</span></span>|<span data-ttu-id="1c8ce-109">Description</span><span class="sxs-lookup"><span data-stu-id="1c8ce-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c8ce-110">DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="1c8ce-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="1c8ce-111">Définissez un groupe d’async await des opérations dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="1c8ce-112">Chaque décalage yield correspond à l’instruction de retour d’une expression await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="1c8ce-113">Chaque `breakpointMethod` / `breakpointOffset` paire identifie où l’opération asynchrone reprendra ; il peut être dans une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="1c8ce-114">DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="1c8ce-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="1c8ce-115">Définit le langage intermédiaire de décalage pour le gestionnaire catch de généré par le compilateur qui encapsule une méthode async.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="1c8ce-116">Offset IL de la capture générée permet de gérer des catch comme s’il s’agissait de code non-utilisateur, même si elle peut se produire dans une méthode de code de l’utilisateur par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="1c8ce-117">En particulier, il est utilisé en réponse à une **CatchHandlerFound** événement d’exception.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="1c8ce-118">DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="1c8ce-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="1c8ce-119">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="1c8ce-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c8ce-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c8ce-120">Requirements</span></span>  
 <span data-ttu-id="1c8ce-121">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1c8ce-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8ce-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c8ce-122">See Also</span></span>  
 [<span data-ttu-id="1c8ce-123">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="1c8ce-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
