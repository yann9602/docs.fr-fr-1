---
title: Fonction CreateCordbObject
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCoredbObject
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7007e541e9999e0cb14a83845eb28d71336b3ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createcordbobject-function"></a><span data-ttu-id="6f439-102">Fonction CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="6f439-102">CreateCordbObject Function</span></span>
<span data-ttu-id="6f439-103">Crée une interface de débogueur ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) qui fournit des fonctionnalités d’instanciation d’une session de débogage managée sur un processus distant.</span><span class="sxs-lookup"><span data-stu-id="6f439-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f439-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f439-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f439-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6f439-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="6f439-106">[in] Version de débogage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="6f439-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="6f439-107">Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="6f439-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="6f439-108">[out] Pointeur vers un pointeur vers un objet qui sera converti en un [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface et retourné.</span><span class="sxs-lookup"><span data-stu-id="6f439-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f439-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6f439-109">Return Value</span></span>  
 <span data-ttu-id="6f439-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f439-110">S_OK</span></span>  
 <span data-ttu-id="6f439-111">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemins d'accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="6f439-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="6f439-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6f439-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="6f439-113">`ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="6f439-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="6f439-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6f439-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="6f439-115">Impossible d'allouer suffisamment de mémoire pour `ppCordb`.</span><span class="sxs-lookup"><span data-stu-id="6f439-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="6f439-116">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="6f439-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="6f439-117">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="6f439-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f439-118">Notes</span><span class="sxs-lookup"><span data-stu-id="6f439-118">Remarks</span></span>  
 <span data-ttu-id="6f439-119">Le [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface retournée dans `ppCordb` est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.</span><span class="sxs-lookup"><span data-stu-id="6f439-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f439-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6f439-120">Requirements</span></span>  
 <span data-ttu-id="6f439-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f439-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f439-122">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="6f439-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="6f439-123">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="6f439-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="6f439-124">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="6f439-124">**.NET Framework Versions:** 3.5 SP1</span></span>
