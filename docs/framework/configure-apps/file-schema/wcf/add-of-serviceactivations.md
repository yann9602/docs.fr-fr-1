---
title: "&lt;add&gt; de &lt;serviceActivations&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;add&gt; de &lt;serviceActivations&gt;
Élément de configuration qui vous permet de définir des paramètres d'activation de services virtuels mappés aux types de service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  Cela permet d'activer des services hébergés dans WAS\/IIS sans utiliser de fichier .svc.  
  
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
  
|Attribut|Description|  
|--------------|-----------------|  
|factory|Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.|  
|service|Le ServiceType qui implémente le service \(Typename qualifié complet ou Typename court \(s'il est placé dans le dossier App\_Code\).|  
|relativeAddress|L'adresse relative dans l'application IIS active \(par exemple « Service.svc ».  Dans WCF 4.0 cette adresse relative doit contenir une des extensions de fichiers connues \(.svc, .xamlx,…\).  Aucun fichier physique ne doit exister pour relativeUrl.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Section de configuration qui décrit les paramètres d'activation.|  
  
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
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>