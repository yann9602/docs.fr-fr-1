---
title: "ImportTypes2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportTypes2
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes2
helpviewer_keywords: ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61d707cdd827b5e435c961a14e67170ab0e2bc90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="abc02-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="abc02-102">ImportTypes2 Method</span></span>
<span data-ttu-id="abc02-103">Lance l’importation de types.</span><span class="sxs-lookup"><span data-stu-id="abc02-103">Initiates the import of types.</span></span> <span data-ttu-id="abc02-104">Appelez cette méthode pour commencer à importer les types de chaque portée importée par [méthode ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="abc02-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc02-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abc02-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="abc02-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="abc02-107">ID de l’assembly dans lequel vous voulez importer.</span><span class="sxs-lookup"><span data-stu-id="abc02-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="abc02-108">ID du fichier à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="abc02-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="abc02-109">Portée de base zéro à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="abc02-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="abc02-110">Reçoit le handle d’énumérateur pour les types dans l’étendue donnée.</span><span class="sxs-lookup"><span data-stu-id="abc02-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="abc02-111">Si vous le souhaitez reçoit [IMetaDataImport2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="abc02-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="abc02-112">Si vous le souhaitez reçoit le nombre de types dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="abc02-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abc02-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="abc02-113">Return Value</span></span>  
 <span data-ttu-id="abc02-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="abc02-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc02-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="abc02-115">Requirements</span></span>  
 <span data-ttu-id="abc02-116">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="abc02-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc02-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abc02-117">See Also</span></span>  
 [<span data-ttu-id="abc02-118">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="abc02-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="abc02-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="abc02-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="abc02-120">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="abc02-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
