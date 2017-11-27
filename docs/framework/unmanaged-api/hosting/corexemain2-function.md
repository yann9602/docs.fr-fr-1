---
title: _CorExeMain2, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain2
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorExeMain2
helpviewer_keywords: _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c705627de8e8157212ae3e6a2ab4f2c12246653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corexemain2-function"></a><span data-ttu-id="439b8-102">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="439b8-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="439b8-103">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="439b8-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="439b8-104">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="439b8-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439b8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="439b8-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="439b8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="439b8-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="439b8-107">[in] Pointeur vers le code mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="439b8-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="439b8-108">[in] Le nombre d’éléments `pUnmappedPE` peut contenir.</span><span class="sxs-lookup"><span data-stu-id="439b8-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="439b8-109">[in] Pointeur vers le nom de l’image exécutable.</span><span class="sxs-lookup"><span data-stu-id="439b8-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="439b8-110">[in] Le nom du fichier de chargeur.</span><span class="sxs-lookup"><span data-stu-id="439b8-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="439b8-111">[in] Paramètres de ligne de commande, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="439b8-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="439b8-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="439b8-112">Requirements</span></span>  
 <span data-ttu-id="439b8-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="439b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439b8-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="439b8-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="439b8-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="439b8-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="439b8-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439b8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="439b8-117">See Also</span></span>  
 [<span data-ttu-id="439b8-118">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="439b8-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
