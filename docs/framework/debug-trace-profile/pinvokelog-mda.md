---
title: "Assistant Débogage managé pInvokeLog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c4842d838fd5b4fee29187f118c784c55e0eb13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="249d5-102">Assistant Débogage managé pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="249d5-102">pInvokeLog MDA</span></span>
<span data-ttu-id="249d5-103">L’Assistant Débogage managé (MDA) `pInvokeLog` est activé pour chaque signature d’appel de code non managé unique utilisée pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="249d5-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="249d5-104">Effet sur le runtime</span><span class="sxs-lookup"><span data-stu-id="249d5-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="249d5-105">Cet Assistant Débogage managé n'a aucun effet sur le CLR.</span><span class="sxs-lookup"><span data-stu-id="249d5-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="249d5-106">Sortie</span><span class="sxs-lookup"><span data-stu-id="249d5-106">Output</span></span>  
 <span data-ttu-id="249d5-107">Message indiquant la signature d’appel de code non managé utilisée lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="249d5-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="249d5-108">Configuration</span><span class="sxs-lookup"><span data-stu-id="249d5-108">Configuration</span></span>  
 <span data-ttu-id="249d5-109">Chaque élément de correspondance filtre les fichiers .dll en fonction des appels de code non managé effectués.</span><span class="sxs-lookup"><span data-stu-id="249d5-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="249d5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="249d5-110">See Also</span></span>  
 [<span data-ttu-id="249d5-111">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="249d5-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="249d5-112">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="249d5-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
