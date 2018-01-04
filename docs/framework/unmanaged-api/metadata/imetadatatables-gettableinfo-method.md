---
title: "IMetaDataTables::GetTableInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ce9e3beb15724c7d7ddf02cbe7f83795d474139
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="efa6d-102">IMetaDataTables::GetTableInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="efa6d-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="efa6d-103">Obtient le nom, la taille de ligne, le nombre de lignes, le nombre de colonnes et les index de colonne clé de la table spécifiée.</span><span class="sxs-lookup"><span data-stu-id="efa6d-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efa6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efa6d-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efa6d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efa6d-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="efa6d-106">[in] L’identificateur de la table dont les propriétés à retourner.</span><span class="sxs-lookup"><span data-stu-id="efa6d-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="efa6d-107">[out] Pointeur vers la taille, en octets, d’une ligne de table.</span><span class="sxs-lookup"><span data-stu-id="efa6d-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="efa6d-108">[out] Pointeur vers le nombre de lignes dans la table.</span><span class="sxs-lookup"><span data-stu-id="efa6d-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="efa6d-109">[out] Pointeur vers le nombre de colonnes dans la table.</span><span class="sxs-lookup"><span data-stu-id="efa6d-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="efa6d-110">[out] Pointeur vers l’index de la colonne clée, ou -1 si la table ne comporte aucune colonne clé.</span><span class="sxs-lookup"><span data-stu-id="efa6d-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="efa6d-111">[out] Pointeur vers un pointeur vers le nom de table.</span><span class="sxs-lookup"><span data-stu-id="efa6d-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efa6d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="efa6d-112">Requirements</span></span>  
 <span data-ttu-id="efa6d-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efa6d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efa6d-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="efa6d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="efa6d-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="efa6d-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="efa6d-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efa6d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa6d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efa6d-117">See Also</span></span>  
 [<span data-ttu-id="efa6d-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="efa6d-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="efa6d-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="efa6d-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
