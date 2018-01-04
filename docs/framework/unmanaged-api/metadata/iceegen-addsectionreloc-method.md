---
title: "ICeeGen::AddSectionReloc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AddSectionReloc
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e4bb3b1e436f51726ce50f80e1fd88c10f20fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="ab45a-102">ICeeGen::AddSectionReloc, méthode</span><span class="sxs-lookup"><span data-stu-id="ab45a-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="ab45a-103">Ajoute une instruction .reloc au code base.</span><span class="sxs-lookup"><span data-stu-id="ab45a-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="ab45a-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="ab45a-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab45a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab45a-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab45a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab45a-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="ab45a-107">[in] La section de code en mémoire à laquelle ajouter une instruction .reloc.</span><span class="sxs-lookup"><span data-stu-id="ab45a-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="ab45a-108">[in] Le décalage de la section.</span><span class="sxs-lookup"><span data-stu-id="ab45a-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="ab45a-109">[in] La section à laquelle `offset` fait référence.</span><span class="sxs-lookup"><span data-stu-id="ab45a-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="ab45a-110">[in] Parmi les [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) valeurs indiquant le genre d’instruction .reloc à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ab45a-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab45a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab45a-111">Requirements</span></span>  
 <span data-ttu-id="ab45a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab45a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab45a-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab45a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab45a-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab45a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab45a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab45a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab45a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab45a-116">See Also</span></span>  
 [<span data-ttu-id="ab45a-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="ab45a-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
