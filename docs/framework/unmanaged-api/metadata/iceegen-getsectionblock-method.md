---
title: "ICeeGen::GetSectionBlock, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="5cd7c-102">ICeeGen::GetSectionBlock, méthode</span><span class="sxs-lookup"><span data-stu-id="5cd7c-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="5cd7c-103">Obtient un bloc de section de la base de code.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="5cd7c-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd7c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cd7c-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cd7c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cd7c-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="5cd7c-107">[in] La section à partir de laquelle récupérer un bloc de la base de code.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="5cd7c-108">[in] La longueur du bloc doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="5cd7c-109">[in] Octets par rapport au début de la section, avec lequel aligner le premier octet du bloc.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="5cd7c-110">Il s’agit de la position du bloc dans la section.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="5cd7c-111">[out] Pointeur vers un emplacement qui reçoit l’adresse du bloc récupéré.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cd7c-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5cd7c-112">Remarks</span></span>  
 <span data-ttu-id="5cd7c-113">Appelez `GetSectionBlock` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérés par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="5cd7c-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd7c-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5cd7c-114">Requirements</span></span>  
 <span data-ttu-id="5cd7c-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd7c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd7c-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5cd7c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cd7c-117">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cd7c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cd7c-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd7c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd7c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cd7c-119">See Also</span></span>  
 [<span data-ttu-id="5cd7c-120">ICeeGen (Interface)</span><span class="sxs-lookup"><span data-stu-id="5cd7c-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
