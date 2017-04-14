---
title: "&lt;serviceActivations&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;serviceActivations&gt;
Élément de configuration qui vous permet d'ajouter des paramètres qui définissent des paramètres d'activation de services virtuels mappés aux types de service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Cela permet d'activer des services hébergés dans WAS\/IIS sans utiliser de fichier .svc.  
  
## Syntaxe  
  
```  
  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<ajouter\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|Ajoute un élément de configuration qui spécifie l'activation d'une application de service.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.|  
  
## Notes  
 L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.  
  
```  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.  
  
 Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.  Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.  De plus, `serviceHostingEnvironment` est une section machinetoApplication qui peut être héritée.  Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui\-ci.  
  
 L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non\-HTTP.  Elle requiert des extensions dans relativeAddress, par exemple  .svc, .xoml ou .xamlx.  Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d'activer le service sur n'importe quelle extension.  En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>