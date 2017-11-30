---
title: StrongNameKeyDelete, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c7b3ccc9ec1b8cbc81de115f734e1d11e0e0ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="b79a6-102">StrongNameKeyDelete, fonction</span><span class="sxs-lookup"><span data-stu-id="b79a6-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="b79a6-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="b79a6-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="b79a6-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="b79a6-104">This function has been deprecated.</span></span> <span data-ttu-id="b79a6-105">Utilisez le [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="b79a6-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79a6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b79a6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b79a6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b79a6-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="b79a6-108">[in] Le nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b79a6-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b79a6-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b79a6-109">Return Value</span></span>  
 <span data-ttu-id="b79a6-110">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="b79a6-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b79a6-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="b79a6-111">Remarks</span></span>  
 <span data-ttu-id="b79a6-112">Utilisez le [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) de fonction pour importer une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="b79a6-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="b79a6-113">Si le `StrongNameKeyDelete` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="b79a6-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79a6-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b79a6-114">Requirements</span></span>  
 <span data-ttu-id="b79a6-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b79a6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b79a6-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b79a6-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b79a6-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b79a6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b79a6-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b79a6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79a6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b79a6-119">See Also</span></span>  
 [<span data-ttu-id="b79a6-120">StrongNameKeyDelete (méthode)</span><span class="sxs-lookup"><span data-stu-id="b79a6-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="b79a6-121">StrongNameKeyInstall (méthode)</span><span class="sxs-lookup"><span data-stu-id="b79a6-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="b79a6-122">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="b79a6-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
