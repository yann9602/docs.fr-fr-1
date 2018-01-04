---
title: "IMetaDataImport::GetParamProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="690cb-102">IMetaDataImport::GetParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="690cb-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="690cb-103">Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="690cb-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="690cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="690cb-104">Syntax</span></span>  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="690cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="690cb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="690cb-106">[in] Jeton ParamDef qui représente le paramètre pour retourner les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="690cb-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="690cb-107">[out] Pointeur vers le jeton MethodDef représentant la méthode qui prend le paramètre.</span><span class="sxs-lookup"><span data-stu-id="690cb-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="690cb-108">[out] La position ordinale du paramètre dans la liste d’arguments de méthode.</span><span class="sxs-lookup"><span data-stu-id="690cb-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="690cb-109">[out] Une mémoire tampon pour contenir le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="690cb-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="690cb-110">[in] La taille demandée en caractères larges de `szName`.</span><span class="sxs-lookup"><span data-stu-id="690cb-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="690cb-111">[out] La taille retournée en caractères larges de `szName`.</span><span class="sxs-lookup"><span data-stu-id="690cb-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="690cb-112">[out] Pointeur vers un indicateur d’attribut associé au paramètre.</span><span class="sxs-lookup"><span data-stu-id="690cb-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="690cb-113">[out] Un pointeur vers un indicateur spécifiant que le paramètre est un <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="690cb-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="690cb-114">[out] Pointeur vers une chaîne constante retournée par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="690cb-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="690cb-115">[out] La taille de `ppValue` en caractères larges, ou zéro si `ppValue` ne contient pas de chaîne.</span><span class="sxs-lookup"><span data-stu-id="690cb-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="690cb-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="690cb-116">Requirements</span></span>  
 <span data-ttu-id="690cb-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="690cb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="690cb-118">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="690cb-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="690cb-119">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="690cb-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="690cb-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="690cb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690cb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="690cb-121">See Also</span></span>  
 [<span data-ttu-id="690cb-122">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="690cb-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="690cb-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="690cb-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
