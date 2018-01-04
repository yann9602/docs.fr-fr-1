---
title: "IMetaDataImport::GetModuleRefProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee230b691411c49ba4f0096d998ac229283fc02c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="f1dcf-102">IMetaDataImport::GetModuleRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="f1dcf-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="f1dcf-103">Obtient le nom du module référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1dcf-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1dcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1dcf-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1dcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f1dcf-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="f1dcf-106">[in] Le jeton de métadonnées ModuleRef qui fait référence au module pour obtenir des informations de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f1dcf-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="f1dcf-107">[out] Une mémoire tampon pour contenir le nom du module.</span><span class="sxs-lookup"><span data-stu-id="f1dcf-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f1dcf-108">[in] La taille demandée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="f1dcf-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f1dcf-109">[out] La taille retournée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="f1dcf-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1dcf-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f1dcf-110">Requirements</span></span>  
 <span data-ttu-id="f1dcf-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1dcf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1dcf-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1dcf-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1dcf-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1dcf-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1dcf-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1dcf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1dcf-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1dcf-115">See Also</span></span>  
 [<span data-ttu-id="f1dcf-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f1dcf-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f1dcf-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f1dcf-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
