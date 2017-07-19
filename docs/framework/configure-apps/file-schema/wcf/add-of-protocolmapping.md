---
title: "&lt;add&gt; de &lt;protocolMapping&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;add&gt; de &lt;protocolMapping&gt;
Représente un mappage de protocole par défaut entre un schéma de protocole de transport \(par exemple, http, net.tcp, net.pipe, etc.\) et une liaison [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Lors de la création de points de terminaison par défaut au moment de l'exécution, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] examine les mappages configurés et sélectionne une liaison à utiliser en tant qu'adresse de base.  
  
## Syntaxe  
  
```vb  
  
<protocolMapping>  
    <add binding="String”  
         bindingConfiguration="String”  
         scheme="http/net.msmq/net.pipe/net.tcp"/>  
</protocolMapping>  
  
```  
  
```csharp  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Chaîne qui spécifie le type de liaison à utiliser pour un point de terminaison pendant la création de points de terminaison par défaut.|  
|bindingConfiguration|Chaîne qui spécifie le nom de la section de configuration de liaison à référencer.|  
|scheme|Schéma de protocole de transport à utiliser pour le point de terminaison par défaut.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<protocolMapping\>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Représente une section de configuration pour la définition de mappages de protocole par défaut entre des schémas de protocole de transport \(par exemple, http, net.tcp, net.pipe, etc.\) et des liaisons [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].|  
  
## Exemple  
 L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.  Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.  Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.  
  
```  
  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
  
```  
  
## Voir aussi  
 [System.ServiceModel.Configuration.ProtocolMappingSection](assetId:///System.ServiceModel.Configuration.ProtocolMappingSection?qualifyHint=False&amp;autoUpgrade=True)   
 [System.ServiceModel.Configuration.ProtocolMappingElement](assetId:///System.ServiceModel.Configuration.ProtocolMappingElement?qualifyHint=False&amp;autoUpgrade=True)