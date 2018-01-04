---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54cc369b309d1ffe20d0f3e6a2d4ae4e0443c85f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="c64d4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="c64d4-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="c64d4-103">Définit le langage intermédiaire de décalage pour le gestionnaire catch de généré par le compilateur qui encapsule une méthode async.</span><span class="sxs-lookup"><span data-stu-id="c64d4-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="c64d4-104">Par le débogueur, l’offset IL de la capture générée permet de gérer la capture comme s’il était code non-utilisateur, même si elle peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c64d4-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="c64d4-105">En particulier, il est utilisé en réponse à une **CatchHandlerFound** événement d’exception.</span><span class="sxs-lookup"><span data-stu-id="c64d4-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c64d4-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c64d4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c64d4-107">Parameters</span></span>  
  
|<span data-ttu-id="c64d4-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c64d4-108">Parameter</span></span>|<span data-ttu-id="c64d4-109">Description</span><span class="sxs-lookup"><span data-stu-id="c64d4-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="c64d4-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c64d4-110">Return Value</span></span>  
 <span data-ttu-id="c64d4-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c64d4-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c64d4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c64d4-112">Requirements</span></span>  
 <span data-ttu-id="c64d4-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c64d4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c64d4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c64d4-114">See Also</span></span>  
 [<span data-ttu-id="c64d4-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="c64d4-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
