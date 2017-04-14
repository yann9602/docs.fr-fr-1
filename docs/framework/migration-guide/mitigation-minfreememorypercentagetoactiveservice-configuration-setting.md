---
title: "Att&#233;nuation&#160;: param&#232;tre de configuration minFreeMemoryPercentageToActiveService | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a7875f26-0da8-4afe-9846-7a21778f757b
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Att&#233;nuation&#160;: param&#232;tre de configuration minFreeMemoryPercentageToActiveService
Dans [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], une exception est levée si la mémoire disponible sur le serveur web est inférieure au pourcentage spécifié par le paramètre de configuration [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ce paramètre a été ignoré.  
  
## Impact  
 Dans la plupart des cas, l'impact du réglage du paramètre [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) est souhaitable : il améliore la stabilité du système en prévenant les exceptions <xref:System.OutOfMemoryException> qui peuvent se produire lorsqu'un service Windows Communication Foundation \(WCF\) est démarré sur un système ayant une mémoire contrainte.  
  
 Toutefois, dans certains cas, un service qui démarrait correctement peut ne plus démarrer.  Dans ce cas, un message d'erreur détaillé s'affiche :  
  
```Output  
  
La vérification des portes mémoire a échoué, car la mémoire disponible (nnnn octets) est inférieure à nn % de la mémoire totale.  Par conséquent, le service n'est pas disponible pour les requêtes entrantes.  Pour résoudre ce problème, réduisez la charge sur l'ordinateur ou réglez la valeur de minFreeMemoryPercentageToActivateService sur l'élément de configuration de serviceHostingEnvironment.    
```  
  
## Atténuation  
 Pour rétablir le comportement précédent où le paramètre [minFreeMemoryPercentageToActivateService](../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) a été ignoré, modifiez le fichier Web.config comme suit :  
  
```  
  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"   
                           minFreeMemoryPercentageToActivateService="0">  
   <serviceActivations>  
   ...  
   </serviceActivations>  
</serviceHostingEnvironment>  
  
```  
  
## Voir aussi  
 [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)