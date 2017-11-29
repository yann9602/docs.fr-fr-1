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
ms.openlocfilehash: 7c0afbb9be9af3ffe69ddfcac85b70de53a391ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="f2da2-102">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="f2da2-102">IMetaDataFilter Interface</span></span>
<span data-ttu-id="f2da2-103">Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.</span><span class="sxs-lookup"><span data-stu-id="f2da2-103">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2da2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f2da2-104">Methods</span></span>  
  
|<span data-ttu-id="f2da2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f2da2-105">Method</span></span>|<span data-ttu-id="f2da2-106">Description</span><span class="sxs-lookup"><span data-stu-id="f2da2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2da2-107">IsTokenMarked (méthode)</span><span class="sxs-lookup"><span data-stu-id="f2da2-107">IsTokenMarked Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="f2da2-108">Obtient une valeur qui indique si le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="f2da2-108">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="f2da2-109">MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="f2da2-109">MarkToken Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|<span data-ttu-id="f2da2-110">Définit une valeur qui indique que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="f2da2-110">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="f2da2-111">UnmarkAll (méthode)</span><span class="sxs-lookup"><span data-stu-id="f2da2-111">UnmarkAll Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|<span data-ttu-id="f2da2-112">Supprime les marques de traitement de tous les jetons dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="f2da2-112">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2da2-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2da2-113">Requirements</span></span>  
 <span data-ttu-id="f2da2-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2da2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2da2-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2da2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2da2-116">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2da2-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2da2-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2da2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2da2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2da2-118">See Also</span></span>  
 [<span data-ttu-id="f2da2-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f2da2-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
