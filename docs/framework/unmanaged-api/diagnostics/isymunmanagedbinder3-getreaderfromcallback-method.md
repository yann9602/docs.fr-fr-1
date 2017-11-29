---
title: "ISymUnmanagedBinder3::GetReaderFromCallback, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3.GetReaderFromCallback
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e748742c1c67df0b33818e3f6f3c5786e07c65f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="e09fe-102">ISymUnmanagedBinder3::GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="e09fe-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="e09fe-103">Permet à l’utilisateur d’implémenter ou de fournir via un rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations de répertoire de débogage à partir de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e09fe-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e09fe-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e09fe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e09fe-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e09fe-106">[in] Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e09fe-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e09fe-107">[in] Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e09fe-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e09fe-108">[in] Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="e09fe-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="e09fe-109">[in] Une valeur de la [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) énumération qui spécifie la stratégie à utiliser lorsque vous effectuez une recherche pour un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="e09fe-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="e09fe-110">[in] Pointeur vers la fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="e09fe-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e09fe-111">[out] Un pointeur qui est défini à le [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e09fe-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e09fe-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e09fe-112">Return Value</span></span>  
 <span data-ttu-id="e09fe-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e09fe-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09fe-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e09fe-114">Requirements</span></span>  
 <span data-ttu-id="e09fe-115">**En-tête :** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="e09fe-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09fe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e09fe-116">See Also</span></span>  
 [<span data-ttu-id="e09fe-117">ISymUnmanagedBinder3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="e09fe-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
