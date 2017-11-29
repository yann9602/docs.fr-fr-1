---
title: CertFreeAuthenticodeTimestamperInfo, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeTimestamperInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8b6392e57e641d25d07580fcb6bf630f8d983be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="ea0b5-102">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="ea0b5-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="ea0b5-103">Libère les ressources allouées pour le [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="ea0b5-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea0b5-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea0b5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea0b5-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="ea0b5-106">[en entrée, en sortie] Les informations de l’horodateur à libérer.</span><span class="sxs-lookup"><span data-stu-id="ea0b5-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="ea0b5-107">Consultez le [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="ea0b5-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea0b5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea0b5-108">Return Value</span></span>  
 <span data-ttu-id="ea0b5-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="ea0b5-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="ea0b5-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="ea0b5-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea0b5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea0b5-111">See Also</span></span>  
 [<span data-ttu-id="ea0b5-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ea0b5-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
