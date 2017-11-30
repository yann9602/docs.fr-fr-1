---
title: "ICorDebugProcess2::GetVersion, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84db785d47f97fe058b8a66070bcf4757fa11517
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="6d277-102">ICorDebugProcess2::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="6d277-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="6d277-103">Obtient le numéro de version du common language runtime (CLR) qui est en cours d’exécution de ce processus.</span><span class="sxs-lookup"><span data-stu-id="6d277-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d277-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d277-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d277-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="6d277-106">[out] Pointeur vers une structure COR_VERSION qui stocke le numéro de version du runtime.</span><span class="sxs-lookup"><span data-stu-id="6d277-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d277-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d277-107">Remarks</span></span>  
 <span data-ttu-id="6d277-108">Le `GetVersion` méthode retourne un code d’erreur si aucune exécution n’a été chargée dans le processus.</span><span class="sxs-lookup"><span data-stu-id="6d277-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d277-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6d277-109">Requirements</span></span>  
 <span data-ttu-id="6d277-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d277-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d277-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d277-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d277-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d277-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d277-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d277-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
