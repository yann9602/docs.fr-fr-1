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
ms.openlocfilehash: 9c4456757c56440463010d4adc3d3eed90dbc07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="d0408-102">GetWin32ResBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="d0408-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="d0408-103">Récupère le blob de ressources Win32.</span><span class="sxs-lookup"><span data-stu-id="d0408-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="d0408-104">Appelez cette méthode après avoir défini les options d’assembly.</span><span class="sxs-lookup"><span data-stu-id="d0408-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0408-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0408-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d0408-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0408-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d0408-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d0408-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d0408-108">Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de Version Win32</span><span class="sxs-lookup"><span data-stu-id="d0408-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="d0408-109">TRUE si le fichier est une DLL, false pour un EXE.</span><span class="sxs-lookup"><span data-stu-id="d0408-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="d0408-110">Icône facultative à insérer dans le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="d0408-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="d0408-111">Reçoit le blob de ressources.</span><span class="sxs-lookup"><span data-stu-id="d0408-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="d0408-112">Reçoit la taille de l’objet blob.</span><span class="sxs-lookup"><span data-stu-id="d0408-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0408-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d0408-113">Return Value</span></span>  
 <span data-ttu-id="d0408-114">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="d0408-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0408-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d0408-115">Requirements</span></span>  
 <span data-ttu-id="d0408-116">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="d0408-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0408-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0408-117">See Also</span></span>  
 [<span data-ttu-id="d0408-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d0408-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d0408-119">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="d0408-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d0408-120">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="d0408-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
