---
title: "&lt;compositeDuplex&gt; | Microsoft Docs"
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
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;compositeDuplex&gt;
Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.  
  
## Syntaxe  
  
```  
  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|clientBaseAddress|URI qui définit l'adresse du canal arrière en mode duplex.  Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.<br /><br /> Si cet attribut n'est pas défini, une adresse par défaut "`full qualified name+default port\TemporaryIndigoAddress\guid`" est générée.  La valeur par défaut est `null`.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP.  En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.  
  
 Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion.  Cette adresse cliente est fournie par l'attribut `clientBaseAddress`.  Notez que Windows Communication Foundation \(WCF\) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.  
  
## Exemple  
  
```  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>   
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)