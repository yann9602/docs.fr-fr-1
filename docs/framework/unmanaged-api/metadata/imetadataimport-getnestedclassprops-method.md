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
ms.openlocfilehash: 8a538cea5267b32790a9c656df9584d5ea31f54c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="dd61b-102">IMetaDataImport::GetNestedClassProps, méthode</span><span class="sxs-lookup"><span data-stu-id="dd61b-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="dd61b-103">Obtient le jeton TypeDef parent <xref:System.Type> spécifié type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="dd61b-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd61b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd61b-104">Syntax</span></span>  
  
```  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd61b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd61b-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="dd61b-106">[in] Jeton TypeDef représentant le <xref:System.Type> pour renvoyer la classe parente d’émission de jeton.</span><span class="sxs-lookup"><span data-stu-id="dd61b-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="dd61b-107">[out] Un pointeur vers le jeton TypeDef pour le <xref:System.Type> qui `tdNestedClass` est imbriqué dans.</span><span class="sxs-lookup"><span data-stu-id="dd61b-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd61b-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dd61b-108">Requirements</span></span>  
 <span data-ttu-id="dd61b-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd61b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd61b-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd61b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd61b-111">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd61b-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd61b-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd61b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd61b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd61b-113">See Also</span></span>  
 [<span data-ttu-id="dd61b-114">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd61b-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dd61b-115">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd61b-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
