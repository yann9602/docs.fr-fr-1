---
title: IMetaDataFilter, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter
helpviewer_keywords: IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0918802a146940fb7579279e56f752bd114c746c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="0841c-102">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="0841c-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="0841c-103">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="0841c-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0841c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0841c-104">Methods</span></span>  
  
|<span data-ttu-id="0841c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0841c-105">Method</span></span>|<span data-ttu-id="0841c-106">Description</span><span class="sxs-lookup"><span data-stu-id="0841c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0841c-107">IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="0841c-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="0841c-108">Obtient une valeur qui indique si le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="0841c-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="0841c-109">MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="0841c-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="0841c-110">Définit une valeur qui indique que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="0841c-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="0841c-111">UnmarkAll, méthode</span><span class="sxs-lookup"><span data-stu-id="0841c-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="0841c-112">Supprime les marques de traitement de tous les jetons dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="0841c-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0841c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0841c-113">Requirements</span></span>  
 <span data-ttu-id="0841c-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0841c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0841c-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0841c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0841c-116">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0841c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0841c-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0841c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0841c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0841c-118">See Also</span></span>  
 [<span data-ttu-id="0841c-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="0841c-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
