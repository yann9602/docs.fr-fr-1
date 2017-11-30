---
title: "ForwardTranslateAccelerator (fonction) (référence des API non managées WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ForwardTranslateAccelerator
api_location: PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 663b28ed1a9430a6280ccd0ee9a44da2dea0c3cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="3a5b0-102">ForwardTranslateAccelerator (fonction) (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="3a5b0-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="3a5b0-103">Cette API prend en charge l’infrastructure de Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="3a5b0-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="3a5b0-104">Utilisée par l’infrastructure de Windows Presentation Foundation (WPF) pour la gestion de windows.</span><span class="sxs-lookup"><span data-stu-id="3a5b0-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a5b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a5b0-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a5b0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a5b0-106">Parameters</span></span>  
 <span data-ttu-id="3a5b0-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="3a5b0-107">pMsg</span></span>  
 <span data-ttu-id="3a5b0-108">Pointeur vers un message.</span><span class="sxs-lookup"><span data-stu-id="3a5b0-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="3a5b0-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="3a5b0-109">appUnhandled</span></span>  
 <span data-ttu-id="3a5b0-110">`true`Lorsque l’application a déjà reçue une chance de traiter le message d’entrée, mais elle n’a pas gérée dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="3a5b0-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a5b0-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3a5b0-111">Requirements</span></span>  
 <span data-ttu-id="3a5b0-112">**Plateformes :** consultez [configuration système requise du .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a5b0-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a5b0-113">**DLL :**</span><span class="sxs-lookup"><span data-stu-id="3a5b0-113">**DLL:**</span></span>  
  
 <span data-ttu-id="3a5b0-114">Dans le .NET Framework 3.0 et 3.5 : PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="3a5b0-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="3a5b0-115">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="3a5b0-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="3a5b0-116">**Version du .NET framework :**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a5b0-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5b0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a5b0-117">See Also</span></span>  
 [<span data-ttu-id="3a5b0-118">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="3a5b0-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
