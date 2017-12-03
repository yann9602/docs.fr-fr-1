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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16a3b9b361048344993fdc338544b6b0ceb95387
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="e6859-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="e6859-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="e6859-103">Cette section de configuration contient tous les éléments de configuration ServiceModel de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6859-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6859-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6859-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6859-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6859-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e6859-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e6859-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6859-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6859-107">Attributes</span></span>  
 <span data-ttu-id="e6859-108">Aucun</span><span class="sxs-lookup"><span data-stu-id="e6859-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6859-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6859-109">Child Elements</span></span>  
  
|<span data-ttu-id="e6859-110">Élément</span><span class="sxs-lookup"><span data-stu-id="e6859-110">Element</span></span>|<span data-ttu-id="e6859-111">Description</span><span class="sxs-lookup"><span data-stu-id="e6859-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6859-112">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e6859-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="e6859-113">Cette section définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e6859-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e6859-114">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="e6859-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="e6859-115">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="e6859-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="e6859-116">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="e6859-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e6859-117">Cette section contient une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e6859-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="e6859-118">Chaque entrée est identifiée par son `name` unique.</span><span class="sxs-lookup"><span data-stu-id="e6859-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="e6859-119">Les services utilisent les liaisons en les liant à l'aide de `name`.</span><span class="sxs-lookup"><span data-stu-id="e6859-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="e6859-120">\<client ></span><span class="sxs-lookup"><span data-stu-id="e6859-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="e6859-121">Cette section contient la liste des points de terminaison utilisés par un client pour se connecter à un service.</span><span class="sxs-lookup"><span data-stu-id="e6859-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="e6859-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="e6859-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="e6859-123">Cette section définit des contrats COM activés pour interagir avec WCF et COM.</span><span class="sxs-lookup"><span data-stu-id="e6859-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="e6859-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e6859-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="e6859-125">Cette section peut uniquement être définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="e6859-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="e6859-126">Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e6859-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e6859-127">Chaque collection définit des éléments de comportement consommés respectivement par tous les points de terminaison et services de [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e6859-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="e6859-128">Si un comportement est défini dans les `<commonBehaviors>` et `<behaviors>` sections, le comportement dans le \<comportements > section est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="e6859-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="e6859-129">\<extensions ></span><span class="sxs-lookup"><span data-stu-id="e6859-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="e6859-130">Cette section contient une collection d'extensions qui permettent à l'utilisateur de créer des liaisons, des comportements et d'autres aspects d'extensions définis par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6859-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="e6859-131">\<Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e6859-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="e6859-132">Cette section contient les paramètres des fonctionnalités de diagnostic de WCF.</span><span class="sxs-lookup"><span data-stu-id="e6859-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="e6859-133">L'utilisateur peut activer/désactiver le suivi, les compteurs de performance et le fournisseur WMI et ajouter des filtres de messages personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e6859-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="e6859-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="e6859-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="e6859-135">Cette section définit un ensemble de mappage de protocole par défaut entre les schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="e6859-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="e6859-136">\<routage ></span><span class="sxs-lookup"><span data-stu-id="e6859-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e6859-137">Cette section définit un jeu de filtres de routage, qui détermine le type de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l'évaluation des messages entrants, ainsi que des tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu'un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="e6859-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="e6859-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="e6859-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="e6859-139">Cette section définit le type instancié par l'environnement d'hébergement de service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="e6859-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="e6859-140">Si cette section est vide, le type par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e6859-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="e6859-141">\<Services ></span><span class="sxs-lookup"><span data-stu-id="e6859-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="e6859-142">Cette section contient une collection de services.</span><span class="sxs-lookup"><span data-stu-id="e6859-142">The section contains a collection of services.</span></span> <span data-ttu-id="e6859-143">Pour chaque service défini dans l'assembly, cet élément contient un élément `service` indiquant les paramètres du service.</span><span class="sxs-lookup"><span data-stu-id="e6859-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="e6859-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="e6859-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e6859-145">Cette section définit une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés réutilisables.</span><span class="sxs-lookup"><span data-stu-id="e6859-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="e6859-146">Un point de terminaison standard possède un ou plusieurs attributs d'adresse, de liaison et de contrat ayant une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="e6859-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="e6859-147">Par exemple, dans le point de terminaison de découverte, le contrat est fixe.</span><span class="sxs-lookup"><span data-stu-id="e6859-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="e6859-148">Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e6859-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6859-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6859-149">Parent Elements</span></span>  
  
|<span data-ttu-id="e6859-150">Élément</span><span class="sxs-lookup"><span data-stu-id="e6859-150">Element</span></span>|<span data-ttu-id="e6859-151">Description</span><span class="sxs-lookup"><span data-stu-id="e6859-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6859-152">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e6859-152">\<configuration></span></span>|<span data-ttu-id="e6859-153">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="e6859-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6859-154">Remarques</span><span class="sxs-lookup"><span data-stu-id="e6859-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="e6859-155"> n'ajoute pas d'éléments aux sections de configuration d'autres produits.</span><span class="sxs-lookup"><span data-stu-id="e6859-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="e6859-156">Les services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e6859-156">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e6859-157">Un assembly peut contenir n'importe quel nombre de services.</span><span class="sxs-lookup"><span data-stu-id="e6859-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="e6859-158">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="e6859-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e6859-159">Cette section et son contenu définissent le contrat, le comportement et les points de terminaison du service en question.</span><span class="sxs-lookup"><span data-stu-id="e6859-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e6859-160">Seul l'attribut `name` d'un service est requis.</span><span class="sxs-lookup"><span data-stu-id="e6859-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="e6859-161">Par défaut, le nom d'un service décrit le type CLR sous-jacent utilisé pour implémenter un service ; toutefois, vous pouvez modifier la propriété ConfigurationName d'un <xref:System.ServiceModel.ServiceContractAttribute> pour remplacer la spécification de type CLR.</span><span class="sxs-lookup"><span data-stu-id="e6859-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="e6859-162">L'attribut `behaviorConfiguration` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e6859-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="e6859-163">Il identifie le comportement utilisé par un service.</span><span class="sxs-lookup"><span data-stu-id="e6859-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="e6859-164">Le comportement spécifié par cet attribut doit être lié à un comportement de service défini dans l'étendue du même fichier de configuration (c'est-à-dire le même fichier ou un fichier parent).</span><span class="sxs-lookup"><span data-stu-id="e6859-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="e6859-165">Chaque service expose un ou plusieurs points de terminaison définis dans un élément `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="e6859-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="e6859-166">Chaque point de terminaison possède sa propre adresse et sa propre liaison.</span><span class="sxs-lookup"><span data-stu-id="e6859-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="e6859-167">Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.</span><span class="sxs-lookup"><span data-stu-id="e6859-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="e6859-168">Les liaisons sont liées aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e6859-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e6859-169">L'attribut `binding` définit la section dans laquelle la liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="e6859-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="e6859-170">L'attribut `bindingConfiguration` définit parmi les liaisons configurées figurant dans la section de liaison celle qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e6859-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="e6859-171">Une section de liaison peut définir plusieurs liaisons configurées.</span><span class="sxs-lookup"><span data-stu-id="e6859-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6859-172">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6859-172">Example</span></span>  
 <span data-ttu-id="e6859-173">Voici un exemple de fichier de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="e6859-173">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6859-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6859-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
