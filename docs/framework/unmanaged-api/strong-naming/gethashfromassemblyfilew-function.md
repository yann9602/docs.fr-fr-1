---
title: GetHashFromAssemblyFileW, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFileW
helpviewer_keywords: GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa88de90f831e1faaca2624a77a556d6a2b566c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="d7312-102">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="d7312-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="d7312-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7312-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="d7312-104">Le chemin d’accès au fichier d’assembly doit être spécifié sous forme de chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="d7312-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="d7312-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="d7312-105">This function has been deprecated.</span></span> <span data-ttu-id="d7312-106">Utilisez le [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="d7312-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7312-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7312-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7312-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7312-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d7312-109">[in] Le chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="d7312-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="d7312-110">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="d7312-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d7312-111">[dans, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="d7312-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d7312-112">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="d7312-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d7312-113">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="d7312-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d7312-114">[in] La taille maximum demandée `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d7312-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d7312-115">[out] Le retournée, la taille, en octets, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d7312-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7312-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d7312-116">Requirements</span></span>  
 <span data-ttu-id="d7312-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7312-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7312-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d7312-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d7312-119">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7312-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7312-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7312-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7312-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7312-121">See Also</span></span>  
 [<span data-ttu-id="d7312-122">GetHashFromAssemblyFileW (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7312-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="d7312-123">GetHashFromAssemblyFile (méthode)</span><span class="sxs-lookup"><span data-stu-id="d7312-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="d7312-124">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="d7312-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
