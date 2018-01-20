---
title: Configuration client
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75b594d01c8a9297f3383c2648b3853c2c024b9b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="client-configuration"></a>Configuration client
Vous pouvez utiliser la configuration client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour spécifier l'adresse, la liaison, le comportement, le contrat et les propriétés « ABC » du point de terminaison de client, que les clients utilisent pour se connecter aux points de terminaison de service. Le [ \<client >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) élément a un [ \<point de terminaison >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément dont les attributs sont utilisés pour configurer le point de terminaison ABC. Ces attributs sont traités dans la section « Configuration des points de terminaison » de cette rubrique.  
  
 Le [ \<point de terminaison >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément contient également un [ \<métadonnées >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) élément qui est utilisé pour spécifier les paramètres pour l’importation et exportation de métadonnées, un [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) élément qui constituée une collection d’en-têtes d’adresse personnalisés, et un [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) élément qui permet l’authentification d’un point de terminaison par d’autres points de terminaison échanger des messages avec lui. Le [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) et [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) éléments font partie de la <xref:System.ServiceModel.EndpointAddress> et sont décrits dans le [adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) rubrique. Des liens vers les rubriques qui expliquent l’utilisation des extensions de métadonnées sont fournis dans la sous-section Configuration des métadonnées de cette rubrique.  
  
## <a name="configuring-endpoints"></a>Configuration des points de terminaison  
 La configuration du client est conçue pour permettre au client spécifier un ou plusieurs points de terminaison, chacun avec son propre nom, adresse et contrat, et référençant chacun les [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) et [ \< comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) éléments dans la configuration du client à utiliser pour configurer ce point de terminaison. Le fichier configuration client doit être nommé « App.config » parce que c'est le nom que l'exécution [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attend. L'exemple suivant illustre un fichier de configuration client.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 L'attribut `name` facultatif identifie de manière unique un point de terminaison pour un contrat donné. Il est utilisé par le <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou par le <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> pour spécifier quel point de terminaison est visé dans la configuration client et doit être chargé lorsqu'un canal est créé pour le desservir. Le nom générique de configuration du point de terminaison « * » est disponible et indique à la méthode <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> qu'elle doit charger toute configuration de point de terminaison dans le fichier, si tant est qu'une configuration est disponible, et lève une exception dans le cas contraire. Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié. La valeur par défaut pour l'attribut `name` est une chaîne vide qui est mise en correspondance comme tout autre nom.  
  
 Chaque point de terminaison doit avoir une adresse qui lui est associée pour pouvoir être localisé et identifié. L'attribut `address` peut être utilisé pour spécifier l'URL qui fournit l'emplacement du point de terminaison. Mais l'adresse d'un point de terminaison de service peut également être spécifiée dans du code en créant un URI et en l'ajoutant à <xref:System.ServiceModel.ServiceHost> qui utilise l'une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Comme indiqué dans l’introduction, le [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) et [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) éléments font partie de la <xref:System.ServiceModel.EndpointAddress> et sont également décrits dans le [ Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) rubrique.  
  
 L'attribut `binding` indique le type de liaison que le point de terminaison s'attend à utiliser lors de la connexion à un service. Ce type doit posséder une section de configuration inscrite s'il doit être référencé. Dans l’exemple précédent, il s’agit du [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, ce qui indique que le point de terminaison utilise une <xref:System.ServiceModel.WSHttpBinding>. Mais il peut y avoir plusieurs liaisons d’un type donné utilisables par le point de terminaison. Chacune de celles-ci a son propre [ \<liaison >](../../../../docs/framework/misc/binding.md) élément dans l’élément de type (binding). L'attribut `bindingconfiguration` est utilisé pour distinguer plusieurs liaisons du même type. Sa valeur est mise en correspondance avec la `name` attribut de la [ \<liaison >](../../../../docs/framework/misc/binding.md) élément. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment configurer un client de liaison à l’aide de la configuration, consultez [Comment : spécifier une liaison Client dans Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 Le `behaviorConfiguration` attribut est utilisé pour spécifier les [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) de la [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) le point de terminaison doit utiliser. Sa valeur est mise en correspondance avec la `name` attribut de la [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément. Pour obtenir un exemple de configuration pour spécifier les comportements du client, consultez [configuration des comportements clients](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 L'attribut `contract` spécifie quel contrat le point de terminaison expose. Cette valeur correspond au <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> de <xref:System.ServiceModel.ServiceContractAttribute>. La valeur par défaut est le nom de type complet de la classe qui implémente le service.  
  
### <a name="configuring-metadata"></a>Configuration des métadonnées  
 Le [ \<métadonnées >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) élément est utilisé pour spécifier les paramètres utilisés pour enregistrer les métadonnées des extensions d’importation. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]extension du système de métadonnées, consultez[extension du système de métadonnées](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Points de terminaison : adresses, liaisons et contrats](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Configuration des comportements clients](../../../../docs/framework/wcf/configuring-client-behaviors.md)
