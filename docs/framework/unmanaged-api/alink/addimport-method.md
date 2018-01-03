---
title: AddImport Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="f1855-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="f1855-102">AddImport Method1</span></span>
<span data-ttu-id="f1855-103">Ajoute des importations à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f1855-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1855-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1855-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1855-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f1855-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f1855-106">ID unique de l’assembly à augmenter.</span><span class="sxs-lookup"><span data-stu-id="f1855-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="f1855-107">ID unique récupéré à partir de [méthode ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="f1855-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f1855-108">Indicateurs de COM + FileDef tels que `ffContainsNoMetaData` et `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="f1855-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="f1855-109">`dwFlags`est passé à [DefineFile, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f1855-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="f1855-110">Pointeur vers le jeton qui reçoit l’ID pour le fichier résultant.</span><span class="sxs-lookup"><span data-stu-id="f1855-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1855-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f1855-111">Return Value</span></span>  
 <span data-ttu-id="f1855-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f1855-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1855-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f1855-113">Requirements</span></span>  
 <span data-ttu-id="f1855-114">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="f1855-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1855-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1855-115">See Also</span></span>  
 [<span data-ttu-id="f1855-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f1855-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f1855-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f1855-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f1855-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="f1855-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
