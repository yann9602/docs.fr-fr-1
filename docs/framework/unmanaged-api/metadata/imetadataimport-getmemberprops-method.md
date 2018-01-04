---
title: "IMetaDataImport::GetMemberProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="a8e3c-102">IMetaDataImport::GetMemberProps, méthode</span><span class="sxs-lookup"><span data-stu-id="a8e3c-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="a8e3c-103">Obtient les informations de métadonnées, y compris le nom, le signature binaire et l’adresse virtuelle relative, de la <xref:System.Type> membre référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8e3c-104">Syntax</span></span>  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8e3c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8e3c-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="a8e3c-106">[in] Jeton qui référence le membre pour obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a8e3c-107">[out] Pointeur vers le jeton de métadonnées qui représente la classe du membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="a8e3c-108">[out] Le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="a8e3c-109">[in] La taille en caractères larges de la `szMember` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="a8e3c-110">[out] La taille en caractères étendus du nom retourné.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="a8e3c-111">[out] Toutes les valeurs d’indicateur appliqués au membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="a8e3c-112">[out] Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="a8e3c-113">[out] La taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="a8e3c-114">[out] Pointeur vers l’adresse virtuelle relative du membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="a8e3c-115">[out] Toutes les indicateurs d’implémentation de méthode associées au membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="a8e3c-116">[out] Un indicateur qui marque un <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="a8e3c-117">[out] Une valeur de chaîne constante retournée par ce membre.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="a8e3c-118">[out] La taille en caractères de `ppValue`, ou zéro si `ppValue` ne contient pas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a8e3c-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8e3c-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8e3c-119">Requirements</span></span>  
 <span data-ttu-id="a8e3c-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8e3c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8e3c-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8e3c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8e3c-122">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8e3c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8e3c-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8e3c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e3c-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8e3c-124">See Also</span></span>  
 [<span data-ttu-id="a8e3c-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a8e3c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a8e3c-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a8e3c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
