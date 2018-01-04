---
title: "IMetaDataImport::GetTypeSpecFromToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeSpecFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10d4d9dcad2494410cc361617d5292c519b6dc00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="2af62-102">IMetaDataImport::GetTypeSpecFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="2af62-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="2af62-103">Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="2af62-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2af62-104">Syntax</span></span>  
  
```  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2af62-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2af62-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="2af62-106">[in] Le jeton TypeSpec associé à la signature de métadonnées demandé.</span><span class="sxs-lookup"><span data-stu-id="2af62-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="2af62-107">[out] Pointeur vers la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="2af62-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="2af62-108">[out] La taille, en octets, de la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2af62-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2af62-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2af62-109">Return Value</span></span>  
 <span data-ttu-id="2af62-110">HRESULT qui indique la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="2af62-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="2af62-111">Échecs peuvent être testés avec la macro FAILED.</span><span class="sxs-lookup"><span data-stu-id="2af62-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af62-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2af62-112">Requirements</span></span>  
 <span data-ttu-id="2af62-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af62-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af62-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2af62-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2af62-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2af62-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2af62-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af62-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2af62-117">See Also</span></span>  
 [<span data-ttu-id="2af62-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2af62-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2af62-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2af62-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
