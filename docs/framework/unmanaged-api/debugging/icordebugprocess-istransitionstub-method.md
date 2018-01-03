---
title: "ICorDebugProcess::IsTransitionStub, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe38cf5f53c2514b845238c1d52fa12df526fdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="9ec8e-102">ICorDebugProcess::IsTransitionStub, méthode</span><span class="sxs-lookup"><span data-stu-id="9ec8e-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="9ec8e-103">Obtient une valeur qui indique si une adresse est à l’intérieur d’un stub qui provoquera une transition vers du code managé.</span><span class="sxs-lookup"><span data-stu-id="9ec8e-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec8e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ec8e-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ec8e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ec8e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9ec8e-106">[in] A `CORDB_ADDRESS` valeur qui spécifie l’adresse en question.</span><span class="sxs-lookup"><span data-stu-id="9ec8e-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="9ec8e-107">[out] Un pointeur vers une valeur booléenne qui est `true` si l’adresse spécifiée est à l’intérieur d’un stub qui provoquera une transition vers du code managé ; sinon *`pbTransitionStub` est `false`.</span><span class="sxs-lookup"><span data-stu-id="9ec8e-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise *`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ec8e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="9ec8e-108">Remarks</span></span>  
 <span data-ttu-id="9ec8e-109">Le `IsTransitionStub` méthode peut être utilisée par le code pas à pas non managé pour décider du moment retourner le contrôle de pas à pas pour l’exécution pas à pas géré.</span><span class="sxs-lookup"><span data-stu-id="9ec8e-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="9ec8e-110">Vous pouvez également les stubs de transition identité en examinant les informations contenues dans le fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="9ec8e-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec8e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ec8e-111">Requirements</span></span>  
 <span data-ttu-id="9ec8e-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec8e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ec8e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ec8e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ec8e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ec8e-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
