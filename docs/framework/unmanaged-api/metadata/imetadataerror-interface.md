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
ms.openlocfilehash: 9ae90221a1b305fdf09ae9583e720a2092289362
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="23cc5-102">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="23cc5-102">IMetaDataError Interface</span></span>
<span data-ttu-id="23cc5-103">Fournit un mécanisme de rappel pour signaler les erreurs pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="23cc5-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23cc5-104">Le `IMetaDataError` interface doit être implémentée par le client.</span><span class="sxs-lookup"><span data-stu-id="23cc5-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23cc5-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="23cc5-105">Methods</span></span>  
  
|<span data-ttu-id="23cc5-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="23cc5-106">Method</span></span>|<span data-ttu-id="23cc5-107">Description</span><span class="sxs-lookup"><span data-stu-id="23cc5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23cc5-108">OnError (méthode)</span><span class="sxs-lookup"><span data-stu-id="23cc5-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="23cc5-109">Fournit une notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="23cc5-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23cc5-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="23cc5-110">Requirements</span></span>  
 <span data-ttu-id="23cc5-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23cc5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23cc5-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23cc5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23cc5-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23cc5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23cc5-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23cc5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23cc5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23cc5-115">See Also</span></span>  
 [<span data-ttu-id="23cc5-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="23cc5-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
