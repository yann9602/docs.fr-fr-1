---
title: "ICorDebugAssembly::EnumerateModules, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.EnumerateModules
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28c6f2efe4a48c198bd64fa7f5665b97969dbc43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="f7cc1-102">ICorDebugAssembly::EnumerateModules, méthode</span><span class="sxs-lookup"><span data-stu-id="f7cc1-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="f7cc1-103">Obtient un énumérateur pour les modules contenus dans le `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="f7cc1-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7cc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7cc1-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7cc1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7cc1-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="f7cc1-106">[out] Pointeur vers l’adresse de l’interface ICorDebugModuleEnum qui est l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="f7cc1-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7cc1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7cc1-107">Requirements</span></span>  
 <span data-ttu-id="f7cc1-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7cc1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7cc1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7cc1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7cc1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7cc1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7cc1-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7cc1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
