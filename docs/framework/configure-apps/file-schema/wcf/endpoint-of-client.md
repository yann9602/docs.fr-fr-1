---
title: "&lt;endpoint&gt; de &lt;client&gt; | Microsoft Docs"
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
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# &lt;endpoint&gt; de &lt;client&gt;
Spécifie les propriétés du contrat, de la liaison et de l'adresse du point de terminaison du canal employées par les clients pour se connecter aux points de terminaison de service sur le serveur.  
  
## Syntaxe  
  
```  
  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"  
   endpointConfiguration=”String”  
   kind=”String”  
   name="String"  
</endpoint>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|address|Attribut de chaîne requis.<br /><br /> Spécifie l'adresse du point de terminaison.  La valeur par défaut est une chaîne vide.  L'adresse doit être un URI absolu.|  
|behaviorConfiguration|Chaîne qui contient le nom de comportement du comportement à utiliser pour instancier le point de terminaison.  Le nom du comportement doit être dans la portée, au niveau où le service est défini.  La valeur par défaut est une chaîne vide.|  
|liaison|Attribut de chaîne requis.<br /><br /> Chaîne qui indique le type de liaison à utiliser.  Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé.  Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.|  
|bindingConfiguration|Facultatif.  Chaîne qui contient le nom de la configuration de liaison à utiliser lorsque le point de terminaison est instancié.  La configuration de la liaison doit être dans la portée, au niveau où le point de terminaison est défini.  La valeur par défaut est une chaîne vide.<br /><br /> Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration.  Définissez cet attribut si vous essayez d'utiliser une liaison personnalisée.  Sinon, une exception peut être levée.|  
|contrat|Attribut de chaîne requis.<br /><br /> Chaîne qui indique le contrat exposé par ce point de terminaison.  L'assembly doit implémenter le type de contrat.|  
|endpointConfiguration|Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard.  Le même nom doit être défini dans la section `<standardEndpoints>`.|  
|kind|Chaîne qui spécifie le type de point de terminaison standard appliqué.  Le type doit être inscrit dans la section `<extensions>` ou dans machine.config.  Si rien n'est spécifié, un point de terminaison de canal commun est créé.|  
|name|Attribut de chaîne facultatif.  Cet attribut identifie uniquement un point de terminaison pour un contrat donné.  Vous pouvez définir plusieurs clients pour un type de contrat donné.  Chaque définition doit être différenciée par un nom de configuration unique.  Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié.  La valeur par défaut est une chaîne vide.<br /><br /> L'attribut `name` d'une liaison est utilisé pour l'exportation de définition à travers WSDL.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<en\-têtes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|Collection d'en\-têtes d'adresses.|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<client\>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.|  
  
## Exemple  
 Il s'agit d'un exemple de configuration de point de terminaison de canal.  
  
```  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>   
 <xref:System.ServiceModel.Configuration.ClientSection>   
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>   
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>   
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>   
 [Configuration client WCF](../../../../../docs/framework/wcf/feature-details/client-configuration.md)   
 [Clients](../../../../../docs/framework/wcf/feature-details/clients.md)