---
title: "ProcessUnhandledException (fonction) (référence des API non managées WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ProcessUnhandledException
api_location: PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8328ae4bcbff54743e8df0a4b6ff6da3065ea470
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="d4448-102">ProcessUnhandledException (fonction) (référence des API non managées WPF)</span><span class="sxs-lookup"><span data-stu-id="d4448-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="d4448-103">Cette API prend en charge l’infrastructure de Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="d4448-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="d4448-104">Utilisé par l’infrastructure de Windows Presentation Foundation (WPF) pour la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="d4448-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4448-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4448-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4448-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4448-106">Parameters</span></span>  
 <span data-ttu-id="d4448-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="d4448-107">errorMsg</span></span>  
 <span data-ttu-id="d4448-108">Message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="d4448-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4448-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4448-109">Requirements</span></span>  
 <span data-ttu-id="d4448-110">**Plateformes :** consultez [configuration système requise du .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4448-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4448-111">**DLL :**</span><span class="sxs-lookup"><span data-stu-id="d4448-111">**DLL:**</span></span>  
  
 <span data-ttu-id="d4448-112">Dans le .NET Framework 3.0 et 3.5 : PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="d4448-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="d4448-113">Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="d4448-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="d4448-114">**Version du .NET framework :**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4448-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4448-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4448-115">See Also</span></span>  
 [<span data-ttu-id="d4448-116">Référence des API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="d4448-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
