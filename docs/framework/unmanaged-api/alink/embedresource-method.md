---
title: "EmbedResource, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 815e4b6abbb56b0998a12c096f0ba7cb678778ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="bdb5f-102">EmbedResource, méthode</span><span class="sxs-lookup"><span data-stu-id="bdb5f-102">EmbedResource Method</span></span>
<span data-ttu-id="bdb5f-103">Déclare une ressource incorporée.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-103">Declares an embedded resource.</span></span> <span data-ttu-id="bdb5f-104">Cette méthode n’incorpore pas réellement la ressource.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb5f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdb5f-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdb5f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdb5f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bdb5f-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="bdb5f-108">ID de jeton ou l’assembly du fichier qui contient la ressource de fichier.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="bdb5f-109">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="bdb5f-110">Décalage de la ressource adresse RVA.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bdb5f-111">Accessibilité indicateurs tels que `mrPublic` et `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="bdb5f-112">Ces indicateurs peuvent être passés à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="bdb5f-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdb5f-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bdb5f-113">Return Value</span></span>  
 <span data-ttu-id="bdb5f-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb5f-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdb5f-115">Requirements</span></span>  
 <span data-ttu-id="bdb5f-116">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="bdb5f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb5f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdb5f-117">See Also</span></span>  
 [<span data-ttu-id="bdb5f-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="bdb5f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bdb5f-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="bdb5f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bdb5f-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="bdb5f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
