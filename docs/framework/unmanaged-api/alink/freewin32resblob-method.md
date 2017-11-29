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
ms.openlocfilehash: ae7b01fee1460abfae8fc2f8f6c12a5f19d83b6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="f19bb-102">FreeWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="f19bb-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="f19bb-103">Libère l’objet blob de ressources Win32 et les ressources associées.</span><span class="sxs-lookup"><span data-stu-id="f19bb-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f19bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f19bb-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f19bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f19bb-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="f19bb-106">Objet blob de ressources à libérer.</span><span class="sxs-lookup"><span data-stu-id="f19bb-106">The resource blob to be released.</span></span> <span data-ttu-id="f19bb-107">Cette méthode assigne le pointeur d’objet blob avec la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="f19bb-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f19bb-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f19bb-108">Return Value</span></span>  
 <span data-ttu-id="f19bb-109">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f19bb-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f19bb-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f19bb-110">Requirements</span></span>  
 <span data-ttu-id="f19bb-111">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="f19bb-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19bb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f19bb-112">See Also</span></span>  
 [<span data-ttu-id="f19bb-113">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f19bb-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f19bb-114">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="f19bb-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f19bb-115">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="f19bb-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
