---
title: CertFreeAuthenticodeSignerInfo, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f922cdba8bcfce6c9ff4543f6aea5bacfdc60ab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="bc18e-102">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="bc18e-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="bc18e-103">Libère les ressources allouées pour le [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="bc18e-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc18e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc18e-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc18e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc18e-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="bc18e-106">[en entrée, en sortie] Les informations du signataire à libérer.</span><span class="sxs-lookup"><span data-stu-id="bc18e-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="bc18e-107">Consultez le [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="bc18e-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc18e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bc18e-108">Return Value</span></span>  
 <span data-ttu-id="bc18e-109">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="bc18e-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bc18e-110">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="bc18e-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc18e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc18e-111">See Also</span></span>  
 [<span data-ttu-id="bc18e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bc18e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
