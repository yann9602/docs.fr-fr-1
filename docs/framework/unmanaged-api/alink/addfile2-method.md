---
title: "AddFile2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddFile2
- IALink2.AddFile2
api_location: alink.dll
api_type: COM
f1_keywords: AddFile2
helpviewer_keywords: AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd04b8435c7296b1c7b097ab426d103adaa0e993
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="addfile2-method"></a><span data-ttu-id="e990e-102">AddFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="e990e-102">AddFile2 Method</span></span>
<span data-ttu-id="e990e-103">Ajoute des fichiers à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e990e-103">Adds files to the assembly.</span></span> <span data-ttu-id="e990e-104">Peut également être utilisé pour créer des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="e990e-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e990e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e990e-105">Syntax</span></span>  
  
```  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e990e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e990e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e990e-107">ID de l’assembly auquel le fichier est ajouté.</span><span class="sxs-lookup"><span data-stu-id="e990e-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="e990e-108">Nom du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="e990e-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e990e-109">COM + `FileDef` indicateurs tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="e990e-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="e990e-110">`dwFlags`est passé à [DefineFile, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e990e-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e990e-111">Interface [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e990e-111">Interface to [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="e990e-112">Reçoit l’ID du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="e990e-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e990e-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e990e-113">Return Value</span></span>  
 <span data-ttu-id="e990e-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="e990e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e990e-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e990e-115">Requirements</span></span>  
 <span data-ttu-id="e990e-116">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="e990e-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e990e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e990e-117">See Also</span></span>  
 [<span data-ttu-id="e990e-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e990e-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e990e-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e990e-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e990e-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="e990e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
