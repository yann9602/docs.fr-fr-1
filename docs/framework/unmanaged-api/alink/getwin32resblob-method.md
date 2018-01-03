---
title: "GetWin32ResBlob, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="7402f-102">GetWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="7402f-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="7402f-103">Récupère le blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="7402f-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="7402f-104">Appelez cette méthode après avoir défini les options d’assembly.</span><span class="sxs-lookup"><span data-stu-id="7402f-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7402f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7402f-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7402f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7402f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="7402f-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7402f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="7402f-108">Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de Version Win32</span><span class="sxs-lookup"><span data-stu-id="7402f-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="7402f-109">TRUE si le fichier est une DLL, false pour un EXE.</span><span class="sxs-lookup"><span data-stu-id="7402f-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="7402f-110">Icône facultative à insérer dans le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="7402f-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="7402f-111">Reçoit le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="7402f-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="7402f-112">Reçoit la taille de l’objet blob.</span><span class="sxs-lookup"><span data-stu-id="7402f-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7402f-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7402f-113">Return Value</span></span>  
 <span data-ttu-id="7402f-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="7402f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7402f-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7402f-115">Requirements</span></span>  
 <span data-ttu-id="7402f-116">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="7402f-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7402f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7402f-117">See Also</span></span>  
 [<span data-ttu-id="7402f-118">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="7402f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="7402f-119">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="7402f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="7402f-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="7402f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
