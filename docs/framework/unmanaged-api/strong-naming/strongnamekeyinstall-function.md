---
title: StrongNameKeyInstall, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyInstall
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyInstall
helpviewer_keywords: StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60044e12a884a28cb7485118a95d2bf7650723fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="c5988-102">StrongNameKeyInstall, fonction</span><span class="sxs-lookup"><span data-stu-id="c5988-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="c5988-103">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="c5988-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="c5988-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c5988-104">This function has been deprecated.</span></span> <span data-ttu-id="c5988-105">Utilisez le [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="c5988-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5988-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5988-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5988-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5988-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="c5988-108">[in] Le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="c5988-108">[in] The name of the key container.</span></span> <span data-ttu-id="c5988-109">`wszKeyContainer`doit être une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="c5988-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="c5988-110">[in] La paire de clés binaire.</span><span class="sxs-lookup"><span data-stu-id="c5988-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="c5988-111">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c5988-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5988-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5988-112">Return Value</span></span>  
 <span data-ttu-id="c5988-113">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="c5988-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5988-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5988-114">Remarks</span></span>  
 <span data-ttu-id="c5988-115">Utilisez le [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) afin de supprimer le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="c5988-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="c5988-116">Si le `StrongNameKeyInstall` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="c5988-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5988-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5988-117">Requirements</span></span>  
 <span data-ttu-id="c5988-118">**Plateformes :** WindSee [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5988-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5988-119">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c5988-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c5988-120">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5988-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5988-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5988-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5988-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5988-122">See Also</span></span>  
 [<span data-ttu-id="c5988-123">StrongNameKeyInstall (méthode)</span><span class="sxs-lookup"><span data-stu-id="c5988-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="c5988-124">StrongNameKeyDelete (méthode)</span><span class="sxs-lookup"><span data-stu-id="c5988-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="c5988-125">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="c5988-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
