---
title: CreateALink, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a><span data-ttu-id="6b83b-102">CreateALink, fonction</span><span class="sxs-lookup"><span data-stu-id="6b83b-102">CreateALink Function</span></span>
<span data-ttu-id="6b83b-103">Crée une instance de l’utilitaire Assembly Linker et définit un pointeur vers l’interface spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b83b-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b83b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b83b-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b83b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b83b-105">Parameters</span></span>  
  
|<span data-ttu-id="6b83b-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6b83b-106">Parameter</span></span>|<span data-ttu-id="6b83b-107">Description</span><span class="sxs-lookup"><span data-stu-id="6b83b-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="6b83b-108">Le nom physique d’une des interfaces Assembly Linker.</span><span class="sxs-lookup"><span data-stu-id="6b83b-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="6b83b-109">L’emplacement de réussite contient un pointeur vers le `riid` interface.</span><span class="sxs-lookup"><span data-stu-id="6b83b-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b83b-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b83b-110">Requirements</span></span>  
 <span data-ttu-id="6b83b-111">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="6b83b-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b83b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b83b-112">See Also</span></span>  
 [<span data-ttu-id="6b83b-113">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="6b83b-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
