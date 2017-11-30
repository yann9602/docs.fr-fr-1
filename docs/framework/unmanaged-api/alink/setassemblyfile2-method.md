---
title: "SetAssemblyFile2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetAssemblyFile2
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile2
helpviewer_keywords: SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7363a8f633d5f447f72e27ba03055f589564bdd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="85c00-102">SetAssemblyFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="85c00-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="85c00-103">Définit le nom et les options pour un nouvel assembly.</span><span class="sxs-lookup"><span data-stu-id="85c00-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="85c00-104">N’appelez pas cette méthode lorsque vous générez des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="85c00-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c00-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85c00-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85c00-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85c00-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="85c00-107">Nom du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="85c00-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="85c00-108">[IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="85c00-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="85c00-109">Les options sont représentées par [énumération AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="85c00-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="85c00-110">Reçoit l’ID unique de l’assembly en cours de construction.</span><span class="sxs-lookup"><span data-stu-id="85c00-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85c00-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="85c00-111">Return Value</span></span>  
 <span data-ttu-id="85c00-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="85c00-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85c00-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85c00-113">Requirements</span></span>  
 <span data-ttu-id="85c00-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="85c00-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c00-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c00-115">See Also</span></span>  
 [<span data-ttu-id="85c00-116">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="85c00-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="85c00-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="85c00-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="85c00-118">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="85c00-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
