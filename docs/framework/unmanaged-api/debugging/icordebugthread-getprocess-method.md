---
title: "ICorDebugThread::GetProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be58714856b93a244248fb97d6cc1e1b4ec476c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="2f888-102">ICorDebugThread::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="2f888-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="2f888-103">Obtient un pointeur d’interface vers le processus qui ICorDebugThread fait partie.</span><span class="sxs-lookup"><span data-stu-id="2f888-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f888-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f888-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f888-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f888-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="2f888-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="2f888-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f888-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2f888-107">Requirements</span></span>  
 <span data-ttu-id="2f888-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f888-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f888-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f888-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f888-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f888-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f888-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f888-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
