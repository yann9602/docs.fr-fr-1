---
title: "ICorDebugThread::CreateEval, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aebabf12e6dcf12f0e1e1f24ec2ad69ea55ec86c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="d5bdf-102">ICorDebugThread::CreateEval, méthode</span><span class="sxs-lookup"><span data-stu-id="d5bdf-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="d5bdf-103">Crée un objet ICorDebugEval qui rassemble et expose les fonctionnalités de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d5bdf-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5bdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5bdf-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5bdf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5bdf-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="d5bdf-106">[out] Un pointeur vers l’adresse d’un `ICorDebugEval` objet qui rassemble et expose les fonctionnalités de ce thread.</span><span class="sxs-lookup"><span data-stu-id="d5bdf-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5bdf-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="d5bdf-107">Remarks</span></span>  
 <span data-ttu-id="d5bdf-108">L’objet d’évaluation envoie une nouvelle chaîne sur le thread avant de procéder à son calcul.</span><span class="sxs-lookup"><span data-stu-id="d5bdf-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="d5bdf-109">Cela interrompt le calcul en cours d’exécution sur le thread jusqu'à ce que l’évaluation s’exécute.</span><span class="sxs-lookup"><span data-stu-id="d5bdf-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5bdf-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d5bdf-110">Requirements</span></span>  
 <span data-ttu-id="d5bdf-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5bdf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5bdf-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5bdf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5bdf-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5bdf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5bdf-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5bdf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
