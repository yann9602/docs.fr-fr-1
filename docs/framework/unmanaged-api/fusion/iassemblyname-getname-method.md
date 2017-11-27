---
title: "IAssemblyName::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.GetName
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 612efc9d5334fd34cc61f2243914de59370c45a0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="78cc7-102">IAssemblyName::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="78cc7-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="78cc7-103">Obtient le nom simple, non chiffré de l’assembly référencé par ce [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="78cc7-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78cc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78cc7-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78cc7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78cc7-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="78cc7-106">[dans, out] La taille de `pwzName` en caractères larges, y compris le caractère de marque de fin null.</span><span class="sxs-lookup"><span data-stu-id="78cc7-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="78cc7-107">[out] Une mémoire tampon pour contenir le nom de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="78cc7-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78cc7-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78cc7-108">Requirements</span></span>  
 <span data-ttu-id="78cc7-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78cc7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78cc7-110">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="78cc7-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="78cc7-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78cc7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78cc7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78cc7-112">See Also</span></span>  
 [<span data-ttu-id="78cc7-113">IAssemblyName (Interface)</span><span class="sxs-lookup"><span data-stu-id="78cc7-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
