---
title: "IMetaDataImport::GetTypeRefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23dbfe2468088da5e02fb7156606af5f3fa51044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="ddd5b-102">IMetaDataImport::GetTypeRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="ddd5b-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="ddd5b-103">Obtient les métadonnées associées du <xref:System.Type> référencé par le jeton TypeRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddd5b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddd5b-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddd5b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ddd5b-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="ddd5b-106">[in] Le jeton TypeRef qui représente le type à retourner les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="ddd5b-107">[out] Pointeur vers la portée dans laquelle la référence est faite.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="ddd5b-108">Cette valeur est un jeton AssemblyRef ou ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="ddd5b-109">[out] Une mémoire tampon contenant le nom de type.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ddd5b-110">[in] La taille demandée en caractères larges de `szName`.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ddd5b-111">[out] La taille retournée en caractères larges de `szName`.</span><span class="sxs-lookup"><span data-stu-id="ddd5b-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddd5b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ddd5b-112">Requirements</span></span>  
 <span data-ttu-id="ddd5b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddd5b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddd5b-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddd5b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddd5b-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddd5b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddd5b-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddd5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd5b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddd5b-117">See Also</span></span>  
 [<span data-ttu-id="ddd5b-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ddd5b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ddd5b-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ddd5b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
