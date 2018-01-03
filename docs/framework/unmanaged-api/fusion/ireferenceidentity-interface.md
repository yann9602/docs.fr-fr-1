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
ms.workload: dotnet
ms.openlocfilehash: c9696687f292d7dcaa3d430c1e269f0fedb05e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="93ea2-102">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="93ea2-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="93ea2-103">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="93ea2-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93ea2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93ea2-104">Methods</span></span>  
  
|<span data-ttu-id="93ea2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="93ea2-105">Method</span></span>|<span data-ttu-id="93ea2-106">Description</span><span class="sxs-lookup"><span data-stu-id="93ea2-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="93ea2-107">Obtient un pointeur d’interface vers un nouveau `IReferenceIdentity` instance qui est identique à ce `IReferenceIdentity`, à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="93ea2-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="93ea2-108">Obtient un pointeur d’interface vers un `IEnumIDENTITY_ATTRIBUTE` instance qui contient les attributs associés à ce `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="93ea2-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="93ea2-109">Obtient la valeur de l’attribut dans l’espace de noms spécifié, avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="93ea2-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="93ea2-110">Définit l’attribut qui possède l’espace de noms et le nom spécifié à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="93ea2-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93ea2-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93ea2-111">Requirements</span></span>  
 <span data-ttu-id="93ea2-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93ea2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ea2-113">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="93ea2-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="93ea2-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ea2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ea2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93ea2-115">See Also</span></span>  
 [<span data-ttu-id="93ea2-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="93ea2-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="93ea2-117">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="93ea2-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
