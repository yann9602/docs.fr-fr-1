---
title: "ICorDebugModule::EnableJITDebugging, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="ef7ee-102">ICorDebugModule::EnableJITDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="ef7ee-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="ef7ee-103">Contrôle si le compilateur (JIT) juste-à-temps conserve les informations de débogage pour les méthodes de ce module.</span><span class="sxs-lookup"><span data-stu-id="ef7ee-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef7ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef7ee-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef7ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef7ee-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="ef7ee-106">[in] Définissez cette valeur sur `true` pour permettre au compilateur JIT de conserver les informations de mappage entre la version de langage intermédiaire (MSIL) de Microsoft et de la version de compilation JIT de chaque méthode dans ce module.</span><span class="sxs-lookup"><span data-stu-id="ef7ee-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="ef7ee-107">[in] Définissez cette valeur sur `true` pour permettre au compilateur JIT de générer du code avec certaines optimisations spécifiques au JIT pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="ef7ee-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef7ee-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ef7ee-108">Remarks</span></span>  
 <span data-ttu-id="ef7ee-109">Débogage JIT est activé par défaut pour tous les modules qui sont chargés lorsque le débogueur est actif.</span><span class="sxs-lookup"><span data-stu-id="ef7ee-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="ef7ee-110">Par programmation l’activation ou désactivation des paramètres substitue les paramètres globaux.</span><span class="sxs-lookup"><span data-stu-id="ef7ee-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef7ee-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ef7ee-111">Requirements</span></span>  
 <span data-ttu-id="ef7ee-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef7ee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef7ee-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef7ee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef7ee-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef7ee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef7ee-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef7ee-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
