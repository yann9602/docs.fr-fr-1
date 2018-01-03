---
title: "ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 560690e95e7aa0aef37e3a708183641bd70ee97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="fc54e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="fc54e-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="fc54e-103">Vérifie si la méthode async informations ou non.</span><span class="sxs-lookup"><span data-stu-id="fc54e-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="fc54e-104">Si cette méthode retourne `FALSE` , il est interdit d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="fc54e-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="fc54e-105">Ils seront retournent tous les `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="fc54e-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc54e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc54e-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc54e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc54e-107">Parameters</span></span>  
  
|<span data-ttu-id="fc54e-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fc54e-108">Parameter</span></span>|<span data-ttu-id="fc54e-109">Description</span><span class="sxs-lookup"><span data-stu-id="fc54e-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="fc54e-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc54e-110">Return Value</span></span>  
 <span data-ttu-id="fc54e-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fc54e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc54e-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc54e-112">Requirements</span></span>  
 <span data-ttu-id="fc54e-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc54e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc54e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc54e-114">See Also</span></span>  
 [<span data-ttu-id="fc54e-115">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="fc54e-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
