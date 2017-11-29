---
title: "SetAssemblyFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyFile
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile
helpviewer_keywords: SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d83062db41b5fa1485555de40be0a39a65e0459a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="27d07-102">SetAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="27d07-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="27d07-103">Attribue le nom de l’assembly doit être créé.</span><span class="sxs-lookup"><span data-stu-id="27d07-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="27d07-104">Pas à utiliser lors de la production de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="27d07-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d07-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27d07-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27d07-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27d07-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="27d07-107">Nom qualifié complet du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="27d07-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="27d07-108">Pointeur vers [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="27d07-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="27d07-109">Indicateurs tel que défini dans [énumération AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="27d07-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="27d07-110">Pointeur vers l’ID de l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="27d07-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27d07-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="27d07-111">Return Value</span></span>  
 <span data-ttu-id="27d07-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="27d07-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d07-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="27d07-113">Requirements</span></span>  
 <span data-ttu-id="27d07-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="27d07-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d07-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27d07-115">See Also</span></span>  
 [<span data-ttu-id="27d07-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="27d07-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="27d07-117">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="27d07-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="27d07-118">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="27d07-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
