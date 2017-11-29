---
title: "ICorDebugEval::GetThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.GetThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cde844d0664f7dc7643ef60b65befa95f2d039e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="7a199-102">ICorDebugEval::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="7a199-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="7a199-103">Obtient le thread dans lequel cette évaluation s’exécute ou s’exécutera.</span><span class="sxs-lookup"><span data-stu-id="7a199-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a199-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a199-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a199-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7a199-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="7a199-106">[out] Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="7a199-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a199-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7a199-107">Requirements</span></span>  
 <span data-ttu-id="7a199-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a199-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a199-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a199-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a199-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a199-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a199-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a199-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
