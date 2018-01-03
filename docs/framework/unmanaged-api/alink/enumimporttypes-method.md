---
title: "EnumImportTypes, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: EnumImportTypes
helpviewer_keywords: EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="62db4-102">EnumImportTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="62db4-102">EnumImportTypes Method</span></span>
<span data-ttu-id="62db4-103">Énumère chaque type dans chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="62db4-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62db4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62db4-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62db4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62db4-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="62db4-106">Handle pour l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="62db4-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="62db4-107">Nombre maximal de types à récupérer.</span><span class="sxs-lookup"><span data-stu-id="62db4-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="62db4-108">Reçoit des jetons, dans la limite de type `dwMax`.</span><span class="sxs-lookup"><span data-stu-id="62db4-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="62db4-109">Reçoit le nombre réel de type dans `aTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="62db4-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62db4-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="62db4-110">Return Value</span></span>  
 <span data-ttu-id="62db4-111">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="62db4-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62db4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="62db4-112">Requirements</span></span>  
 <span data-ttu-id="62db4-113">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="62db4-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62db4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62db4-114">See Also</span></span>  
 [<span data-ttu-id="62db4-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="62db4-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="62db4-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="62db4-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="62db4-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="62db4-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
