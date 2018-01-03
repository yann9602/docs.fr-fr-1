---
title: "ICorDebugProcess::GetHandle, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28065bff38fdf8c7f69920be1f7c6704dd03d69d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="e3e91-102">ICorDebugProcess::GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="e3e91-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="e3e91-103">Obtient un handle vers le processus.</span><span class="sxs-lookup"><span data-stu-id="e3e91-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3e91-104">Syntax</span></span>  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3e91-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3e91-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="e3e91-106">[out] Un pointeur vers un `HPROCESS` qui est le handle du processus.</span><span class="sxs-lookup"><span data-stu-id="e3e91-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3e91-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e3e91-107">Remarks</span></span>  
 <span data-ttu-id="e3e91-108">Le handle récupéré appartient à l’interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="e3e91-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="e3e91-109">Le débogueur doit dupliquer le handle avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="e3e91-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3e91-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e3e91-110">Requirements</span></span>  
 <span data-ttu-id="e3e91-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e91-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3e91-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3e91-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3e91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3e91-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
