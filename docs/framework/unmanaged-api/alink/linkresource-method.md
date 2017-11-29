---
title: "LinkResource, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="eaef5-102">LinkResource, méthode</span><span class="sxs-lookup"><span data-stu-id="eaef5-102">LinkResource Method</span></span>
<span data-ttu-id="eaef5-103">Liens dans une ressource.</span><span class="sxs-lookup"><span data-stu-id="eaef5-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaef5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaef5-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eaef5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eaef5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="eaef5-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="eaef5-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="eaef5-107">Nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="eaef5-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="eaef5-108">Nouveau nom de fichier facultatif.</span><span class="sxs-lookup"><span data-stu-id="eaef5-108">Optional new file name.</span></span> <span data-ttu-id="eaef5-109">Si non NULL, `pszFileName` sera copié vers pszNewLocation.</span><span class="sxs-lookup"><span data-stu-id="eaef5-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="eaef5-110">Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="eaef5-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="eaef5-111">Accessibilité indicateurs tels que `mrPublic` et `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="eaef5-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="eaef5-112">Ce paramètre peut être passé à [DefineManifestResource, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="eaef5-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaef5-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eaef5-113">Return Value</span></span>  
 <span data-ttu-id="eaef5-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="eaef5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaef5-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eaef5-115">Requirements</span></span>  
 <span data-ttu-id="eaef5-116">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="eaef5-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaef5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eaef5-117">See Also</span></span>  
 [<span data-ttu-id="eaef5-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="eaef5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="eaef5-119">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="eaef5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="eaef5-120">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="eaef5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
