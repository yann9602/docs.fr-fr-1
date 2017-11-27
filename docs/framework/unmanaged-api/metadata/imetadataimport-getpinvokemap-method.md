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
ms.openlocfilehash: adb6a9a5f53dcfd8ada5b3aa9d75daac18d50283
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="b7ed7-102">IMetaDataImport::GetPinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="b7ed7-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="b7ed7-103">Obtient un jeton ModuleRef pour représenter l'assembly cible d'un appel PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ed7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7ed7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b7ed7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7ed7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b7ed7-106">[in] Jeton FieldDef ou MethodDef pour obtenir les métadonnées de mappage PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="b7ed7-107">[out] Pointeur vers les indicateurs utilisés pour le mappage.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="b7ed7-108">Cette valeur est un masque de bits de le [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-108">This value is a bitmask from the [CorPinvokeMap](../../../../docs/framework/unmanaged-api/metadata/corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="b7ed7-109">[out] Le nom de la DLL cible non managée.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="b7ed7-110">[in] La taille en caractères larges de `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="b7ed7-111">[out] Le nombre de caractères étendus retournés dans `szImportName`.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="b7ed7-112">[out] Pointeur vers un jeton ModuleRef qui représente la bibliothèque d’objets cible non managée.</span><span class="sxs-lookup"><span data-stu-id="b7ed7-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ed7-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b7ed7-113">Requirements</span></span>  
 <span data-ttu-id="b7ed7-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ed7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ed7-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7ed7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7ed7-116">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7ed7-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7ed7-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ed7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ed7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7ed7-118">See Also</span></span>  
 [<span data-ttu-id="b7ed7-119">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="b7ed7-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b7ed7-120">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="b7ed7-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
