---
title: "IMetaDataImport2::GetMethodSpecProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetMethodSpecProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b07e79f3990782e18ffdc57e9bd75a0b62765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="07773-102">IMetaDataImport2::GetMethodSpecProps, méthode</span><span class="sxs-lookup"><span data-stu-id="07773-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="07773-103">Obtient le jeton de la signature de métadonnées de la méthode référencée par le MethodSpec spécifié.</span><span class="sxs-lookup"><span data-stu-id="07773-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07773-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07773-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="07773-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="07773-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="07773-106">[in] Jeton MethodSpec qui représente l’instanciation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="07773-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="07773-107">[out] Pointeur vers le jeton MethodDef ou MethodRef qui représente la définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="07773-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="07773-108">[out] Pointeur vers la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="07773-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="07773-109">[out] La taille, en octets, de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="07773-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07773-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="07773-110">Requirements</span></span>  
 <span data-ttu-id="07773-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07773-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07773-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="07773-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07773-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07773-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07773-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07773-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07773-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07773-115">See Also</span></span>  
 [<span data-ttu-id="07773-116">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="07773-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="07773-117">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="07773-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
