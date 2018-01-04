---
title: "IMetaDataImport::GetMemberRefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6cd229d9286dfe9c12a4c6f7e171f8bb634fcc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="16267-102">IMetaDataImport::GetMemberRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="16267-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="16267-103">Obtient les métadonnées associées au membre référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="16267-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16267-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16267-104">Syntax</span></span>  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16267-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16267-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="16267-106">[in] Jeton MemberRef pour retourner les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="16267-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="16267-107">[out] Un jeton TypeDef ou TypeRef ou TypeSpec qui représente la classe qui déclare le membre, ou un jeton ModuleRef qui représente la classe de module qui déclare le membre, ou MethodDef qui représente le membre.</span><span class="sxs-lookup"><span data-stu-id="16267-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="16267-108">[out] Un tampon pour chaîne pour le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="16267-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="16267-109">[in] La taille demandée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="16267-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="16267-110">[out] La taille retournée en caractères larges de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="16267-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="16267-111">[out] Pointeur vers la signature de métadonnées binaires pour le membre.</span><span class="sxs-lookup"><span data-stu-id="16267-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="16267-112">[out] La taille en octets de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="16267-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16267-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="16267-113">Requirements</span></span>  
 <span data-ttu-id="16267-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16267-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16267-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16267-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16267-116">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16267-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16267-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16267-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16267-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16267-118">See Also</span></span>  
 [<span data-ttu-id="16267-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="16267-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="16267-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="16267-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
