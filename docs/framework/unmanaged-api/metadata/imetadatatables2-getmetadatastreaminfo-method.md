---
title: "IMetaDataTables2::GetMetaDataStreamInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStreamInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06185d8a6f62d69e88aef7579ec40d7dcdec12a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="a4756-102">IMetaDataTables2::GetMetaDataStreamInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="a4756-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="a4756-103">Obtient le nom, la taille et le contenu du flux de métadonnées à l’index spécifié.</span><span class="sxs-lookup"><span data-stu-id="a4756-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4756-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4756-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4756-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4756-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="a4756-106">[in] Index de flux de métadonnées demandé.</span><span class="sxs-lookup"><span data-stu-id="a4756-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="a4756-107">[out] Pointeur vers le nom du flux de données.</span><span class="sxs-lookup"><span data-stu-id="a4756-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a4756-108">[out] Un pointeur vers le flux de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a4756-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="a4756-109">[out] La taille, en octets, de `ppv`.</span><span class="sxs-lookup"><span data-stu-id="a4756-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4756-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a4756-110">Requirements</span></span>  
 <span data-ttu-id="a4756-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4756-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4756-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a4756-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4756-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4756-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4756-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4756-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4756-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4756-115">See Also</span></span>  
 [<span data-ttu-id="a4756-116">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="a4756-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="a4756-117">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="a4756-117">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
