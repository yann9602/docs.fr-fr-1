---
title: "SetAssemblyProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae13daab0352ad4367c7ad6e06d6c12af23c75bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="8e549-102">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8e549-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="8e549-103">Assigne des propriétés au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8e549-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e549-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8e549-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e549-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8e549-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8e549-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8e549-107">Fichier qui définit la propriété.</span><span class="sxs-lookup"><span data-stu-id="8e549-107">File that defines the property.</span></span> <span data-ttu-id="8e549-108">Peut être NULL si `AssemblyID` n’indique pas un netmodule indépendant.</span><span class="sxs-lookup"><span data-stu-id="8e549-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="8e549-109">Indique l’option de modification.</span><span class="sxs-lookup"><span data-stu-id="8e549-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="8e549-110">Nouvelle valeur de l’option.</span><span class="sxs-lookup"><span data-stu-id="8e549-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e549-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8e549-111">Return Value</span></span>  
 <span data-ttu-id="8e549-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="8e549-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e549-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8e549-113">Requirements</span></span>  
 <span data-ttu-id="8e549-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="8e549-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e549-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e549-115">See Also</span></span>  
 [<span data-ttu-id="8e549-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="8e549-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8e549-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="8e549-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8e549-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="8e549-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
