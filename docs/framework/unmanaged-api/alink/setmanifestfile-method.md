---
title: "SetManifestFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="f63c7-102">SetManifestFile, méthode</span><span class="sxs-lookup"><span data-stu-id="f63c7-102">SetManifestFile Method</span></span>
<span data-ttu-id="f63c7-103">Vous permet de spécifier ou de réinitialiser le fichier manifeste par l’éditeur de liens lorsqu’il crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f63c7-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63c7-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f63c7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f63c7-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="f63c7-106">Le nom du fichier manifeste dont le contenu est placé dans le blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="f63c7-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f63c7-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f63c7-107">Return Value</span></span>  
 <span data-ttu-id="f63c7-108">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="f63c7-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63c7-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f63c7-109">Remarks</span></span>  
 <span data-ttu-id="f63c7-110">Appelez cela avant de demander le Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="f63c7-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="f63c7-111">La valeur de le `pszFile` paramètre est le nom du fichier manifeste dont le contenu est lu et mis dans les ressources Win32 avec l’ID de RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="f63c7-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="f63c7-112">Lorsqu’elle est appelée à l’aide d’un paramètre de valeur NULL, tout manifeste lu précédemment est désactivée.</span><span class="sxs-lookup"><span data-stu-id="f63c7-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="f63c7-113">Cela permet de réinitialiser l’état de l’éditeur de liens à celui de la durée d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="f63c7-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63c7-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f63c7-114">Requirements</span></span>  
 <span data-ttu-id="f63c7-115">Requiert aLink.h</span><span class="sxs-lookup"><span data-stu-id="f63c7-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63c7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f63c7-116">See Also</span></span>  
 [<span data-ttu-id="f63c7-117">IALink3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="f63c7-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="f63c7-118">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="f63c7-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="f63c7-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f63c7-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f63c7-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="f63c7-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
