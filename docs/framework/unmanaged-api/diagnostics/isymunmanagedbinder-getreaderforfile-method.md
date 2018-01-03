---
title: "ISymUnmanagedBinder::GetReaderForFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderForFile
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="1bbdc-102">ISymUnmanagedBinder::GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="1bbdc-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="1bbdc-103">Une interface de métadonnées et un nom de fichier, retourne le correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure qui lit les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="1bbdc-104">Cette méthode s’ouvre le fichier du programme (PDB) de la base de données uniquement s’il est en regard du fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="1bbdc-105">Cette modification a été apportée pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-105">This change has been made for security purposes.</span></span> <span data-ttu-id="1bbdc-106">Si vous avez besoin d’une recherche plus étendue pour le fichier PDB, utilisez la [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1bbdc-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bbdc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bbdc-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1bbdc-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bbdc-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1bbdc-109">[in] Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1bbdc-110">[in] Pointeur vers le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1bbdc-111">[in] Pointeur vers le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1bbdc-112">[out] Un pointeur qui est défini à le <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bbdc-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1bbdc-113">Return Value</span></span>  
 <span data-ttu-id="1bbdc-114">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1bbdc-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bbdc-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bbdc-115">Requirements</span></span>  
 <span data-ttu-id="1bbdc-116">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1bbdc-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bbdc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1bbdc-117">See Also</span></span>  
 [<span data-ttu-id="1bbdc-118">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="1bbdc-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="1bbdc-119">GetReaderForFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="1bbdc-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
