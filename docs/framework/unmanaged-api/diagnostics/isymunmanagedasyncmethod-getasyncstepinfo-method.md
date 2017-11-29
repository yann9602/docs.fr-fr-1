---
title: "ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad3fb6dba7740c3c541a446205b90d6f007635a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="6e59e-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="6e59e-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="6e59e-103">Consultez [defineasyncstepinfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e59e-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e59e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e59e-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e59e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e59e-105">Parameters</span></span>  
  
|<span data-ttu-id="6e59e-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6e59e-106">Parameter</span></span>|<span data-ttu-id="6e59e-107">Description</span><span class="sxs-lookup"><span data-stu-id="6e59e-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="6e59e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6e59e-108">Return Value</span></span>  
 <span data-ttu-id="6e59e-109">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6e59e-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e59e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6e59e-110">Requirements</span></span>  
 <span data-ttu-id="6e59e-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6e59e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e59e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e59e-112">See Also</span></span>  
 [<span data-ttu-id="6e59e-113">Isymunmanagedasyncmethod, Interface</span><span class="sxs-lookup"><span data-stu-id="6e59e-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
