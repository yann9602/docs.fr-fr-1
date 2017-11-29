---
title: "ImportTypes, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes
helpviewer_keywords: ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b8fb83d4e3244010550cb21fedbc6c3b1c5d60d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="importtypes-method"></a><span data-ttu-id="268a2-102">ImportTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="268a2-102">ImportTypes Method</span></span>
<span data-ttu-id="268a2-103">Lance l’importation de types de chaque portée importée par [méthode ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="268a2-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="268a2-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="268a2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="268a2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="268a2-106">ID de l’assembly dans lequel importer.</span><span class="sxs-lookup"><span data-stu-id="268a2-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="268a2-107">ID du fichier à importer à partir de.</span><span class="sxs-lookup"><span data-stu-id="268a2-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="268a2-108">Portée de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="268a2-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="268a2-109">Reçoit le handle d’énumérateur pour les types dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="268a2-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="268a2-110">Si vous le souhaitez reçoit [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="268a2-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="268a2-111">Si vous le souhaitez reçoit le nombre de types dans l’étendue indiquée.</span><span class="sxs-lookup"><span data-stu-id="268a2-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="268a2-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="268a2-112">Return Value</span></span>  
 <span data-ttu-id="268a2-113">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="268a2-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="268a2-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="268a2-114">Requirements</span></span>  
 <span data-ttu-id="268a2-115">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="268a2-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268a2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="268a2-116">See Also</span></span>  
 [<span data-ttu-id="268a2-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="268a2-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="268a2-118">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="268a2-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="268a2-119">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="268a2-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
