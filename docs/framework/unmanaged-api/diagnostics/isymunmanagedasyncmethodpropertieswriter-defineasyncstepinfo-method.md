---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c33403c48e6f395d8d0e10c7fddcea327d87529a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="cf6b6-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="cf6b6-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="cf6b6-103">Définissez un groupe d’async await des opérations dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf6b6-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="cf6b6-104">Chaque décalage yield correspond à l’instruction de retour d’une expression await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="cf6b6-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="cf6b6-105">Chaque `breakpointMethod` / `breakpointOffset` paire nous indique où l’opération asynchrone reprendra, (qui peuvent être dans une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="cf6b6-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6b6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf6b6-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf6b6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf6b6-107">Parameters</span></span>  
  
|<span data-ttu-id="cf6b6-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cf6b6-108">Parameter</span></span>|<span data-ttu-id="cf6b6-109">Description</span><span class="sxs-lookup"><span data-stu-id="cf6b6-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="cf6b6-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cf6b6-110">Return Value</span></span>  
 <span data-ttu-id="cf6b6-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="cf6b6-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf6b6-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf6b6-112">Requirements</span></span>  
 <span data-ttu-id="cf6b6-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cf6b6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf6b6-114">See Also</span></span>  
 [<span data-ttu-id="cf6b6-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="cf6b6-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
