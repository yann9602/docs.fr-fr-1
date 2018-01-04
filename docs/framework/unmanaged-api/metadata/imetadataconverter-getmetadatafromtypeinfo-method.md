---
title: "IMetaDataConverter::GetMetaDataFromTypeInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetMetaDataFromTypeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66e090efc9ce8a8fc1ca5de8d8f7a60f9ca17b9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="3a39b-102">IMetaDataConverter::GetMetaDataFromTypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="3a39b-102">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>
<span data-ttu-id="3a39b-103">Obtient un pointeur vers un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance qui représente la signature de métadonnées de la bibliothèque de types référencée par le `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="3a39b-103">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a39b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a39b-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a39b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a39b-105">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="3a39b-106">[in] Un pointeur vers un `ITypeInfo` objet qui fait référence à la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="3a39b-106">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="3a39b-107">[out] Un pointeur vers un emplacement qui reçoit l’adresse de le `IMetaDataImport` instance qui représente la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3a39b-107">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a39b-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3a39b-108">Requirements</span></span>  
 <span data-ttu-id="3a39b-109">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a39b-109">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a39b-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a39b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a39b-111">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a39b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a39b-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a39b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a39b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a39b-113">See Also</span></span>  
 [<span data-ttu-id="3a39b-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3a39b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3a39b-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3a39b-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
