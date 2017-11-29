---
title: "IMetaDataImport::CloseEnum, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 80e156cd92519fc78f2a3076d03b279b7a63c1d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="4a7ed-102">IMetaDataImport::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="4a7ed-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="4a7ed-103">Ferme l’énumérateur qui est identifié par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a7ed-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a7ed-104">Syntax</span></span>  
  
```  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a7ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a7ed-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4a7ed-106">[in] Le handle pour l’énumérateur à fermer.</span><span class="sxs-lookup"><span data-stu-id="4a7ed-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a7ed-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4a7ed-107">Remarks</span></span>  
 <span data-ttu-id="4a7ed-108">Le handle spécifié par `hEnum` est obtenu à partir d’une précédente `Enum` *nom* appeler (par exemple, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="4a7ed-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a7ed-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4a7ed-109">Requirements</span></span>  
 <span data-ttu-id="4a7ed-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a7ed-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a7ed-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a7ed-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a7ed-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a7ed-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a7ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7ed-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a7ed-114">See Also</span></span>  
 [<span data-ttu-id="4a7ed-115">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="4a7ed-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4a7ed-116">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="4a7ed-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
