---
title: "IMetaDataImport::GetNestedClassProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNestedClassProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bbfe382a9a2fdf8ece1015ee73c3d9ef604ec7e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="d1d44-102">IMetaDataImport::GetNestedClassProps, méthode</span><span class="sxs-lookup"><span data-stu-id="d1d44-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="d1d44-103">Obtient le jeton TypeDef parent <xref:System.Type> spécifié type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="d1d44-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1d44-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1d44-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1d44-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="d1d44-106">[in] Jeton TypeDef représentant le <xref:System.Type> pour renvoyer la classe parente d’émission de jeton.</span><span class="sxs-lookup"><span data-stu-id="d1d44-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="d1d44-107">[out] Un pointeur vers le jeton TypeDef pour le <xref:System.Type> qui `tdNestedClass` est imbriqué dans.</span><span class="sxs-lookup"><span data-stu-id="d1d44-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d44-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1d44-108">Requirements</span></span>  
 <span data-ttu-id="d1d44-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d44-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d44-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1d44-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1d44-111">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1d44-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1d44-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d44-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d44-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1d44-113">See Also</span></span>  
 [<span data-ttu-id="d1d44-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d1d44-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d1d44-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d1d44-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
