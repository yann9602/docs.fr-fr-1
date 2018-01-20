---
title: "CorOpenFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4447f648277576169c9004d1880283728639c8f3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="coropenflags-enumeration"></a><span data-ttu-id="11ca5-102">CorOpenFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="11ca5-102">CorOpenFlags Enumeration</span></span>
<span data-ttu-id="11ca5-103">Contient des valeurs d'indicateurs qui contrôlent le comportement des métadonnées après ouverture des fichiers manifeste.</span><span class="sxs-lookup"><span data-stu-id="11ca5-103">Contains flag values that control metadata behavior upon opening manifest files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ca5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11ca5-104">Syntax</span></span>  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="11ca5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="11ca5-105">Members</span></span>  
  
|<span data-ttu-id="11ca5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="11ca5-106">Member</span></span>|<span data-ttu-id="11ca5-107">Description</span><span class="sxs-lookup"><span data-stu-id="11ca5-107">Description</span></span>|  
|------------|-----------------|  
|`ofRead`|<span data-ttu-id="11ca5-108">Indique que le fichier doit être ouvert en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="11ca5-108">Indicates that the file should be opened for reading only.</span></span>|  
|`ofWrite`|<span data-ttu-id="11ca5-109">Indique que le fichier doit être ouvert en écriture.</span><span class="sxs-lookup"><span data-stu-id="11ca5-109">Indicates that the file should be opened for writing.</span></span><br /><br /> <span data-ttu-id="11ca5-110">Si vous utilisez l'indicateur `ofWrite` lors de l'ouverture d'un fichier .winmd, vous devez aussi passer l'indicateur `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="11ca5-110">If you are using the `ofWrite` flag when opening a .winmd file, you should also pass the `ofNoTransform` flag.</span></span>|  
|`ofReadWriteMask`|<span data-ttu-id="11ca5-111">Un masque pour la lecture et l'écriture.</span><span class="sxs-lookup"><span data-stu-id="11ca5-111">A mask for reading and writing.</span></span>|  
|`ofCopyMemory`|<span data-ttu-id="11ca5-112">Indique que le fichier doit être lu en mémoire.</span><span class="sxs-lookup"><span data-stu-id="11ca5-112">Indicates that the file should be read into memory.</span></span> <span data-ttu-id="11ca5-113">Les métadonnées doivent gérer leur propre copie.</span><span class="sxs-lookup"><span data-stu-id="11ca5-113">Metadata should maintain its own copy.</span></span>|  
|`ofCacheImage`|<span data-ttu-id="11ca5-114">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="11ca5-114">Obsolete.</span></span> <span data-ttu-id="11ca5-115">Cet indicateur est ignoré.</span><span class="sxs-lookup"><span data-stu-id="11ca5-115">This flag is ignored.</span></span>|  
|`ofManifestMetadata`|<span data-ttu-id="11ca5-116">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="11ca5-116">Obsolete.</span></span> <span data-ttu-id="11ca5-117">Cet indicateur est ignoré.</span><span class="sxs-lookup"><span data-stu-id="11ca5-117">This flag is ignored.</span></span>|  
|`ofReadOnly`|<span data-ttu-id="11ca5-118">Indique que le fichier doit être ouvert pour lecture et qu’un appel à `QueryInterface` pour un [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) ne peut pas être établie.</span><span class="sxs-lookup"><span data-stu-id="11ca5-118">Indicates that the file should be opened for reading, and that a call to `QueryInterface` for an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) cannot be made.</span></span>|  
|`ofTakeOwnership`|<span data-ttu-id="11ca5-119">Indique que la mémoire a été allouée à l’aide d’un appel à [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) et sera libérée par les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="11ca5-119">Indicates that the memory was allocated using a call to [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) and will be freed by the metadata.</span></span>|  
|`ofNoTypeLib`|<span data-ttu-id="11ca5-120">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="11ca5-120">Obsolete.</span></span> <span data-ttu-id="11ca5-121">Cet indicateur est ignoré.</span><span class="sxs-lookup"><span data-stu-id="11ca5-121">This flag is ignored.</span></span>|  
|`ofNoTransform`|<span data-ttu-id="11ca5-122">Indique que les transformations automatiques de fichiers .winmd doivent être désactivées.</span><span class="sxs-lookup"><span data-stu-id="11ca5-122">Indicates that automatic transforms of .winmd files should be disabled.</span></span> <span data-ttu-id="11ca5-123">En d'autres termes, la projection d'un type Windows Runtime vers un type .NET Framework doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="11ca5-123">In other words, the projection of a Windows Runtime type to a .NET Framework type should be disabled.</span></span> <span data-ttu-id="11ca5-124">Pour plus d’informations, consultez [Underneath the Hood avec .NET et Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span><span class="sxs-lookup"><span data-stu-id="11ca5-124">For more information, see [Underneath the Hood with .NET and the Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).</span></span>|  
|`ofReserved1`|<span data-ttu-id="11ca5-125">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="11ca5-125">Reserved for internal use.</span></span>|  
|`ofReserved2`|<span data-ttu-id="11ca5-126">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="11ca5-126">Reserved for internal use.</span></span>|  
|`ofReserved`|<span data-ttu-id="11ca5-127">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="11ca5-127">Reserved for internal use.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11ca5-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="11ca5-128">Requirements</span></span>  
 <span data-ttu-id="11ca5-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11ca5-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11ca5-130">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="11ca5-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="11ca5-131">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11ca5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ca5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11ca5-132">See Also</span></span>  
 [<span data-ttu-id="11ca5-133">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="11ca5-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
