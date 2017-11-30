---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e017097183243c84a2ce40cc473067e05c80c3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="fc396-102">ISymUnmanagedAsyncMethod::GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="fc396-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="fc396-103">Consultez [definekickoffmethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="fc396-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc396-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc396-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc396-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc396-105">Parameters</span></span>  
  
|<span data-ttu-id="fc396-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fc396-106">Parameter</span></span>|<span data-ttu-id="fc396-107">Description</span><span class="sxs-lookup"><span data-stu-id="fc396-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="fc396-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc396-108">Return Value</span></span>  
 <span data-ttu-id="fc396-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fc396-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc396-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fc396-110">Requirements</span></span>  
 <span data-ttu-id="fc396-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc396-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc396-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc396-112">See Also</span></span>  
 [<span data-ttu-id="fc396-113">Isymunmanagedasyncmethod, Interface</span><span class="sxs-lookup"><span data-stu-id="fc396-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
