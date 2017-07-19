---
title: "&lt;personnalis&#233;&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;personnalis&#233;&gt;
Spécifie les paramètres pour un service de programme de résolution d'homologue personnalisé.  
  
## Syntaxe  
  
```  
  
<custom address="Uri"  
   resolverType="String">  
      <headers/>  
   <identity/>  
</peerResolver>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`address`|URI indiquant l'adresse de point de terminaison du nœud homologue qui héberge le service de programme de résolution d'homologue personnalisé.|  
|`resolverType`|Chaîne contenant le type du service de programme de résolution d'homologue personnalisé.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Indique l'identité des programmes de résolution d'homologue personnalisés configurés avec cet élément.  Cet élément est de type <xref:System.ServiceModel.Configuration.IdentityElement>.|  
|[\<en\-têtes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|Collection d'en\-têtes d'adresse utilisée pour les messages SOAP gérés par le programme de résolution d'homologue personnalisé.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<resolver\>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|Un programme de résolution d'homologue est utilisé pour résoudre un ID de maille d'homologues en un jeu d'adresses de nœuds homologues représentant plusieurs nœuds faisant partie de la maille.|  
  
## Notes  
 Cet élément définit les paramètres de base pour un service de programme de résolution d'homologue personnalisé, y compris l'adresse de point de terminaison de l'homologue qui héberge le service et tous les paramètres de liaison spécifiques.  Pour plus d'informations sur la création d'un programme de résolution personnalisé, consultez [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/fr-fr/12aa3787-2962-439c-ad27-46523c8b0419).  
  
## Voir aussi  
 <xref:System.Servicemodel.PeerResolvers.CustomPeerResolverService>   
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>   
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>   
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>   
 [Programmes de résolution d'homologue](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)   
 [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/fr-fr/12aa3787-2962-439c-ad27-46523c8b0419)