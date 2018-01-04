---
title: "IMetaDataConverter::GetTypeLibFromMetaData, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter.GetTypeLibFromMetaData
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e7665eabf46d4bda822dcb41125ccfcee6d8516
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="d6f39-102">IMetaDataConverter::GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="d6f39-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="d6f39-103">Obtient un pointeur vers un `ITypeLib` instance qui représente la bibliothèque de types qui contient les noms de module et de bibliothèque spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d6f39-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6f39-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,   
    [in]  BSTR     strTlbName,   
    [out] ITypeLib **ppITL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6f39-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6f39-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="d6f39-106">[in] Le nom du module de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="d6f39-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="d6f39-107">[in] Le nom de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="d6f39-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="d6f39-108">[out] Un pointeur vers un emplacement qui reçoit l’adresse de le `ITypeLib` instance qui représente la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="d6f39-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6f39-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6f39-109">Requirements</span></span>  
 <span data-ttu-id="d6f39-110">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6f39-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6f39-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6f39-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6f39-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6f39-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6f39-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6f39-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f39-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6f39-114">See Also</span></span>  
 [<span data-ttu-id="d6f39-115">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="d6f39-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
