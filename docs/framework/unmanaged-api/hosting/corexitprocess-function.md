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
ms.workload: dotnet
ms.openlocfilehash: 560f63c131ad336a3ff4b4edec0aed2b58d33ba5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="61692-102">CorExitProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="61692-102">CorExitProcess Function</span></span>
<span data-ttu-id="61692-103">Arrête le processus non managé en cours.</span><span class="sxs-lookup"><span data-stu-id="61692-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="61692-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61692-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="61692-105">Utilisez le [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="61692-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61692-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61692-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61692-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61692-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="61692-108">Entier qui spécifie le code de sortie.</span><span class="sxs-lookup"><span data-stu-id="61692-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61692-109">Notes</span><span class="sxs-lookup"><span data-stu-id="61692-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61692-110">Compter les [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` quitte chaque exécution commencée dans le processus, et pas seulement le runtime auquel les API héritées ont été liés.</span><span class="sxs-lookup"><span data-stu-id="61692-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61692-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61692-111">Requirements</span></span>  
 <span data-ttu-id="61692-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61692-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61692-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61692-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61692-114">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61692-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61692-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61692-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61692-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61692-116">See Also</span></span>  
 [<span data-ttu-id="61692-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="61692-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
