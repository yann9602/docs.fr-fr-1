---
title: "ExportNestedType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedType
helpviewer_keywords: ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6d40fffb2d40012d69599ad1bfcdbdaf454aa02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="e1b23-102">ExportNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="e1b23-102">ExportNestedType Method</span></span>
<span data-ttu-id="e1b23-103">Spécifie les types imbriqués comme étant exportable.</span><span class="sxs-lookup"><span data-stu-id="e1b23-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="e1b23-104">Le [ExportType, méthode](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) peut également exporter les types imbriqués, mais cette méthode est plus rapide.</span><span class="sxs-lookup"><span data-stu-id="e1b23-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b23-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1b23-105">Syntax</span></span>  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1b23-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1b23-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e1b23-107">ID de l’assembly à exporter à partir de.</span><span class="sxs-lookup"><span data-stu-id="e1b23-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e1b23-108">Jeton de fichier ou l’Assembly du fichier qui définit le type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="e1b23-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="e1b23-109">Type de jeton de type à rendre exportable.</span><span class="sxs-lookup"><span data-stu-id="e1b23-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="e1b23-110">Jeton de type parent.</span><span class="sxs-lookup"><span data-stu-id="e1b23-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e1b23-111">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="e1b23-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e1b23-112">`ComType`indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e1b23-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e1b23-113">Cette valeur peut être passée à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e1b23-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e1b23-114">Reçoit le jeton pour le type exporté.</span><span class="sxs-lookup"><span data-stu-id="e1b23-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1b23-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e1b23-115">Return Value</span></span>  
 <span data-ttu-id="e1b23-116">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="e1b23-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b23-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1b23-117">Requirements</span></span>  
 <span data-ttu-id="e1b23-118">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="e1b23-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b23-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1b23-119">See Also</span></span>  
 [<span data-ttu-id="e1b23-120">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e1b23-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e1b23-121">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e1b23-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e1b23-122">API ALink</span><span class="sxs-lookup"><span data-stu-id="e1b23-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
