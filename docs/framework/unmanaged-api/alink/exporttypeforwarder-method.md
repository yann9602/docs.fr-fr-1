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
ms.openlocfilehash: 0f117d64673729113d917d700e3a26f9723b5a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="74db4-102">ExportTypeForwarder, méthode</span><span class="sxs-lookup"><span data-stu-id="74db4-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="74db4-103">Ajoute un redirecteur de type à la table de type de l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="74db4-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74db4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74db4-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74db4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74db4-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="74db4-106">Référence à l’assembly auquel le redirecteur de type fait référence.</span><span class="sxs-lookup"><span data-stu-id="74db4-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="74db4-107">Nom de type qualifié complet à exporter.</span><span class="sxs-lookup"><span data-stu-id="74db4-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="74db4-108">`ComType`indicateurs tels que `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="74db4-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="74db4-109">Cette valeur peut être passée à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="74db4-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="74db4-110">Reçoit le jeton du type exporté.</span><span class="sxs-lookup"><span data-stu-id="74db4-110">Receives the token of the exported type.</span></span> <span data-ttu-id="74db4-111">Cela est nécessaire uniquement pour émettre des types imbriqués.</span><span class="sxs-lookup"><span data-stu-id="74db4-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74db4-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="74db4-112">Return Value</span></span>  
 <span data-ttu-id="74db4-113">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="74db4-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74db4-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="74db4-114">Requirements</span></span>  
 <span data-ttu-id="74db4-115">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="74db4-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74db4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74db4-116">See Also</span></span>  
 [<span data-ttu-id="74db4-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="74db4-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="74db4-118">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="74db4-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="74db4-119">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="74db4-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
