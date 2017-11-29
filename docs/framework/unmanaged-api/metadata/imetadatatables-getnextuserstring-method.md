---
title: "IMetaDataTables::GetNextUserString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 318bd7d05a7da5ce728ca80fe9bacfd84f501884
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="9d75b-102">IMetaDataTables::GetNextUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="9d75b-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="9d75b-103">Obtient l’index de la ligne qui contient la chaîne codée en dur suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d75b-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d75b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d75b-104">Syntax</span></span>  
  
```  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d75b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d75b-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="9d75b-106">[in] Une valeur d’index de la colonne de chaîne en cours.</span><span class="sxs-lookup"><span data-stu-id="9d75b-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="9d75b-107">[out] Pointeur vers l’index de ligne de la chaîne suivante dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="9d75b-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d75b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d75b-108">Remarks</span></span>  
 <span data-ttu-id="9d75b-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="9d75b-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9d75b-110">Pour plus d’informations sur la table GUID, consultez la documentation du Common Language Infrastructure (CLI), en particulier « Partition II : Metadata Definition et Semantics ».</span><span class="sxs-lookup"><span data-stu-id="9d75b-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9d75b-111">La documentation est disponible en ligne. Consultez [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) sur MSDN et [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) sur le site web d’Ecma International.</span><span class="sxs-lookup"><span data-stu-id="9d75b-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d75b-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d75b-112">Requirements</span></span>  
 <span data-ttu-id="9d75b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d75b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d75b-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d75b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d75b-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d75b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d75b-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d75b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d75b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d75b-117">See Also</span></span>  
 [<span data-ttu-id="9d75b-118">IMetaDataTables (Interface)</span><span class="sxs-lookup"><span data-stu-id="9d75b-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9d75b-119">IMetaDataTables2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="9d75b-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
