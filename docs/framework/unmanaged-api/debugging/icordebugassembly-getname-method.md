---
title: "ICorDebugAssembly::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d54139f8d7562f7f1ceb6e704731cd890a5f99df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="1a4c0-102">ICorDebugAssembly::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="1a4c0-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="1a4c0-103">Obtient le nom de l’assembly que cela `ICorDebugAssembly` représente l’instance.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a4c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a4c0-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a4c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a4c0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1a4c0-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1a4c0-107">[out] Pointeur vers un entier qui spécifie la longueur réelle du nom.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1a4c0-108">[out] Tableau qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a4c0-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a4c0-109">Remarks</span></span>  
 <span data-ttu-id="1a4c0-110">Le `GetName` méthode retourne le chemin d’accès et le nom complet de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1a4c0-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a4c0-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1a4c0-111">Requirements</span></span>  
 <span data-ttu-id="1a4c0-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a4c0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a4c0-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a4c0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a4c0-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a4c0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a4c0-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
