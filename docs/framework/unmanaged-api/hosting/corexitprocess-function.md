---
title: CorExitProcess, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="f2ede-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="f2ede-102">CorExitProcess Function</span></span>
<span data-ttu-id="f2ede-103">Arrête le processus non managé en cours.</span><span class="sxs-lookup"><span data-stu-id="f2ede-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="f2ede-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f2ede-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="f2ede-105">Utilisez le [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="f2ede-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ede-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ede-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2ede-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2ede-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="f2ede-108">Entier qui spécifie le code de sortie.</span><span class="sxs-lookup"><span data-stu-id="f2ede-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2ede-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2ede-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2ede-110">Compter les [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` quitte chaque exécution commencée dans le processus, et pas seulement le runtime auquel les API héritées ont été liés.</span><span class="sxs-lookup"><span data-stu-id="f2ede-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ede-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2ede-111">Requirements</span></span>  
 <span data-ttu-id="f2ede-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ede-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ede-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f2ede-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2ede-114">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2ede-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2ede-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ede-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ede-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2ede-116">See Also</span></span>  
 [<span data-ttu-id="f2ede-117">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="f2ede-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
