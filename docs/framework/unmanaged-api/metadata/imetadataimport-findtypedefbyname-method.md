---
title: "IMetaDataImport::FindTypeDefByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeDefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b3a5f9ff15e2b94e6d5c5e885605d8eabae711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="9c72e-102">IMetaDataImport::FindTypeDefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="9c72e-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="9c72e-103">Obtient un pointeur vers les métadonnées TypeDef jeton pour la <xref:System.Type> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c72e-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c72e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c72e-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c72e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c72e-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="9c72e-106">[in] Le nom du type pour lequel obtenir le jeton TypeDef.</span><span class="sxs-lookup"><span data-stu-id="9c72e-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="9c72e-107">[in] Un jeton TypeDef ou TypeRef qui représente la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="9c72e-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="9c72e-108">Si le type à rechercher n’est pas une classe imbriquée, définissez cette valeur sur NULL.</span><span class="sxs-lookup"><span data-stu-id="9c72e-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="9c72e-109">[out] Pointeur vers le jeton TypeDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="9c72e-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c72e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9c72e-110">Requirements</span></span>  
 <span data-ttu-id="9c72e-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c72e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c72e-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c72e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c72e-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c72e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c72e-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c72e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c72e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c72e-115">See Also</span></span>  
 [<span data-ttu-id="9c72e-116">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c72e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9c72e-117">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="9c72e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
