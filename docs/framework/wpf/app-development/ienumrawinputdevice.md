---
title: IEnumRAWINPUTDEVICE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a93458e97ef317c425f3b51b1e3abc20ade2931b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="9b7a0-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="9b7a0-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="9b7a0-103">Cette interface énumère les périphériques d'entrée brute ; elle est uniquement utilisée par PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="9b7a0-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b7a0-104">Cette API est conçue et pris en charge uniquement sur l'ordinateur client local</span><span class="sxs-lookup"><span data-stu-id="9b7a0-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="9b7a0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b7a0-105">Members</span></span>  
  
|<span data-ttu-id="9b7a0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b7a0-106">Member</span></span>|<span data-ttu-id="9b7a0-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b7a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b7a0-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="9b7a0-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="9b7a0-109">Énumère les éléments `celt` suivants (c'est-à-dire les structures RAWINPUTDEVICE) dans la liste de l'énumérateur, en les retournant dans `rgelt` avec le nombre réel d'éléments énumérés dans `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="9b7a0-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="9b7a0-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="9b7a0-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="9b7a0-111">Fait en sorte que l’énumérateur d’ignorer la prochaine `celt` éléments dans l’énumération afin que le prochain appel à [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) ne retourne pas ces éléments.</span><span class="sxs-lookup"><span data-stu-id="9b7a0-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="9b7a0-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="9b7a0-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="9b7a0-113">Réinitialise la séquence d'énumération au début.</span><span class="sxs-lookup"><span data-stu-id="9b7a0-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="9b7a0-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="9b7a0-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="9b7a0-115">Crée un autre énumérateur de périphériques d'entrée brute avec le même état que l'énumérateur actif pour itérer au sein de la même liste.</span><span class="sxs-lookup"><span data-stu-id="9b7a0-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b7a0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b7a0-116">See Also</span></span>  
 [<span data-ttu-id="9b7a0-117">À propos des entrées brutes</span><span class="sxs-lookup"><span data-stu-id="9b7a0-117">About Raw Input</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
