---
title: "IMetaDataImport::GetTypeDefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="bf0ed-102">IMetaDataImport::GetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf0ed-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="bf0ed-103">Retourne des informations de métadonnées pour le <xref:System.Type> représenté par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf0ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf0ed-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf0ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf0ed-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bf0ed-106">[in] Le jeton TypeDef qui représente le type à retourner les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="bf0ed-107">[out] Une mémoire tampon contenant le nom de type.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="bf0ed-108">[in] La taille en caractères larges de `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="bf0ed-109">[out] Le nombre de caractères étendus retournés dans `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="bf0ed-110">[out] Pointeur vers tous les indicateurs qui modifient la définition de type.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="bf0ed-111">Cette valeur est un masque de bits de le [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="bf0ed-112">[out] Un jeton de métadonnées TypeDef ou TypeRef qui représente le type de base du type demandé.</span><span class="sxs-lookup"><span data-stu-id="bf0ed-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf0ed-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf0ed-113">Requirements</span></span>  
 <span data-ttu-id="bf0ed-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf0ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf0ed-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf0ed-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf0ed-116">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf0ed-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf0ed-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf0ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf0ed-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf0ed-118">See Also</span></span>  
 [<span data-ttu-id="bf0ed-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="bf0ed-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bf0ed-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="bf0ed-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
