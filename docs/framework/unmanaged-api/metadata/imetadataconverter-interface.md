---
title: IMetaDataConverter, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="f9a21-102">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="f9a21-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="f9a21-103">Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.</span><span class="sxs-lookup"><span data-stu-id="f9a21-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9a21-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f9a21-104">Methods</span></span>  
  
|<span data-ttu-id="f9a21-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f9a21-105">Method</span></span>|<span data-ttu-id="f9a21-106">Description</span><span class="sxs-lookup"><span data-stu-id="f9a21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9a21-107">GetMetaDataFromTypeInfo (méthode)</span><span class="sxs-lookup"><span data-stu-id="f9a21-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="f9a21-108">Obtient un pointeur vers un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance qui représente la signature de métadonnées pour la bibliothèque de types référencée par le `ITypeInfo` instance.</span><span class="sxs-lookup"><span data-stu-id="f9a21-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="f9a21-109">GetMetaDataFromTypeLib (méthode)</span><span class="sxs-lookup"><span data-stu-id="f9a21-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="f9a21-110">Obtient un pointeur vers un `IMetaDataImport` instance qui représente la signature de métadonnées pour la bibliothèque de types représentée par le `ITypeLib` instance.</span><span class="sxs-lookup"><span data-stu-id="f9a21-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="f9a21-111">GetTypeLibFromMetaData (méthode)</span><span class="sxs-lookup"><span data-stu-id="f9a21-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="f9a21-112">Obtient un pointeur vers un `ITypeLib` instance qui représente la bibliothèque de types qui contient les noms de module et de bibliothèque spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f9a21-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9a21-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f9a21-113">Requirements</span></span>  
 <span data-ttu-id="f9a21-114">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a21-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a21-115">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f9a21-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9a21-116">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9a21-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9a21-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a21-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9a21-118">See Also</span></span>  
 [<span data-ttu-id="f9a21-119">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f9a21-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="f9a21-120">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="f9a21-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
