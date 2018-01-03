---
title: "GetFileDef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 473cbaba8712ee247733ba3075c0163e259cf4dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="6e13b-102">GetFileDef, méthode</span><span class="sxs-lookup"><span data-stu-id="6e13b-102">GetFileDef Method</span></span>
<span data-ttu-id="6e13b-103">Récupère le jeton FileDef réel utilisé dans les métadonnées (par opposition au jeton assigné par ALink).</span><span class="sxs-lookup"><span data-stu-id="6e13b-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e13b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e13b-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e13b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e13b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6e13b-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6e13b-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="6e13b-107">Jeton du fichier ajouté récupéré à partir de la méthode AddFile ou AddImport (méthode).</span><span class="sxs-lookup"><span data-stu-id="6e13b-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="6e13b-108">Reçoit le jeton FileDef.</span><span class="sxs-lookup"><span data-stu-id="6e13b-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e13b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6e13b-109">Return Value</span></span>  
 <span data-ttu-id="6e13b-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="6e13b-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e13b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e13b-111">Requirements</span></span>  
 <span data-ttu-id="6e13b-112">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="6e13b-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e13b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e13b-113">See Also</span></span>  
 [<span data-ttu-id="6e13b-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="6e13b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6e13b-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="6e13b-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6e13b-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="6e13b-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
