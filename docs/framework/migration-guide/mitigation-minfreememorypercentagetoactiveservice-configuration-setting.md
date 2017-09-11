---
title: "Atténuation : paramètre de configuration minFreeMemoryPercentageToActiveService"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f7f228890476d45517a21bc09806538139c5e389
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-minfreememorypercentagetoactiveservice-configuration-setting"></a><span data-ttu-id="038c9-102">Atténuation : paramètre de configuration minFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="038c9-102">Mitigation: minFreeMemoryPercentageToActiveService Configuration Setting</span></span>
<span data-ttu-id="038c9-103">Dans [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], une exception est levée si la mémoire disponible sur le serveur web est inférieure au pourcentage spécifié par le paramètre de configuration [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).</span><span class="sxs-lookup"><span data-stu-id="038c9-103">In the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], an exception is thrown if the available memory on the web server is less than the percentage specified by the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) configuration setting.</span></span> <span data-ttu-id="038c9-104">Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ce paramètre a été ignoré.</span><span class="sxs-lookup"><span data-stu-id="038c9-104">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], this setting was ignored.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="038c9-105">Impact</span><span class="sxs-lookup"><span data-stu-id="038c9-105">Impact</span></span>  
 <span data-ttu-id="038c9-106">Dans la plupart des cas, l’impact du réglage du paramètre [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) est souhaitable : il améliore la stabilité du système en prévenant les exceptions <xref:System.OutOfMemoryException> qui peuvent se produire quand un service Windows Communication Foundation (WCF) est démarré sur un système ayant une mémoire contrainte.</span><span class="sxs-lookup"><span data-stu-id="038c9-106">In most cases, the impact of observing the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting is desirable: It improves system stability by preventing the <xref:System.OutOfMemoryException> exceptions that can occur when a Windows Communication Foundation (WCF) service is started on a system that has constrained memory.</span></span>  
  
 <span data-ttu-id="038c9-107">Toutefois, dans certains cas, un service qui démarrait correctement peut ne plus démarrer.</span><span class="sxs-lookup"><span data-stu-id="038c9-107">However, in some cases, a service that previously started successfully may be unable to start.</span></span> <span data-ttu-id="038c9-108">Dans ce cas, un message d'erreur détaillé s'affiche :</span><span class="sxs-lookup"><span data-stu-id="038c9-108">In that case, a detailed error message appears:</span></span>  
  
```console
Memory gates checking failed because the free memory (nnnn bytes) is less than nn% of total memory. As a result, the service will not be available for incoming requests. To resolve this, either reduce the load on the machine or adjust the value of minFreeMemoryPercentageToActivateService on the serviceHostingEnvironment config element.
```
  
## <a name="mitigation"></a><span data-ttu-id="038c9-109">Atténuation</span><span class="sxs-lookup"><span data-stu-id="038c9-109">Mitigation</span></span>  
 <span data-ttu-id="038c9-110">Pour rétablir le comportement précédent où le paramètre [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) a été ignoré, modifiez le fichier Web.config comme suit :</span><span class="sxs-lookup"><span data-stu-id="038c9-110">To revert to the previous behavior where the [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) setting was ignored, modify the web.config file as follows:</span></span>  
  
```xml
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="see-also"></a><span data-ttu-id="038c9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="038c9-111">See Also</span></span>  
 [<span data-ttu-id="038c9-112">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="038c9-112">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

