---
title: IDefinitionIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a63436f107a2604fd5620854339447a4af254e52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="d180a-102">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="d180a-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="d180a-103">Représente la signature unique du code qui définit l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="d180a-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d180a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d180a-104">Methods</span></span>  
  
|<span data-ttu-id="d180a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d180a-105">Method</span></span>|<span data-ttu-id="d180a-106">Description</span><span class="sxs-lookup"><span data-stu-id="d180a-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="d180a-107">Obtient un pointeur d’interface vers un nouveau `IDefinitionIdentity` objet qui est identique à ce `IDefinitionIdentity`, à l’exception des modifications d’attribut spécifiées.</span><span class="sxs-lookup"><span data-stu-id="d180a-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="d180a-108">Obtient un pointeur d’interface vers un [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objet qui contient les attributs associés à ce `IDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="d180a-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="d180a-109">Obtient la valeur de l’attribut avec le nom spécifié dans l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="d180a-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="d180a-110">Définit l’attribut qui porte le nom spécifié dans l’espace de noms spécifié à la valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d180a-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d180a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d180a-111">Requirements</span></span>  
 <span data-ttu-id="d180a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d180a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d180a-113">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="d180a-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d180a-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d180a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d180a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d180a-115">See Also</span></span>  
 [<span data-ttu-id="d180a-116">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="d180a-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
