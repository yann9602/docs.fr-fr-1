---
title: "FreeWin32ResBlob, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.FreeWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: FreeWin32ResBlob
helpviewer_keywords: FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdecedf319ad235bd635dd1d2edf600b0d00dbb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="b294d-102">FreeWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="b294d-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="b294d-103">Libère l’objet blob de ressources Win32 et les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="b294d-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b294d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b294d-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b294d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b294d-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="b294d-106">Objet blob de ressources à libérer.</span><span class="sxs-lookup"><span data-stu-id="b294d-106">The resource blob to be released.</span></span> <span data-ttu-id="b294d-107">Cette méthode assigne le pointeur d’objet blob avec la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="b294d-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b294d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b294d-108">Return Value</span></span>  
 <span data-ttu-id="b294d-109">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="b294d-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b294d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b294d-110">Requirements</span></span>  
 <span data-ttu-id="b294d-111">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="b294d-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b294d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b294d-112">See Also</span></span>  
 [<span data-ttu-id="b294d-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b294d-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="b294d-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b294d-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="b294d-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="b294d-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
