---
title: "IMetaDataImport::GetPermissionSetProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPermissionSetProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2556c0beee7a21d2f01c403ab141054e5bf68177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="dd25a-102">IMetaDataImport::GetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="dd25a-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="dd25a-103">Obtient les métadonnées associées du <xref:System.Security.PermissionSet?displayProperty=nameWithType> représenté par le jeton d’autorisations spécifié.</span><span class="sxs-lookup"><span data-stu-id="dd25a-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd25a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd25a-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd25a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd25a-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="dd25a-106">[in] Le jeton de métadonnées d’autorisation qui représente la jeu d’autorisations à obtenir les propriétés de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="dd25a-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="dd25a-107">[out] Pointeur vers le jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="dd25a-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="dd25a-108">[out] Pointeur vers la signature de métadonnées binaires du jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="dd25a-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="dd25a-109">[out] La taille en octets de `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="dd25a-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd25a-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dd25a-110">Requirements</span></span>  
 <span data-ttu-id="dd25a-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd25a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd25a-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd25a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd25a-113">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd25a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd25a-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd25a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd25a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd25a-115">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 [<span data-ttu-id="dd25a-116">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd25a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dd25a-117">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd25a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
