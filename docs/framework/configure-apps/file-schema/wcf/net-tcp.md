---
title: '&lt;NET.TCP&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a63d32cc4c0e48b8d3fb40526d810e2f66089d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltnettcpgt"></a>&lt;NET.TCP&gt;
Spécifie les paramètres de configuration du service de partage de port NET.TCP, qui permet à plusieurs processus de partager le même port TCP.  
  
 \<system.serviceModel.activation >  
\<NET.TCP >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="Integer"  
          maxPendingAccepts="Integer"  
          maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan"  
          teredoEnabled="Boolean">  
          <allowAccounts>  
             <!-- LocalSystem account -->   
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->   
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->   
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->   
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only)-->   
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`listenBacklog`|Entier qui spécifie le nombre maximal de connexions en attente qui sont acceptées à partir de la connexion partagée, mais qui ne sont pas encore distribuées aux services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. La valeur par défaut est 10.|  
|`maxPendingAccepts`|Entier qui spécifie le nombre maximal de threads d'acceptation simultanés en attente sur le point de terminaison d'écoute du service de partage. La valeur par défaut est 2.|  
|`MaxPendingConnections`|Nombre maximal de connexions que l'écouteur peut mettre en attente d'acceptation par l'application. Lorsque cette valeur de quota est dépassée, les nouvelles connexions entrantes sont supprimées plutôt que mises en attente d'acceptation. Les fonctionnalités de connexion telles que la sécurité des messages peuvent entraîner qu'un client ouvre plusieurs connexions. Les administrateurs de service doivent prendre en compte ces connexions supplémentaires lors de la définition de cette valeur de quota. La valeur par défaut est 10.|  
|`receiveTimeout`|`TimeSpan` qui spécifie le délai d'attente pour lire les données d'encadrement et effectuer la distribution de la connexion à partir des connexions sous-jacentes. La valeur par défaut est « 00:00:10 ».|  
|`teredoEnabled`|Valeur booléenne qui indique si le service de partage de port utilise le service Microsoft Teredo pour écouter les ports TCP pour le compte des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. La valeur par défaut est `false`.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Collection d'éléments de configuration qui contiennent un attribut `securityIdentifier` permettant de spécifier les comptes d'utilisateurs correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.|  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur le partage de ports, consultez [le partage de ports Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded). Pour comprendre comment configurer le service de partage de ports, consultez [configurer le Service de partage de ports Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>  
 [Partage de ports Net.TCP](http://msdn.microsoft.com/en-us/f13692ee-a179-4439-ae72-50db9534eded)  
 [Configuration du Service de partage de ports Net.TCP](http://msdn.microsoft.com/en-us/b6dd81fa-68b7-4e1b-868e-88e5901b7ea0)
