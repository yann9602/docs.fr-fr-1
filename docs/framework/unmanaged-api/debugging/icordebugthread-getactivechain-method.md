---
title: "ICorDebugThread::GetActiveChain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f3f104933bc70682a531c0853cfc6eabcd357831
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="ff94c-102">ICorDebugThread::GetActiveChain, méthode</span><span class="sxs-lookup"><span data-stu-id="ff94c-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="ff94c-103">Obtient un pointeur d’interface vers la chaîne de pile active (la plus récente) sur cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ff94c-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff94c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff94c-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff94c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff94c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ff94c-106">[out] Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne de pile.</span><span class="sxs-lookup"><span data-stu-id="ff94c-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff94c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff94c-107">Remarks</span></span>  
 <span data-ttu-id="ff94c-108">Le `ppChain` paramètre est null si aucune chaîne de pile n’est actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="ff94c-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff94c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ff94c-109">Requirements</span></span>  
 <span data-ttu-id="ff94c-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff94c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff94c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff94c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff94c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff94c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff94c-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff94c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
