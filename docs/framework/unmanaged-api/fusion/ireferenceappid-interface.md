---
title: IReferenceAppId, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="ed24a-102">IReferenceAppId, interface</span><span class="sxs-lookup"><span data-stu-id="ed24a-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="ed24a-103">Représente une référence à l’identificateur unique pour l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ed24a-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed24a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ed24a-104">Methods</span></span>  
  
|<span data-ttu-id="ed24a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ed24a-105">Method</span></span>|<span data-ttu-id="ed24a-106">Description</span><span class="sxs-lookup"><span data-stu-id="ed24a-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="ed24a-107">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de code de l’application référencée par ce `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ed24a-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="ed24a-108">Définit l’identificateur de code de l’application référencée par ce `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ed24a-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="ed24a-109">Obtient un pointeur d’interface vers un `IEnumReferenceIdentity` instance contenant le `IReferenceIdentity` instances qui représentent les membres de ce `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ed24a-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="ed24a-110">Obtient un pointeur vers une représentation sous forme de chaîne de l’identificateur de jeton pour un abonnement à cette `IReferenceAppId`.</span><span class="sxs-lookup"><span data-stu-id="ed24a-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="ed24a-111">Définit l’identificateur de jeton pour un abonnement à cette `IReferenceAppId` à la valeur de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ed24a-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed24a-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed24a-112">Requirements</span></span>  
 <span data-ttu-id="ed24a-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed24a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed24a-114">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="ed24a-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ed24a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed24a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed24a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed24a-116">See Also</span></span>  
 [<span data-ttu-id="ed24a-117">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="ed24a-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="ed24a-118">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="ed24a-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="ed24a-119">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="ed24a-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
