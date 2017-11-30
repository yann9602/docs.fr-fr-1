---
title: IReferenceIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="d8805-102">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="d8805-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="d8805-103">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="d8805-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8805-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d8805-104">Methods</span></span>  
  
|<span data-ttu-id="d8805-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d8805-105">Method</span></span>|<span data-ttu-id="d8805-106">Description</span><span class="sxs-lookup"><span data-stu-id="d8805-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="d8805-107">Obtient un pointeur d’interface vers un nouveau `IReferenceIdentity` instance qui est identique à ce `IReferenceIdentity`, à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d8805-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="d8805-108">Obtient un pointeur d’interface vers un `IEnumIDENTITY_ATTRIBUTE` instance qui contient les attributs associés à ce `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d8805-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="d8805-109">Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="d8805-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="d8805-110">Définit l’attribut qui possède l’espace de noms et le nom spécifié à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d8805-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8805-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8805-111">Requirements</span></span>  
 <span data-ttu-id="d8805-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8805-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8805-113">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="d8805-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d8805-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8805-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8805-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8805-115">See Also</span></span>  
 [<span data-ttu-id="d8805-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="d8805-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="d8805-117">IEnumIDENTITY_ATTRIBUTE (Interface)</span><span class="sxs-lookup"><span data-stu-id="d8805-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
