---
title: '&lt;factorySettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0df9a6bd4da9131961e0ca35ab75109053b97c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfactorysettingsgt"></a>&lt;factorySettings&gt;
Spécifie les paramètres du cache de la fabrique de canaux.  
  
\<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<sendMessageChannelCache >  
\<factorySettings >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|IdleTimeout|Valeur TimeSpan qui spécifie la durée maximale pendant laquelle l'objet peut rester inactif dans le cache avant d'être supprimé.|  
|leaseTimeout|Une valeur TimeSpan qui spécifie l’intervalle de temps après lequel un objet est supprimé du cache.|  
|maxItemsInCache|Entier qui spécifie le nombre maximal d'objets pouvant être placés dans le cache.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sendMessageChannelCache >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|Un comportement de service qui permet de personnaliser le partage du cache niveaux, les paramètres du cache de fabrique de canal et les paramètres du cache de canal pour le flux de travail qui envoient des messages aux points de terminaison de service à l’aide d’envoi d’activités de messagerie.|  
  
## <a name="remarks"></a>Remarques  
 Ce comportement de service est destiné aux flux de travail qui envoient des messages aux points de terminaison de service. Ces flux de travail sont généralement des flux de travail clients, mais peuvent également être des services de flux de travail hébergés dans un <xref:System.ServiceModel.WorkflowServiceHost>.  
  
 Par défaut, dans un flux de travail hébergé par un <xref:System.ServiceModel.WorkflowServiceHost>, le cache utilisé par les activités de messagerie <xref:System.ServiceModel.Activities.Send> est partagé entre toutes les instances de flux de travail dans <xref:System.ServiceModel.WorkflowServiceHost> (mise en cache au niveau de l'hôte). Pour un flux de travail client non hébergé par un objet  <xref:System.ServiceModel.WorkflowServiceHost>, le cache est uniquement disponible pour l'instance de flux de travail (mise en cache au niveau de l'instance). La mise en cache est désactivée par défaut pour toute activité d'envoi dans votre flux de travail qui a des points de terminaison définis dans la configuration.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]comment modifier le niveaux de partage de cache par défaut et les paramètres de cache pour la fabrication de canal et le cache de canaux, consultez [changement des niveaux de partage du Cache pour les activités d’envoi](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
## <a name="example"></a>Exemple  
 Dans un service de flux de travail hébergé, vous pouvez spécifier les paramètres du cache de la fabrique et du cache de canaux dans le fichier de configuration de l'application. Pour cela, ajoutez un comportement de service qui contient les paramètres des caches de la fabrique et de canaux et ajoutez-le à votre service. L’exemple suivant montre le contenu d’un fichier de configuration qui contient la **MyChannelCacheBehavior** comportement de service avec les paramètres du cache du cache et le canal de fabrique personnalisée. Ce comportement de service est ajouté au service via la **behaviorConfiguarion** attribut.  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [Niveaux de modification du partage du Cache pour les activités d’envoi](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
