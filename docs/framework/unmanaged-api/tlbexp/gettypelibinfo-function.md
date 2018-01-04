---
title: Fonction GetTypeLibInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f6b1ad18809b46b7a2b38137231028f696d51b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="7e867-102">Fonction GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="7e867-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="7e867-103">Retourne des informations sur la bibliothèque de types spécifiée en examinant sa [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="7e867-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e867-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e867-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e867-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7e867-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="7e867-106">[in] Le nom de fichier de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="7e867-107">[out] Le GUID de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="7e867-108">[out] ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="7e867-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) indicateur qui identifie le système d’exploitation cible pour la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="7e867-110">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="7e867-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="7e867-111">[out] Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="7e867-112">Par exemple, pour la version *x.y*, le numéro de version majeure est *x*.</span><span class="sxs-lookup"><span data-stu-id="7e867-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="7e867-113">[out] Numéro de version secondaire de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="7e867-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="7e867-114">Par exemple, pour la version *x.y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="7e867-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e867-115">Notes</span><span class="sxs-lookup"><span data-stu-id="7e867-115">Remarks</span></span>  
 <span data-ttu-id="7e867-116">Le `GetTypeLibInfo` fonction est appelée par le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="7e867-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="7e867-117">Cet outil génère une bibliothèque de types décrivant les types dans un assembly du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7e867-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="7e867-118">Si un paramètre est null, la fonction retourne un `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="7e867-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="7e867-119">Sinon, il retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="7e867-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e867-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e867-120">Requirements</span></span>  
 <span data-ttu-id="7e867-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e867-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e867-122">**En-tête :** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="7e867-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="7e867-123">**Bibliothèque :** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="7e867-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="7e867-124">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e867-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e867-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e867-125">See Also</span></span>  
 [<span data-ttu-id="7e867-126">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="7e867-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="7e867-127">[LoadTypeLibEx de le dont (fonction)](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7e867-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
