---
title: BucketParameters, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: BucketParameters
api_location: mscoree.dll
api_type: COM
f1_keywords: BucketParameters
helpviewer_keywords: BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7626ce6b2b6278be7cd9989718c13f7c98e4ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="c96a4-102">BucketParameters, structure</span><span class="sxs-lookup"><span data-stu-id="c96a4-102">BucketParameters Structure</span></span>
<span data-ttu-id="c96a4-103">Stocke le nom de type d’un événement et les paramètres de l’exception actuelle est associé à l’événement.</span><span class="sxs-lookup"><span data-stu-id="c96a4-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c96a4-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="c96a4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c96a4-105">Members</span></span>  
  
|<span data-ttu-id="c96a4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c96a4-106">Member</span></span>|<span data-ttu-id="c96a4-107">Description</span><span class="sxs-lookup"><span data-stu-id="c96a4-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="c96a4-108">`true`, si le reste de cette structure est valide ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="c96a4-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="c96a4-109">Nom du type d’événement.</span><span class="sxs-lookup"><span data-stu-id="c96a4-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="c96a4-110">Un tableau de chaînes, dont chacun spécifie un paramètre pour l’exception actuelle associée à l’événement.</span><span class="sxs-lookup"><span data-stu-id="c96a4-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c96a4-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c96a4-111">Requirements</span></span>  
 <span data-ttu-id="c96a4-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c96a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c96a4-113">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="c96a4-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c96a4-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c96a4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96a4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c96a4-115">See Also</span></span>  
 [<span data-ttu-id="c96a4-116">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c96a4-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
