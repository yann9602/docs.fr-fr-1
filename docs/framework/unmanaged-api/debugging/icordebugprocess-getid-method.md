---
title: "ICorDebugProcess::GetID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 74f388c381576ef69352965877df9f07f0e33281
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="9cdb1-102">ICorDebugProcess::GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="9cdb1-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="9cdb1-103">Obtient l’ID de système d’exploitation (OS) du processus.</span><span class="sxs-lookup"><span data-stu-id="9cdb1-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cdb1-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cdb1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9cdb1-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="9cdb1-106">[out] ID unique du processus.</span><span class="sxs-lookup"><span data-stu-id="9cdb1-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdb1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9cdb1-107">Requirements</span></span>  
 <span data-ttu-id="9cdb1-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdb1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdb1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cdb1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cdb1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cdb1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cdb1-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdb1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
