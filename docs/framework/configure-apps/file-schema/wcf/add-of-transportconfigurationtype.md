---
title: "&lt;add&gt; de &lt;transportConfigurationType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# &lt;add&gt; de &lt;transportConfigurationType&gt;
Cet élément est une paire clé\/valeur, qui identifie le type d'un transport particulier.  
  
## Syntaxe  
  
```  
  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Attribut de chaîne requis.<br /><br /> Contient une clé définie par l'utilisateur qui identifie uniquement le type de transport.|  
|transportConfigurationType|Chaîne contenant le type qui implémente le transport spécifique.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transportConfigurationTypes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Collection de types implémentant le transport spécifique.|  
  
## Exemple  
  
```  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="net.udp"  
      transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>   
 [Hébergement](../../../../../docs/framework/wcf/feature-details/hosting.md)