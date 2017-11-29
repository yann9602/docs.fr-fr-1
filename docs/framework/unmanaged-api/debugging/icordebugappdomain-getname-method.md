---
title: "ICorDebugAppDomain::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="42cce-102">ICorDebugAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="42cce-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="42cce-103">Obtient le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="42cce-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42cce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42cce-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42cce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42cce-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="42cce-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="42cce-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="42cce-107">Définissez cette valeur sur zéro pour mettre cette méthode en mode requête.</span><span class="sxs-lookup"><span data-stu-id="42cce-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="42cce-108">[out] Un pointeur vers la taille du nom ou le nombre de caractères réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="42cce-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="42cce-109">En mode requête, cette valeur permet de l’appelant savoir comment une mémoire tampon de taille à allouer pour le nom.</span><span class="sxs-lookup"><span data-stu-id="42cce-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="42cce-110">[out] Tableau qui stocke le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="42cce-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42cce-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="42cce-111">Remarks</span></span>  
 <span data-ttu-id="42cce-112">Un débogueur appelle la `GetName` méthode une fois pour obtenir la taille d’une mémoire tampon requise pour le nom.</span><span class="sxs-lookup"><span data-stu-id="42cce-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="42cce-113">Le débogueur alloue la mémoire tampon, puis appelle la méthode une deuxième fois pour remplir la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="42cce-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="42cce-114">Le premier appel, pour obtenir la taille du nom, est appelé *en mode requête*.</span><span class="sxs-lookup"><span data-stu-id="42cce-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42cce-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42cce-115">Requirements</span></span>  
 <span data-ttu-id="42cce-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42cce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42cce-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42cce-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42cce-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42cce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42cce-119">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42cce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
