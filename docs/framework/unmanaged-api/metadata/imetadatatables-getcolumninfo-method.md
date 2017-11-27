---
title: "IMetaDataTables::GetColumnInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 939085294666a233341f65a8f5736d9dce201470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a><span data-ttu-id="f3fc7-102">IMetaDataTables::GetColumnInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f3fc7-102">IMetaDataTables::GetColumnInfo Method</span></span>
<span data-ttu-id="f3fc7-103">Obtient les données relatives à la colonne spécifiée dans la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-103">Gets data about the specified column in the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3fc7-104">Syntax</span></span>  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3fc7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3fc7-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="f3fc7-106">[in] Index de la table souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-106">[in] The index of the desired table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="f3fc7-107">[in] Index de la colonne souhaitée.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-107">[in] The index of the desired column.</span></span>  
  
 `poCol`  
 <span data-ttu-id="f3fc7-108">[out] Pointeur vers l’offset de la colonne dans la ligne.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-108">[out] A pointer to the offset of the column in the row.</span></span>  
  
 `pcbCol`  
 <span data-ttu-id="f3fc7-109">[out] Pointeur vers la taille, en octets, de la colonne.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-109">[out] A pointer to the size, in bytes, of the column.</span></span>  
  
 `pType`  
 <span data-ttu-id="f3fc7-110">[out] Pointeur vers le type des valeurs dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-110">[out] A pointer to the type of the values in the column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="f3fc7-111">[out] Pointeur vers un pointeur vers le nom de colonne.</span><span class="sxs-lookup"><span data-stu-id="f3fc7-111">[out] A pointer to a pointer to the column name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fc7-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f3fc7-112">Requirements</span></span>  
 <span data-ttu-id="f3fc7-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3fc7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fc7-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f3fc7-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3fc7-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f3fc7-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3fc7-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fc7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fc7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3fc7-117">See Also</span></span>  
 [<span data-ttu-id="f3fc7-118">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="f3fc7-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="f3fc7-119">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="f3fc7-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
