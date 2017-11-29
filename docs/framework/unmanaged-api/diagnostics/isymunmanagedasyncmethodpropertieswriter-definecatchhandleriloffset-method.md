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
ms.openlocfilehash: 3bae0e2dfb56883a674b282acd385ba45a25bebb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="cef99-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="cef99-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="cef99-103">Définit le langage intermédiaire de décalage pour le gestionnaire catch de généré par le compilateur qui encapsule une méthode async.</span><span class="sxs-lookup"><span data-stu-id="cef99-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="cef99-104">Par le débogueur, l’offset IL de la capture générée permet de gérer la capture comme s’il était code non-utilisateur, même si elle peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cef99-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="cef99-105">En particulier, il est utilisé en réponse à une **CatchHandlerFound** événement d’exception.</span><span class="sxs-lookup"><span data-stu-id="cef99-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cef99-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cef99-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cef99-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cef99-107">Parameters</span></span>  
  
|<span data-ttu-id="cef99-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cef99-108">Parameter</span></span>|<span data-ttu-id="cef99-109">Description</span><span class="sxs-lookup"><span data-stu-id="cef99-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="cef99-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cef99-110">Return Value</span></span>  
 <span data-ttu-id="cef99-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cef99-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cef99-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cef99-112">Requirements</span></span>  
 <span data-ttu-id="cef99-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cef99-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef99-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cef99-114">See Also</span></span>  
 [<span data-ttu-id="cef99-115">Isymunmanagedasyncmethodpropertieswriter, Interface</span><span class="sxs-lookup"><span data-stu-id="cef99-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
