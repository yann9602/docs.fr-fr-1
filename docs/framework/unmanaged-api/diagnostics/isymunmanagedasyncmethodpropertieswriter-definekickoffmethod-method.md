---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68c5d6662d8cbecca06268bd5010878c4e476f47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="7ddcd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="7ddcd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="7ddcd-103">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ddcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ddcd-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ddcd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ddcd-105">Parameters</span></span>  
  
|<span data-ttu-id="7ddcd-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="7ddcd-106">Parameter</span></span>|<span data-ttu-id="7ddcd-107">Description</span><span class="sxs-lookup"><span data-stu-id="7ddcd-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="7ddcd-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7ddcd-108">Return Value</span></span>  
 <span data-ttu-id="7ddcd-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ddcd-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ddcd-110">Requirements</span></span>  
 <span data-ttu-id="7ddcd-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ddcd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddcd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ddcd-112">See Also</span></span>  
 [<span data-ttu-id="7ddcd-113">Isymunmanagedasyncmethodpropertieswriter, Interface</span><span class="sxs-lookup"><span data-stu-id="7ddcd-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
