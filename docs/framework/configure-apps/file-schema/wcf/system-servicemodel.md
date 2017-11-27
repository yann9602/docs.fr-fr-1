---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 563825a92dbdeb90cd17d107795525686b7b4080
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemservicemodelgt"></a>&lt;system.serviceModel&gt;
Cette section de configuration contient tous les éléments de configuration ServiceModel de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportements >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|Cette section définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services. Chaque élément de comportement est identifié par son attribut `name` unique.|  
|[\<liaisons >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Cette section contient une collection de liaisons standard et personnalisées. Chaque entrée est identifiée par son `name` unique. Les services utilisent les liaisons en les liant à l'aide de `name`.|  
|[\<client >](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|Cette section contient la liste des points de terminaison utilisés par un client pour se connecter à un service.|  
|[\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|Cette section définit des contrats COM activés pour interagir avec WCF et COM.|  
|[\<commonBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|Cette section peut uniquement être définie dans le fichier machine.config. Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.  Chaque collection définit des éléments de comportement consommés respectivement par tous les points de terminaison et services de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sur l'ordinateur.  Si un comportement est défini dans les `<commonBehaviors>` et `<behaviors>` sections, le comportement dans le \<comportements > section est prioritaire.|  
|[\<extensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|Cette section contient une collection d'extensions qui permettent à l'utilisateur de créer des liaisons, des comportements et d'autres aspects d'extensions définis par l'utilisateur.|  
|[\<Diagnostics >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|Cette section contient les paramètres des fonctionnalités de diagnostic de WCF. L'utilisateur peut activer/désactiver le suivi, les compteurs de performance et le fournisseur WMI et ajouter des filtres de messages personnalisés.|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Cette section définit un ensemble de mappage de protocole par défaut entre les schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.|  
|[\<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Cette section définit un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Cette section définit le type instancié par l'environnement d'hébergement de service pour un transport particulier. Si cette section est vide, le type par défaut est utilisé.|  
|[\<Services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|Cette section contient une collection de services. Pour chaque service défini dans l'assembly, cet élément contient un élément `service` indiquant les paramètres du service.|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Cette section définit une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés réutilisables. Un point de terminaison standard possède un ou plusieurs attributs d'adresse, de liaison et de contrat ayant une valeur fixe. Par exemple, dans le point de terminaison de découverte, le contrat est fixe. Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<configuration>|Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.|  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] n'ajoute pas d'éléments aux sections de configuration d'autres produits.  
  
 Les services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont définis dans la section `services` du fichier de configuration. Un assembly peut contenir n'importe quel nombre de services. Chacun dispose de sa propre section de configuration de `service`. Cette section et son contenu définissent le contrat, le comportement et les points de terminaison du service en question.  
  
 Seul l'attribut `name` d'un service est requis.  Par défaut, le nom d'un service décrit le type CLR sous-jacent utilisé pour implémenter un service ; toutefois, vous pouvez modifier la propriété ConfigurationName d'un <xref:System.ServiceModel.ServiceContractAttribute> pour remplacer la spécification de type CLR.  
  
 L'attribut `behaviorConfiguration` est facultatif. Il identifie le comportement utilisé par un service. Le comportement spécifié par cet attribut doit être lié à un comportement de service défini dans l'étendue du même fichier de configuration (c'est-à-dire le même fichier ou un fichier parent).  
  
 Chaque service expose un ou plusieurs points de terminaison définis dans un élément `endpoint`. Chaque point de terminaison possède sa propre adresse et sa propre liaison. Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.  
  
 Les liaisons sont liées aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`. L'attribut `binding` définit la section dans laquelle la liaison est définie. L'attribut `bindingConfiguration` définit parmi les liaisons configurées figurant dans la section de liaison celle qui est utilisée. Une section de liaison peut définir plusieurs liaisons configurées.  
  
## <a name="example"></a>Exemple  
 Voici un exemple de fichier de configuration WCF.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
