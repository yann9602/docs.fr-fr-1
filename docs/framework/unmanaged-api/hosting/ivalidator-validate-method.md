---
title: "IValidator::Validate, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a74249cb806f332b3ae575223f237438da616972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="1f0fc-102">IValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="1f0fc-102">IValidator::Validate Method</span></span>
<span data-ttu-id="1f0fc-103">Valide le spécifié fichier exécutable portable (PE) ou un fichier Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="1f0fc-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f0fc-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f0fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f0fc-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="1f0fc-106">[in] Un pointeur vers un `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1f0fc-107">[in] Pointeur vers le domaine d’application dans lequel le fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="1f0fc-108">[in] Une combinaison d’opérations de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valeurs indiquant les validations qui doivent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="1f0fc-109">[in] Le nombre maximal d’erreurs autorisées avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="1f0fc-110">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1f0fc-111">[in] Chaîne qui spécifie le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="1f0fc-112">[in] Pointeur vers la mémoire tampon dans laquelle le fichier est stocké.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="1f0fc-113">[in] La taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="1f0fc-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0fc-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1f0fc-114">Requirements</span></span>  
 <span data-ttu-id="1f0fc-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f0fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f0fc-116">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="1f0fc-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="1f0fc-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f0fc-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f0fc-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f0fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f0fc-119">See Also</span></span>  
 
