---
title: "ImportFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d4f93336fe19210086c39b8db6d167b3caa222
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="importfile-method"></a><span data-ttu-id="d8697-102">ImportFile, méthode</span><span class="sxs-lookup"><span data-stu-id="d8697-102">ImportFile Method</span></span>
<span data-ttu-id="d8697-103">Importe les assemblys et modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="d8697-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8697-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8697-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8697-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8697-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d8697-106">Nom qualifié complet du fichier à importer.</span><span class="sxs-lookup"><span data-stu-id="d8697-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="d8697-107">Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier lorsqu’il est lié dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d8697-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="d8697-108">Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.</span><span class="sxs-lookup"><span data-stu-id="d8697-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="d8697-109">Pointeur vers le jeton où un ID de fichier unique sera stocké.</span><span class="sxs-lookup"><span data-stu-id="d8697-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="d8697-110">Le fichier peut être un assembly ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="d8697-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="d8697-111">Reçoit le pointeur vers [IMetaDataAssemblyImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d8697-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="d8697-112">Peut d’être NULL si le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="d8697-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="d8697-113">Pointeur vers le nombre de fichiers et/ou de portées qui ont été importées.</span><span class="sxs-lookup"><span data-stu-id="d8697-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8697-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d8697-114">Return Value</span></span>  
 <span data-ttu-id="d8697-115">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="d8697-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8697-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d8697-116">Requirements</span></span>  
 <span data-ttu-id="d8697-117">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="d8697-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8697-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8697-118">See Also</span></span>  
 [<span data-ttu-id="d8697-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d8697-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d8697-120">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d8697-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d8697-121">API ALink</span><span class="sxs-lookup"><span data-stu-id="d8697-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
