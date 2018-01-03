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
ms.workload: dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="77729-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="77729-102">ImportTypes2 Method</span></span>
<span data-ttu-id="77729-103">Lance l’importation de types.</span><span class="sxs-lookup"><span data-stu-id="77729-103">Initiates the import of types.</span></span> <span data-ttu-id="77729-104">Appelez cette méthode pour commencer à importer les types de chaque portée importée par [méthode ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="77729-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77729-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77729-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="77729-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77729-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="77729-107">ID de l’assembly dans lequel vous voulez importer.</span><span class="sxs-lookup"><span data-stu-id="77729-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="77729-108">ID du fichier à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="77729-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="77729-109">Portée de base zéro à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="77729-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="77729-110">Reçoit le handle d’énumérateur pour les types dans l’étendue donnée.</span><span class="sxs-lookup"><span data-stu-id="77729-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="77729-111">Si vous le souhaitez reçoit [IMetaDataImport2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="77729-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="77729-112">Si vous le souhaitez reçoit le nombre de types dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="77729-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77729-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="77729-113">Return Value</span></span>  
 <span data-ttu-id="77729-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="77729-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77729-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="77729-115">Requirements</span></span>  
 <span data-ttu-id="77729-116">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="77729-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77729-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77729-117">See Also</span></span>  
 [<span data-ttu-id="77729-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="77729-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="77729-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="77729-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="77729-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="77729-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
