---
title: AddFile Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 943ff2901ee0888860941e86d589060de729907d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="addfile-method1"></a><span data-ttu-id="e55e2-102">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="e55e2-102">AddFile Method1</span></span>
<span data-ttu-id="e55e2-103">Ajoute des fichiers à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e55e2-103">Adds files to the assembly.</span></span> <span data-ttu-id="e55e2-104">Peut également être utilisé pour créer des modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="e55e2-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e55e2-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e55e2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e55e2-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e55e2-107">ID unique de l’assembly à augmenter.</span><span class="sxs-lookup"><span data-stu-id="e55e2-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="e55e2-108">Nom qualifié complet du fichier à ajouter.</span><span class="sxs-lookup"><span data-stu-id="e55e2-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e55e2-109">Indicateurs de COM + FileDef tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="e55e2-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="e55e2-110">`dwFlags`est passé à [DefineFile, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e55e2-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e55e2-111">[IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface à utiliser pour émettre des métadonnées, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e55e2-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="e55e2-112">Pointeur vers l’emplacement de stockage de l’ID unique du fichier ajouté.</span><span class="sxs-lookup"><span data-stu-id="e55e2-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e55e2-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e55e2-113">Return Value</span></span>  
 <span data-ttu-id="e55e2-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="e55e2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e55e2-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e55e2-115">Requirements</span></span>  
 <span data-ttu-id="e55e2-116">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="e55e2-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e55e2-117">See Also</span></span>  
 [<span data-ttu-id="e55e2-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e55e2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e55e2-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e55e2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e55e2-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="e55e2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
