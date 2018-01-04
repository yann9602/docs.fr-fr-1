---
title: "ISymUnmanagedBinder2::GetReaderForFile2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2.GetReaderForFile2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 270a154c40b85ad4774bececf12685393f4d6c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="e1ce0-102">ISymUnmanagedBinder2::GetReaderForFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="e1ce0-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="e1ce0-103">Une interface de métadonnées et un nom de fichier, retourne le correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface qui lit les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="e1ce0-104">Cette méthode fournit une recherche plus étendue pour le fichier du programme (PDB) de la base de données à la [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e1ce0-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ce0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1ce0-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1ce0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1ce0-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e1ce0-107">[in] Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e1ce0-108">[in] Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e1ce0-109">[in] Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="e1ce0-110">[in] Une valeur de la [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) énumération qui spécifie la stratégie à utiliser lorsque vous effectuez une recherche pour un lecteur de symboles.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e1ce0-111">[out] Un pointeur qui est défini à le <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1ce0-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e1ce0-112">Return Value</span></span>  
 <span data-ttu-id="e1ce0-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1ce0-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1ce0-114">Requirements</span></span>  
 <span data-ttu-id="e1ce0-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e1ce0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1ce0-116">Notes</span><span class="sxs-lookup"><span data-stu-id="e1ce0-116">Remarks</span></span>  
 <span data-ttu-id="e1ce0-117">Cette version de la méthode peut rechercher le fichier PDB dans des domaines autres que juste à côté du module.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="e1ce0-118">La stratégie de recherche peut être contrôlée en combinant [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e1ce0-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="e1ce0-119">Par exemple, `AllowReferencePathAccess | AllowSymbolServerAccess` recherche le fichier PDB en regard du fichier exécutable et sur un serveur de symboles, mais ne pas interroger le Registre ou le chemin d’accès dans le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="e1ce0-120">Si le `searchPath` paramètre est fourni, ces répertoires seront toujours recherchés.</span><span class="sxs-lookup"><span data-stu-id="e1ce0-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ce0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1ce0-121">See Also</span></span>  
 [<span data-ttu-id="e1ce0-122">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="e1ce0-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="e1ce0-123">GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="e1ce0-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
