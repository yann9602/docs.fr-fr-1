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
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="c4a39-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a39-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="c4a39-103">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c4a39-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a39-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4a39-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4a39-105">Parameters</span></span>  
  
|<span data-ttu-id="c4a39-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c4a39-106">Parameter</span></span>|<span data-ttu-id="c4a39-107">Description</span><span class="sxs-lookup"><span data-stu-id="c4a39-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="c4a39-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c4a39-108">Return Value</span></span>  
 <span data-ttu-id="c4a39-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="c4a39-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a39-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4a39-110">Requirements</span></span>  
 <span data-ttu-id="c4a39-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c4a39-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a39-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4a39-112">See Also</span></span>  
 [<span data-ttu-id="c4a39-113">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="c4a39-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
