---
title: "ICeeGen::EmitString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.EmitString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f988e54a37212beeeebfbef15e6b148021e0b759
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="cd9b3-102">ICeeGen::EmitString, méthode</span><span class="sxs-lookup"><span data-stu-id="cd9b3-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="cd9b3-103">Émet la chaîne spécifiée dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="cd9b3-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd9b3-105">Syntax</span></span>  
  
```  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd9b3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd9b3-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="cd9b3-107">[in] Chaîne à émettre.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="cd9b3-108">[out] L’adresse virtuelle relative de la chaîne émise.</span><span class="sxs-lookup"><span data-stu-id="cd9b3-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9b3-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cd9b3-109">Requirements</span></span>  
 <span data-ttu-id="cd9b3-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9b3-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd9b3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd9b3-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd9b3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd9b3-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9b3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd9b3-114">See Also</span></span>  
 [<span data-ttu-id="cd9b3-115">ICeeGen (Interface)</span><span class="sxs-lookup"><span data-stu-id="cd9b3-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
