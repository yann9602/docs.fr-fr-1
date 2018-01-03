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
ms.workload: dotnet
ms.openlocfilehash: c0be76e93ab41860f7f3416d0baffe3e4daf84c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="f3121-102">SetAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="f3121-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="f3121-103">Attribue le nom de l’assembly doit être créé.</span><span class="sxs-lookup"><span data-stu-id="f3121-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="f3121-104">Pas à utiliser lors de la production de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="f3121-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3121-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3121-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3121-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f3121-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="f3121-107">Nom qualifié complet du fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="f3121-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="f3121-108">Pointeur vers [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f3121-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="f3121-109">Indicateurs tel que défini dans [énumération AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f3121-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="f3121-110">Pointeur vers l’ID de l’assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="f3121-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3121-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f3121-111">Return Value</span></span>  
 <span data-ttu-id="f3121-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f3121-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3121-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f3121-113">Requirements</span></span>  
 <span data-ttu-id="f3121-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="f3121-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3121-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3121-115">See Also</span></span>  
 [<span data-ttu-id="f3121-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="f3121-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f3121-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="f3121-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f3121-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="f3121-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
