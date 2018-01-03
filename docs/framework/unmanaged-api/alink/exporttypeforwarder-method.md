---
title: "ExportTypeForwarder, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportTypeForwarder
helpviewer_keywords: ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="813b9-102">ExportTypeForwarder, méthode</span><span class="sxs-lookup"><span data-stu-id="813b9-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="813b9-103">Ajoute un redirecteur de type à la table de type de l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="813b9-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="813b9-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="813b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="813b9-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="813b9-106">Référence à l’assembly auquel le redirecteur de type fait référence.</span><span class="sxs-lookup"><span data-stu-id="813b9-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="813b9-107">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="813b9-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="813b9-108">`ComType`indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="813b9-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="813b9-109">Cette valeur peut être passée à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="813b9-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="813b9-110">Reçoit le jeton du type exporté.</span><span class="sxs-lookup"><span data-stu-id="813b9-110">Receives the token of the exported type.</span></span> <span data-ttu-id="813b9-111">Cela est nécessaire uniquement pour émettre des types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="813b9-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="813b9-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="813b9-112">Return Value</span></span>  
 <span data-ttu-id="813b9-113">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="813b9-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="813b9-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="813b9-114">Requirements</span></span>  
 <span data-ttu-id="813b9-115">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="813b9-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813b9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="813b9-116">See Also</span></span>  
 [<span data-ttu-id="813b9-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="813b9-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="813b9-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="813b9-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="813b9-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="813b9-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
