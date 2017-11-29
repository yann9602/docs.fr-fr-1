---
title: "ICorDebugStepper2::SetJMC, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper2.SetJMC
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b34e0d612957da1ec1ca3535bfa1a0d7a5bae5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepper2setjmc-method"></a><span data-ttu-id="e5e18-102">ICorDebugStepper2::SetJMC, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e18-102">ICorDebugStepper2::SetJMC Method</span></span>
<span data-ttu-id="e5e18-103">Définit une valeur qui indique si cette ICorDebugStepper exécute pas à pas uniquement le code créé par le développeur d’une application.</span><span class="sxs-lookup"><span data-stu-id="e5e18-103">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span> <span data-ttu-id="e5e18-104">Ce processus est également connu comme débogage uniquement mon code (JMC).</span><span class="sxs-lookup"><span data-stu-id="e5e18-104">This process is also known as just my code (JMC) debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e18-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5e18-105">Syntax</span></span>  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5e18-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5e18-106">Parameters</span></span>  
 `fIsJMCStepper`  
 <span data-ttu-id="e5e18-107">[in] La valeur `true` pour parcourir uniquement le code qui est créé par le développeur de l’application ; sinon, valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="e5e18-107">[in] Set to `true` to step only through code that is authored by an application's developer; otherwise, set to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e18-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5e18-108">Requirements</span></span>  
 <span data-ttu-id="e5e18-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e18-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e18-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5e18-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5e18-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5e18-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e18-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e18-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
