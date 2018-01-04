---
title: "ICeeGen::GetString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7365cb96021438d9c7e287463782e1cb112a66a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="f8c9d-102">ICeeGen::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="f8c9d-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="f8c9d-103">Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f8c9d-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="f8c9d-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="f8c9d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c9d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8c9d-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8c9d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8c9d-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="f8c9d-107">[in] L’adresse virtuelle relative de la chaîne à retourner.</span><span class="sxs-lookup"><span data-stu-id="f8c9d-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="f8c9d-108">[out] La chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="f8c9d-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c9d-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8c9d-109">Requirements</span></span>  
 <span data-ttu-id="f8c9d-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c9d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c9d-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8c9d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8c9d-112">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8c9d-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8c9d-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c9d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c9d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8c9d-114">See Also</span></span>  
 [<span data-ttu-id="f8c9d-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="f8c9d-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
