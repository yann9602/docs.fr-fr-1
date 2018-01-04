---
title: COR_FIELD_OFFSET, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD_OFFSET
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_FIELD_OFFSET
helpviewer_keywords: COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed41538ae4c1e70843c613493eee9d632dff5f91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="ed51a-102">COR_FIELD_OFFSET, structure</span><span class="sxs-lookup"><span data-stu-id="ed51a-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="ed51a-103">Stocke l'offset, dans une classe, du champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="ed51a-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed51a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed51a-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="ed51a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ed51a-105">Members</span></span>  
  
|<span data-ttu-id="ed51a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ed51a-106">Member</span></span>|<span data-ttu-id="ed51a-107">Description</span><span class="sxs-lookup"><span data-stu-id="ed51a-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="ed51a-108">Un `mdFieldDef` jeton de métadonnées qui représente le champ.</span><span class="sxs-lookup"><span data-stu-id="ed51a-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="ed51a-109">Offset du champ dans sa classe.</span><span class="sxs-lookup"><span data-stu-id="ed51a-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed51a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ed51a-110">Remarks</span></span>  
 <span data-ttu-id="ed51a-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) et [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) méthodes prennent un paramètre de type `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="ed51a-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed51a-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed51a-112">Requirements</span></span>  
 <span data-ttu-id="ed51a-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed51a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed51a-114">**En-tête :** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ed51a-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="ed51a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed51a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed51a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed51a-116">See Also</span></span>  
 [<span data-ttu-id="ed51a-117">Structures de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ed51a-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="ed51a-118">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ed51a-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ed51a-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ed51a-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
