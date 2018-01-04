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
ms.workload: dotnet
ms.openlocfilehash: 938d7b5633a73aafb81b16fd2fa207160cac4e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="ecf68-102">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="ecf68-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="ecf68-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="ecf68-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="ecf68-104">Le chemin d’accès au fichier d’assembly doit être spécifié sous forme de chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="ecf68-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="ecf68-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="ecf68-105">This function has been deprecated.</span></span> <span data-ttu-id="ecf68-106">Utilisez le [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="ecf68-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf68-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecf68-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecf68-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ecf68-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ecf68-109">[in] Le chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="ecf68-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="ecf68-110">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="ecf68-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ecf68-111">[dans, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="ecf68-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ecf68-112">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="ecf68-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ecf68-113">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="ecf68-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ecf68-114">[in] La taille maximum demandée `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ecf68-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ecf68-115">[out] Le retournée, la taille, en octets, `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ecf68-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf68-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ecf68-116">Requirements</span></span>  
 <span data-ttu-id="ecf68-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf68-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf68-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ecf68-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ecf68-119">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecf68-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecf68-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf68-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf68-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ecf68-121">See Also</span></span>  
 [<span data-ttu-id="ecf68-122">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="ecf68-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="ecf68-123">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="ecf68-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="ecf68-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ecf68-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
