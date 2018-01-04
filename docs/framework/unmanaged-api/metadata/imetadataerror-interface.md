---
title: IMetaDataError, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError
helpviewer_keywords: IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4df7aa7400a180151de5420effc8738955d51c26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="be5ec-102">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="be5ec-102">IMetaDataError Interface</span></span>
<span data-ttu-id="be5ec-103">Fournit un mécanisme de rappel pour signaler les erreurs pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="be5ec-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be5ec-104">Le `IMetaDataError` interface doit être implémentée par le client.</span><span class="sxs-lookup"><span data-stu-id="be5ec-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be5ec-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="be5ec-105">Methods</span></span>  
  
|<span data-ttu-id="be5ec-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="be5ec-106">Method</span></span>|<span data-ttu-id="be5ec-107">Description</span><span class="sxs-lookup"><span data-stu-id="be5ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be5ec-108">OnError, méthode</span><span class="sxs-lookup"><span data-stu-id="be5ec-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="be5ec-109">Fournit une notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="be5ec-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be5ec-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be5ec-110">Requirements</span></span>  
 <span data-ttu-id="be5ec-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be5ec-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be5ec-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be5ec-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be5ec-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be5ec-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be5ec-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be5ec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5ec-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be5ec-115">See Also</span></span>  
 [<span data-ttu-id="be5ec-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="be5ec-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
