---
title: "IMetaDataAssemblyEmit::SetExportedTypeProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c41cc2c6433139f1e1f355585e4af0a8f01c7c94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="2773d-102">IMetaDataAssemblyEmit::SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="2773d-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>
<span data-ttu-id="2773d-103">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2773d-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2773d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2773d-104">Syntax</span></span>  
  
```  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,   
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2773d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2773d-105">Parameters</span></span>  
 `ct`  
 <span data-ttu-id="2773d-106">[in] Le jeton de métadonnées qui spécifie le `ExportedType` structure de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2773d-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="2773d-107">[in] Le jeton, de type `File`, `AssemblyRef`, ou `ExportedType`, qui spécifie la façon dont ce type est implémenté.</span><span class="sxs-lookup"><span data-stu-id="2773d-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="2773d-108">[in] Le `TypeDef` jeton référencé dans le fichier de code.</span><span class="sxs-lookup"><span data-stu-id="2773d-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="2773d-109">[in] Combinaison de bits de valeurs qui spécifient les attributs du type.</span><span class="sxs-lookup"><span data-stu-id="2773d-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2773d-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2773d-110">Remarks</span></span>  
 <span data-ttu-id="2773d-111">Pour créer un `ExportedType` structure des métadonnées, utilisez le [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="2773d-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2773d-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2773d-112">Requirements</span></span>  
 <span data-ttu-id="2773d-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2773d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2773d-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2773d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2773d-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2773d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2773d-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2773d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2773d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2773d-117">See Also</span></span>  
 [<span data-ttu-id="2773d-118">IMetaDataAssemblyEmit (Interface)</span><span class="sxs-lookup"><span data-stu-id="2773d-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
