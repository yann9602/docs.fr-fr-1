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
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="42e4b-102">ISymUnmanagedAsyncMethod::GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="42e4b-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="42e4b-103">Consultez [definekickoffmethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="42e4b-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42e4b-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42e4b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42e4b-105">Parameters</span></span>  
  
|<span data-ttu-id="42e4b-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="42e4b-106">Parameter</span></span>|<span data-ttu-id="42e4b-107">Description</span><span class="sxs-lookup"><span data-stu-id="42e4b-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="42e4b-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="42e4b-108">Return Value</span></span>  
 <span data-ttu-id="42e4b-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="42e4b-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42e4b-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42e4b-110">Requirements</span></span>  
 <span data-ttu-id="42e4b-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="42e4b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e4b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42e4b-112">See Also</span></span>  
 [<span data-ttu-id="42e4b-113">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="42e4b-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
