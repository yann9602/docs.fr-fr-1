---
title: "ITypeName::GetNames, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ITypeName.GetNames
api_location: mscoree.dll
api_type: COM
f1_keywords: GetNames
helpviewer_keywords:
- ITypeName::GetNames method [.NET Framework hosting]
- GetNames method [.NET Framework hosting]
ms.assetid: e2a3637b-d1e9-4d93-9e9b-0555fbff793d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 353446dc98695dfb8b63ff1a9e9ee55b38b810d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="itypenamegetnames-method"></a><span data-ttu-id="2879e-102">ITypeName::GetNames, méthode</span><span class="sxs-lookup"><span data-stu-id="2879e-102">ITypeName::GetNames Method</span></span>
<span data-ttu-id="2879e-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2879e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2879e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2879e-104">Syntax</span></span>  
  
```  
HRESULT GetNames (  
    [in] DWORD           count,  
    [out] BSTR*          rgbszNames,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2879e-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2879e-105">Requirements</span></span>  
 <span data-ttu-id="2879e-106">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2879e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2879e-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2879e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2879e-108">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2879e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2879e-109">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2879e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2879e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2879e-110">See Also</span></span>  
 [<span data-ttu-id="2879e-111">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="2879e-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
