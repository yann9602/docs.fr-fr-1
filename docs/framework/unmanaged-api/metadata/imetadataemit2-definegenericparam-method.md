---
title: "IMetaDataEmit2::DefineGenericParam, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 598c616ca91b73d9cb184d9e431e75d00d3f9850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="0757a-102">IMetaDataEmit2::DefineGenericParam, méthode</span><span class="sxs-lookup"><span data-stu-id="0757a-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="0757a-103">Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="0757a-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0757a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0757a-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0757a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0757a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0757a-106">[in] Un `mdTypeDef` ou `mdMethodDef` jeton qui représente la méthode ou le constructeur pour laquelle vous définissez un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="0757a-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="0757a-107">[in] L’index du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="0757a-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="0757a-108">[in] Une valeur de la [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) énumération qui décrit le type du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="0757a-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="0757a-109">[in] Le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="0757a-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="0757a-110">[in] Ce paramètre est réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="0757a-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="0757a-111">[in] Tableau de contraintes de type terminant par zéro.</span><span class="sxs-lookup"><span data-stu-id="0757a-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="0757a-112">Membres de tableau doivent être un `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0757a-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="0757a-113">[out] Jeton qui représente le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="0757a-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0757a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0757a-114">Requirements</span></span>  
 <span data-ttu-id="0757a-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0757a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0757a-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0757a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0757a-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0757a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0757a-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0757a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0757a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0757a-119">See Also</span></span>  
 [<span data-ttu-id="0757a-120">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="0757a-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="0757a-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="0757a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
