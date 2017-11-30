---
title: "ICeeGen::TruncateSection, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.TruncateSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 204c71b55c4ba2ec1e3b137137d8f08845b12e49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="7f90b-102">ICeeGen::TruncateSection, méthode</span><span class="sxs-lookup"><span data-stu-id="7f90b-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="7f90b-103">Tronque la section de code spécifié par la longueur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7f90b-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="7f90b-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="7f90b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f90b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f90b-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f90b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f90b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7f90b-107">[in] La section à tronquer.</span><span class="sxs-lookup"><span data-stu-id="7f90b-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="7f90b-108">[in] La longueur, en octets, de laquelle tronquer la section.</span><span class="sxs-lookup"><span data-stu-id="7f90b-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f90b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7f90b-109">Remarks</span></span>  
 <span data-ttu-id="7f90b-110">Appelez `TruncateSection` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérés par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="7f90b-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f90b-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f90b-111">Requirements</span></span>  
 <span data-ttu-id="7f90b-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f90b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f90b-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f90b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f90b-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f90b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f90b-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f90b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f90b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f90b-116">See Also</span></span>  
 [<span data-ttu-id="7f90b-117">ICeeGen (Interface)</span><span class="sxs-lookup"><span data-stu-id="7f90b-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
