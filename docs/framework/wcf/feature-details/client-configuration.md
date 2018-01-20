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
# <a name="client-configuration"></a><span data-ttu-id="27c42-102">Configuration client</span><span class="sxs-lookup"><span data-stu-id="27c42-102">Client Configuration</span></span>
<span data-ttu-id="27c42-103">Vous pouvez utiliser la configuration client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour spécifier l'adresse, la liaison, le comportement, le contrat et les propriétés « ABC » du point de terminaison de client, que les clients utilisent pour se connecter aux points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="27c42-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="27c42-104">Le [ \<client >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) élément a un [ \<point de terminaison >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément dont les attributs sont utilisés pour configurer le point de terminaison ABC.</span><span class="sxs-lookup"><span data-stu-id="27c42-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="27c42-105">Ces attributs sont traités dans la section « Configuration des points de terminaison » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="27c42-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="27c42-106">Le [ \<point de terminaison >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément contient également un [ \<métadonnées >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) élément qui est utilisé pour spécifier les paramètres pour l’importation et exportation de métadonnées, un [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) élément qui constituée une collection d’en-têtes d’adresse personnalisés, et un [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) élément qui permet l’authentification d’un point de terminaison par d’autres points de terminaison échanger des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="27c42-106">The [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="27c42-107">Le [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) et [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) éléments font partie de la <xref:System.ServiceModel.EndpointAddress> et sont décrits dans le [adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="27c42-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="27c42-108">Des liens vers les rubriques qui expliquent l’utilisation des extensions de métadonnées sont fournis dans la sous-section Configuration des métadonnées de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="27c42-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="27c42-109">Configuration des points de terminaison</span><span class="sxs-lookup"><span data-stu-id="27c42-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="27c42-110">La configuration du client est conçue pour permettre au client spécifier un ou plusieurs points de terminaison, chacun avec son propre nom, adresse et contrat, et référençant chacun les [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) et [ \< comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) éléments dans la configuration du client à utiliser pour configurer ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="27c42-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="27c42-111">Le fichier configuration client doit être nommé « App.config » parce que c'est le nom que l'exécution [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attend.</span><span class="sxs-lookup"><span data-stu-id="27c42-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="27c42-112">L'exemple suivant illustre un fichier de configuration client.</span><span class="sxs-lookup"><span data-stu-id="27c42-112">The following example shows a client configuration file.</span></span>  
  
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
  
 <span data-ttu-id="27c42-113">L'attribut `name` facultatif identifie de manière unique un point de terminaison pour un contrat donné.</span><span class="sxs-lookup"><span data-stu-id="27c42-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="27c42-114">Il est utilisé par le <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> ou par le <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> pour spécifier quel point de terminaison est visé dans la configuration client et doit être chargé lorsqu'un canal est créé pour le desservir.</span><span class="sxs-lookup"><span data-stu-id="27c42-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="27c42-115">Le nom générique de configuration du point de terminaison « \* » est disponible et indique à la méthode <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> qu'elle doit charger toute configuration de point de terminaison dans le fichier, si tant est qu'une configuration est disponible, et lève une exception dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="27c42-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="27c42-116">Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié.</span><span class="sxs-lookup"><span data-stu-id="27c42-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="27c42-117">La valeur par défaut pour l'attribut `name` est une chaîne vide qui est mise en correspondance comme tout autre nom.</span><span class="sxs-lookup"><span data-stu-id="27c42-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="27c42-118">Chaque point de terminaison doit avoir une adresse qui lui est associée pour pouvoir être localisé et identifié.</span><span class="sxs-lookup"><span data-stu-id="27c42-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="27c42-119">L'attribut `address` peut être utilisé pour spécifier l'URL qui fournit l'emplacement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="27c42-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="27c42-120">Mais l'adresse d'un point de terminaison de service peut également être spécifiée dans du code en créant un URI et en l'ajoutant à <xref:System.ServiceModel.ServiceHost> qui utilise l'une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="27c42-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="27c42-121">[Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="27c42-121"> [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="27c42-122">Comme indiqué dans l’introduction, le [ \<en-têtes >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) et [ \<identité >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) éléments font partie de la <xref:System.ServiceModel.EndpointAddress> et sont également décrits dans le [ Adresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="27c42-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="27c42-123">L'attribut `binding` indique le type de liaison que le point de terminaison s'attend à utiliser lors de la connexion à un service.</span><span class="sxs-lookup"><span data-stu-id="27c42-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="27c42-124">Ce type doit posséder une section de configuration inscrite s'il doit être référencé.</span><span class="sxs-lookup"><span data-stu-id="27c42-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="27c42-125">Dans l’exemple précédent, il s’agit du [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, ce qui indique que le point de terminaison utilise une <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="27c42-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="27c42-126">Mais il peut y avoir plusieurs liaisons d’un type donné utilisables par le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="27c42-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="27c42-127">Chacune de celles-ci a son propre [ \<liaison >](../../../../docs/framework/misc/binding.md) élément dans l’élément de type (binding).</span><span class="sxs-lookup"><span data-stu-id="27c42-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="27c42-128">L'attribut `bindingconfiguration` est utilisé pour distinguer plusieurs liaisons du même type.</span><span class="sxs-lookup"><span data-stu-id="27c42-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="27c42-129">Sa valeur est mise en correspondance avec la `name` attribut de la [ \<liaison >](../../../../docs/framework/misc/binding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="27c42-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="27c42-130">comment configurer un client de liaison à l’aide de la configuration, consultez [Comment : spécifier une liaison Client dans Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="27c42-130"> how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="27c42-131">Le `behaviorConfiguration` attribut est utilisé pour spécifier les [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) de la [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) le point de terminaison doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="27c42-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="27c42-132">Sa valeur est mise en correspondance avec la `name` attribut de la [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="27c42-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="27c42-133">Pour obtenir un exemple de configuration pour spécifier les comportements du client, consultez [configuration des comportements clients](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="27c42-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="27c42-134">L'attribut `contract` spécifie quel contrat le point de terminaison expose.</span><span class="sxs-lookup"><span data-stu-id="27c42-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="27c42-135">Cette valeur correspond au <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> de <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="27c42-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="27c42-136">La valeur par défaut est le nom de type complet de la classe qui implémente le service.</span><span class="sxs-lookup"><span data-stu-id="27c42-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="27c42-137">Configuration des métadonnées</span><span class="sxs-lookup"><span data-stu-id="27c42-137">Configuring Metadata</span></span>  
 <span data-ttu-id="27c42-138">Le [ \<métadonnées >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) élément est utilisé pour spécifier les paramètres utilisés pour enregistrer les métadonnées des extensions d’importation.</span><span class="sxs-lookup"><span data-stu-id="27c42-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="27c42-139">extension du système de métadonnées, consultez[extension du système de métadonnées](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="27c42-139"> extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c42-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27c42-140">See Also</span></span>  
 [<span data-ttu-id="27c42-141">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="27c42-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="27c42-142">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="27c42-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
