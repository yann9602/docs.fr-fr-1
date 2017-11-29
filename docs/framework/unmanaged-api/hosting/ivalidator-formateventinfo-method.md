---
title: "IValidator::FormatEventInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0775bf5a2370d9d05899af5bc414caf08b3401fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="f46e5-102">IValidator::FormatEventInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f46e5-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="f46e5-103">Obtient le message d’erreur correspondant à l’erreur de validation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f46e5-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f46e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f46e5-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f46e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f46e5-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="f46e5-106">[in] La valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="f46e5-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="f46e5-107">[in] A `VEContext` instance qui contient les informations de contexte de l’erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="f46e5-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="f46e5-108">[dans, out] Chaîne qui contient le message d’erreur renvoyé.</span><span class="sxs-lookup"><span data-stu-id="f46e5-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="f46e5-109">[in] La longueur maximale du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f46e5-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="f46e5-110">[in] Un tableau sécurisé qui contient des paramètres supplémentaires décrivant l’erreur.</span><span class="sxs-lookup"><span data-stu-id="f46e5-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f46e5-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f46e5-111">Requirements</span></span>  
 <span data-ttu-id="f46e5-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f46e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f46e5-113">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="f46e5-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="f46e5-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f46e5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f46e5-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f46e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46e5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f46e5-116">See Also</span></span>  
 
