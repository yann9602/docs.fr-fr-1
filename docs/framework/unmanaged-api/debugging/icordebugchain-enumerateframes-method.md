---
title: "ICorDebugChain::EnumerateFrames, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87e2fbc0a4ca9d97ac7e57234383ebd8cee56211
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="21264-102">ICorDebugChain::EnumerateFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="21264-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="21264-103">Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.</span><span class="sxs-lookup"><span data-stu-id="21264-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21264-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21264-104">Syntax</span></span>  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21264-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21264-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="21264-106">[out] Pointeur vers l’adresse d’un objet ICorDebugFrameEnum qui est l’énumérateur pour les frames de pile.</span><span class="sxs-lookup"><span data-stu-id="21264-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21264-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="21264-107">Remarks</span></span>  
 <span data-ttu-id="21264-108">La chaîne représente la pile des appels physique pour le thread.</span><span class="sxs-lookup"><span data-stu-id="21264-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="21264-109">Le `EnumerateFrames` méthode doit être appelée uniquement pour les chaînes managées.</span><span class="sxs-lookup"><span data-stu-id="21264-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="21264-110">L’API de débogage ne fournit pas de méthodes pour obtenir des images contenues dans les chaînes non managées.</span><span class="sxs-lookup"><span data-stu-id="21264-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="21264-111">Le débogueur doit utiliser d’autres moyens d’obtenir ces informations.</span><span class="sxs-lookup"><span data-stu-id="21264-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21264-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="21264-112">Requirements</span></span>  
 <span data-ttu-id="21264-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21264-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21264-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21264-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21264-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21264-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21264-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21264-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
