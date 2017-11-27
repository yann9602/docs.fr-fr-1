---
title: "IMetaDataAssemblyImport::GetAssemblyFromScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99734207f3df4582d28c0b318fee80d6bf8926bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="9dfc5-102">IMetaDataAssemblyImport::GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="9dfc5-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="9dfc5-103">Obtient un pointeur vers l’assembly dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="9dfc5-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dfc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dfc5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9dfc5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9dfc5-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="9dfc5-106">[out] Un pointeur vers les données récupérées `mdAssembly` jeton qui identifie l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9dfc5-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dfc5-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9dfc5-107">Requirements</span></span>  
 <span data-ttu-id="9dfc5-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dfc5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dfc5-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9dfc5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9dfc5-110">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9dfc5-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9dfc5-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dfc5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfc5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dfc5-112">See Also</span></span>  
 [<span data-ttu-id="9dfc5-113">IMetaDataAssemblyImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="9dfc5-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
