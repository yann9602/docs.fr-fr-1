---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 32a4e084-09b2-4946-a4a7-19a1fed9f7cc
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b2431662caa41c67746da7e21591c743896c161
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfocount-method"></a><span data-ttu-id="91f0a-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="91f0a-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfoCount Method</span></span>
<span data-ttu-id="91f0a-103">Consultez [defineasyncstepinfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="91f0a-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91f0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91f0a-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfoCount(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91f0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="91f0a-105">Parameters</span></span>  
  
|<span data-ttu-id="91f0a-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="91f0a-106">Parameter</span></span>|<span data-ttu-id="91f0a-107">Description</span><span class="sxs-lookup"><span data-stu-id="91f0a-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="91f0a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="91f0a-108">Return Value</span></span>  
 <span data-ttu-id="91f0a-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="91f0a-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91f0a-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="91f0a-110">Requirements</span></span>  
 <span data-ttu-id="91f0a-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="91f0a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91f0a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91f0a-112">See Also</span></span>  
 [<span data-ttu-id="91f0a-113">Isymunmanagedasyncmethod, Interface</span><span class="sxs-lookup"><span data-stu-id="91f0a-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
