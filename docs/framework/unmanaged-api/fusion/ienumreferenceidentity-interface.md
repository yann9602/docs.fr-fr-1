---
title: IEnumReferenceIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a><span data-ttu-id="9ad30-102">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="9ad30-102">IEnumReferenceIdentity Interface</span></span>
<span data-ttu-id="9ad30-103">Sert d’énumérateur pour une collection de `IReferenceIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="9ad30-103">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ad30-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9ad30-104">Methods</span></span>  
  
|<span data-ttu-id="9ad30-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9ad30-105">Method</span></span>|<span data-ttu-id="9ad30-106">Description</span><span class="sxs-lookup"><span data-stu-id="9ad30-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|<span data-ttu-id="9ad30-107">Obtient un pointeur d’interface vers un nouveau `IEnumReferenceIdentity` qui contient les mêmes membres que ce `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9ad30-107">Gets an interface pointer to a new `IEnumReferenceIdentity` that contains the same members as this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Next`|<span data-ttu-id="9ad30-108">Obtient le nombre spécifié de `IReferenceIdentity` objets, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="9ad30-108">Gets the specified number of `IReferenceIdentity` objects, starting at the current position.</span></span>|  
|`IEnumReferenceIdentity::Reset`|<span data-ttu-id="9ad30-109">Déplace le pointeur d’instruction au début de cette `IEnumReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9ad30-109">Moves the instruction pointer to the beginning of this `IEnumReferenceIdentity`.</span></span>|  
|`IEnumReferenceIdentity::Skip`|<span data-ttu-id="9ad30-110">Déplace le pointeur d’instruction par le nombre spécifié d’éléments, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="9ad30-110">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ad30-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ad30-111">Requirements</span></span>  
 <span data-ttu-id="9ad30-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad30-113">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="9ad30-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9ad30-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad30-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ad30-115">See Also</span></span>  
 [<span data-ttu-id="9ad30-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="9ad30-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="9ad30-117">IReferenceIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="9ad30-117">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
