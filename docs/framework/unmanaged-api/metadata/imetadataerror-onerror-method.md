---
title: "IMetaDataError::OnError, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError.OnError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6e136f3fd76b9eb2be1e49a48316dc65c481fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="904a8-102">IMetaDataError::OnError, méthode</span><span class="sxs-lookup"><span data-stu-id="904a8-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="904a8-103">Fournit une notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="904a8-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="904a8-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="904a8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="904a8-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="904a8-106">[in] La valeur d’erreur HRESULT retourné à la méthode appelante.</span><span class="sxs-lookup"><span data-stu-id="904a8-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="904a8-107">[in] Le jeton de métadonnées de l’objet de code qui était en cours de fusion lorsque l’erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="904a8-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="904a8-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="904a8-108">Requirements</span></span>  
 <span data-ttu-id="904a8-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="904a8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="904a8-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="904a8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="904a8-111">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="904a8-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="904a8-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="904a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="904a8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="904a8-113">See Also</span></span>  
 [<span data-ttu-id="904a8-114">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="904a8-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)
