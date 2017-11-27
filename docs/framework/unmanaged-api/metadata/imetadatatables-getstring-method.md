---
title: "IMetaDataTables::GetString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 687380d3a09a80db216aafbf1ee84c76e31bbf36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="02bb6-102">IMetaDataTables::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="02bb6-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="02bb6-103">Obtient la chaîne à l’index spécifié à partir de la colonne de table dans l’étendue actuelle de la référence.</span><span class="sxs-lookup"><span data-stu-id="02bb6-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02bb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02bb6-104">Syntax</span></span>  
  
```  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02bb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02bb6-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="02bb6-106">[in] Index auquel commencer à rechercher la valeur suivante.</span><span class="sxs-lookup"><span data-stu-id="02bb6-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="02bb6-107">[out] Pointeur vers un pointeur vers la valeur de la chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="02bb6-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02bb6-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="02bb6-108">Requirements</span></span>  
 <span data-ttu-id="02bb6-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02bb6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02bb6-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02bb6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02bb6-111">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02bb6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02bb6-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02bb6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02bb6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02bb6-113">See Also</span></span>  
 [<span data-ttu-id="02bb6-114">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="02bb6-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="02bb6-115">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="02bb6-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
