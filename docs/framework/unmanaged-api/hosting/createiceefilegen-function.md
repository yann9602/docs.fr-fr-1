---
title: CreateICeeFileGen, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="5c9a5-102">CreateICeeFileGen, fonction</span><span class="sxs-lookup"><span data-stu-id="5c9a5-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="5c9a5-103">Crée un [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objet.</span><span class="sxs-lookup"><span data-stu-id="5c9a5-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="5c9a5-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c9a5-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c9a5-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c9a5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5c9a5-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="5c9a5-107">[out] Un pointeur vers l’adresse d’un nouveau `ICeeFileGen` objet.</span><span class="sxs-lookup"><span data-stu-id="5c9a5-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c9a5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5c9a5-108">Return Value</span></span>  
 <span data-ttu-id="5c9a5-109">Cette méthode retourne des codes d’erreur COM standard.</span><span class="sxs-lookup"><span data-stu-id="5c9a5-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c9a5-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="5c9a5-110">Remarks</span></span>  
 <span data-ttu-id="5c9a5-111">Le `ICeeFileGen` objet est utilisé pour créer de common language runtime (CLR) les fichiers exécutables portables (PE).</span><span class="sxs-lookup"><span data-stu-id="5c9a5-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="5c9a5-112">Appelez le [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) afin de détruire le `ICeeFileGen` une fois que l’objet.</span><span class="sxs-lookup"><span data-stu-id="5c9a5-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9a5-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5c9a5-113">Requirements</span></span>  
 <span data-ttu-id="5c9a5-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9a5-115">**En-tête :** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="5c9a5-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="5c9a5-116">**Bibliothèque :** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="5c9a5-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="5c9a5-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9a5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c9a5-118">See Also</span></span>  
 [<span data-ttu-id="5c9a5-119">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="5c9a5-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
