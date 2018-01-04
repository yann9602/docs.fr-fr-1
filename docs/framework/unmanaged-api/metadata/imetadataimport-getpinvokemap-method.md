---
title: "IMetaDataImport::GetPinvokeMap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a28d628040a35d309515703563239a5f802dc4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="caa76-102">IMetaDataImport::GetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="caa76-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="caa76-103">Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.</span><span class="sxs-lookup"><span data-stu-id="caa76-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caa76-104">Syntax</span></span>  
  
```  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="caa76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="caa76-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="caa76-106">[in] Jeton FieldDef ou MethodDef pour obtenir les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="caa76-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="caa76-107">[out] Pointeur vers les indicateurs utilisés pour le mappage.</span><span class="sxs-lookup"><span data-stu-id="caa76-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="caa76-108">Cette valeur est un masque de bits de le [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="caa76-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="caa76-109">[out] Le nom de la DLL cible non managée.</span><span class="sxs-lookup"><span data-stu-id="caa76-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="caa76-110">[in] La taille en caractères larges de `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="caa76-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="caa76-111">[out] Le nombre de caractères étendus retournés dans `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="caa76-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="caa76-112">[out] Pointeur vers un jeton ModuleRef qui représente la bibliothèque d’objets cible non managée.</span><span class="sxs-lookup"><span data-stu-id="caa76-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa76-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="caa76-113">Requirements</span></span>  
 <span data-ttu-id="caa76-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa76-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa76-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="caa76-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="caa76-116">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="caa76-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caa76-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa76-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa76-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caa76-118">See Also</span></span>  
 [<span data-ttu-id="caa76-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="caa76-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="caa76-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="caa76-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
