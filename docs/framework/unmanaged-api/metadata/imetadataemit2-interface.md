---
title: IMetaDataEmit2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 235134c66395f04a87ed4f3325f5cc4cd9fecfc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="dcb4f-102">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="dcb4f-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="dcb4f-103">Étend la [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalement pour offrir la possibilité de travailler avec les types génériques.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcb4f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dcb4f-104">Methods</span></span>  
  
|<span data-ttu-id="dcb4f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="dcb4f-105">Method</span></span>|<span data-ttu-id="dcb4f-106">Description</span><span class="sxs-lookup"><span data-stu-id="dcb4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcb4f-107">DefineGenericParam (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="dcb4f-108">Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="dcb4f-109">DefineMethodSpec (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="dcb4f-110">Crée une instance générique d’une méthode et obtient un jeton pour la définition.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="dcb4f-111">GetDeltaSaveSize (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="dcb4f-112">Obtient une valeur qui indique la différence de taille des données qui sont requis pour exprimer les modifications pour la session active de modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="dcb4f-113">ResetENCLog (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="dcb4f-114">Réinitialise le journal modifier et continuer et démarre une nouvelle session.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="dcb4f-115">SaveDelta (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="dcb4f-116">Enregistre les modifications de la session modifier et continuer actuelle dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="dcb4f-117">SaveDeltaToMemory (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="dcb4f-118">Enregistre les modifications de la session active de modifier et continuer à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="dcb4f-119">SaveDeltaToStream (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="dcb4f-120">Enregistre les modifications de la session modifier et continuer actuelle dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="dcb4f-121">SetGenericParamProps (méthode)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="dcb4f-122">Définit les valeurs de propriété pour la définition de paramètre générique référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="dcb4f-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dcb4f-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dcb4f-123">Requirements</span></span>  
 <span data-ttu-id="dcb4f-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcb4f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb4f-125">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dcb4f-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcb4f-126">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcb4f-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcb4f-127">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb4f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb4f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcb4f-128">See Also</span></span>  
 [<span data-ttu-id="dcb4f-129">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="dcb4f-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="dcb4f-130">IMetaDataEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="dcb4f-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
