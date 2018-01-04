---
title: "ICeeGen::GetSectionCreate, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionCreate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a069f65d3059bfa427ea20623ff9a2ac4049fd39
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="2ec52-102">ICeeGen::GetSectionCreate, méthode</span><span class="sxs-lookup"><span data-stu-id="2ec52-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="2ec52-103">Génère et obtient une section de code utilisant le nom spécifié et les valeurs d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="2ec52-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="2ec52-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="2ec52-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec52-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec52-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ec52-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ec52-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2ec52-107">[in] Un pointeur vers une chaîne qui spécifie le nom de la section doit être créé.</span><span class="sxs-lookup"><span data-stu-id="2ec52-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="2ec52-108">[in] Indicateurs qui spécifient des options.</span><span class="sxs-lookup"><span data-stu-id="2ec52-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="2ec52-109">[out] Pointeur vers la section de code nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="2ec52-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec52-110">Notes</span><span class="sxs-lookup"><span data-stu-id="2ec52-110">Remarks</span></span>  
 <span data-ttu-id="2ec52-111">Appelez `GetSectionCreate` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérés par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="2ec52-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec52-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ec52-112">Requirements</span></span>  
 <span data-ttu-id="2ec52-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec52-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec52-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ec52-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ec52-115">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ec52-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ec52-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec52-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec52-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec52-117">See Also</span></span>  
 [<span data-ttu-id="2ec52-118">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="2ec52-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
