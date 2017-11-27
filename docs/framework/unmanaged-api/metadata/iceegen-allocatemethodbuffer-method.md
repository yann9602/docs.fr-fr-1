---
title: "ICeeGen::AllocateMethodBuffer, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be288bedf12649b4356c68135868b9415840c4d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="7f5d9-102">ICeeGen::AllocateMethodBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="7f5d9-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="7f5d9-103">Crée une mémoire tampon de la taille spécifiée pour une méthode et obtient l’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="7f5d9-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5d9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f5d9-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f5d9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f5d9-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="7f5d9-107">[in] La longueur de la mémoire tampon à créer.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="7f5d9-108">[out] La mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="7f5d9-109">[out] L’adresse virtuelle relative de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7f5d9-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f5d9-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f5d9-110">Requirements</span></span>  
 <span data-ttu-id="7f5d9-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5d9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5d9-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f5d9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f5d9-113">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f5d9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f5d9-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5d9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5d9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f5d9-115">See Also</span></span>  
 [<span data-ttu-id="7f5d9-116">ICeeGen (Interface)</span><span class="sxs-lookup"><span data-stu-id="7f5d9-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
