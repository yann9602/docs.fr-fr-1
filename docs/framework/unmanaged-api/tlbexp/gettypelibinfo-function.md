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
ms.openlocfilehash: a5dc55a9538798b81dce9db02583c271b9f2ed54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="77670-102">Fonction GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="77670-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="77670-103">Retourne des informations sur la bibliothèque de types spécifiée en examinant sa [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="77670-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77670-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77670-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="77670-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77670-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="77670-106">[in] Le nom de fichier de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="77670-107">[out] Le GUID de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="77670-108">[out] ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="77670-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) indicateur qui identifie le système d’exploitation cible pour la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="77670-110">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="77670-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="77670-111">[out] Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="77670-112">Par exemple, pour la version *x.y*, le numéro de version majeure est *x*.</span><span class="sxs-lookup"><span data-stu-id="77670-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="77670-113">[out] Numéro de version secondaire de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="77670-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="77670-114">Par exemple, pour la version *x.y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="77670-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77670-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="77670-115">Remarks</span></span>  
 <span data-ttu-id="77670-116">Le `GetTypeLibInfo` fonction est appelée par le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="77670-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="77670-117">Cet outil génère une bibliothèque de types décrivant les types dans un assembly du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="77670-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="77670-118">Si un paramètre est null, la fonction retourne un `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="77670-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="77670-119">Sinon, il retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="77670-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77670-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="77670-120">Requirements</span></span>  
 <span data-ttu-id="77670-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77670-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77670-122">**En-tête :** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="77670-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="77670-123">**Bibliothèque :** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="77670-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="77670-124">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77670-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77670-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77670-125">See Also</span></span>  
 [<span data-ttu-id="77670-126">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="77670-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="77670-127">[LoadTypeLibEx de le dont (fonction)](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="77670-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
