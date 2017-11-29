---
title: Structure CoreClrDebugRuntimeInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugRuntimeInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e18416822aed6020fb0de8eb5bc7d38e4cd2eb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="a87c7-102">Structure CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a87c7-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="a87c7-103">Représente une instance du Common Language Runtime (CLR) qui est chargée dans un processus sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="a87c7-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a87c7-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a87c7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a87c7-105">Members</span></span>  
  
|<span data-ttu-id="a87c7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a87c7-106">Member</span></span>|<span data-ttu-id="a87c7-107">Description</span><span class="sxs-lookup"><span data-stu-id="a87c7-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="a87c7-108">Identificateur de runtime affecté par le proxy de débogage distant en cours d'exécution sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a87c7-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a87c7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a87c7-109">Requirements</span></span>  
 <span data-ttu-id="a87c7-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87c7-111">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a87c7-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a87c7-112">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a87c7-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a87c7-113">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a87c7-113">**.NET Framework Versions:** 3.5 SP1</span></span>
