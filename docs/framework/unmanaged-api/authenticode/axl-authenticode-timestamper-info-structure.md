---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ada8f5b21328d008ad34f4ac96cbf24e881a93b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="6894f-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="6894f-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="6894f-103">Définit les informations de l'horodateur Authenticode.</span><span class="sxs-lookup"><span data-stu-id="6894f-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6894f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6894f-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="6894f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6894f-105">Members</span></span>  
  
|<span data-ttu-id="6894f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6894f-106">Member</span></span>|<span data-ttu-id="6894f-107">Description</span><span class="sxs-lookup"><span data-stu-id="6894f-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="6894f-108">La taille de cette structure.</span><span class="sxs-lookup"><span data-stu-id="6894f-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="6894f-109">Le code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="6894f-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="6894f-110">L'algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="6894f-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="6894f-111">La date/heure de l'horodatage.</span><span class="sxs-lookup"><span data-stu-id="6894f-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="6894f-112">La chaîne de contexte de l'horodateur.</span><span class="sxs-lookup"><span data-stu-id="6894f-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="6894f-113">Consultez le [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="6894f-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6894f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6894f-114">See Also</span></span>  
 [<span data-ttu-id="6894f-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6894f-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
