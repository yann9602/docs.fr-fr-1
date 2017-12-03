---
title: "&lt;endpoint&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c466d7f7f00d7fd2358f0d5d71c0b705f316f66f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointgt-element"></a><span data-ttu-id="70969-102">&lt;endpoint&gt;, élément</span><span class="sxs-lookup"><span data-stu-id="70969-102">&lt;endpoint&gt; element</span></span>
<span data-ttu-id="70969-103">Spécifie la liaison, le contrat et les propriétés d’adresse d’un point de terminaison de service, utilisé pour exposer des services.</span><span class="sxs-lookup"><span data-stu-id="70969-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="70969-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="70969-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="70969-105">\<service ></span><span class="sxs-lookup"><span data-stu-id="70969-105">\<service></span></span>  
<span data-ttu-id="70969-106">\<point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="70969-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70969-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70969-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70969-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70969-108">Attributes and Elements</span></span>  
 <span data-ttu-id="70969-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70969-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70969-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="70969-110">Attributes</span></span>  
  
|<span data-ttu-id="70969-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="70969-111">Attribute</span></span>|<span data-ttu-id="70969-112">Description</span><span class="sxs-lookup"><span data-stu-id="70969-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70969-113">address</span><span class="sxs-lookup"><span data-stu-id="70969-113">address</span></span>|<span data-ttu-id="70969-114">Chaîne qui contient l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="70969-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="70969-115">L'adresse peut être spécifiée comme une adresse absolue ou relative.</span><span class="sxs-lookup"><span data-stu-id="70969-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="70969-116">Si une adresse relative est fournie, l'hôte doit fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison.</span><span class="sxs-lookup"><span data-stu-id="70969-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="70969-117">Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="70969-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="70969-118">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="70969-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="70969-119">behaviorConfiguration</span></span>|<span data-ttu-id="70969-120">Chaîne qui contient le nom du comportement à utiliser au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="70969-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="70969-121">liaison</span><span class="sxs-lookup"><span data-stu-id="70969-121">binding</span></span>|<span data-ttu-id="70969-122">Attribut de chaîne requis indiquant le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="70969-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="70969-123">Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé.</span><span class="sxs-lookup"><span data-stu-id="70969-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="70969-124">Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.</span><span class="sxs-lookup"><span data-stu-id="70969-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="70969-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="70969-125">bindingConfiguration</span></span>|<span data-ttu-id="70969-126">Chaîne qui spécifie le nom de la liaison à utiliser lorsque le point de terminaison est instancié.</span><span class="sxs-lookup"><span data-stu-id="70969-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="70969-127">Le nom de liaison doit être dans la portée, au niveau où le point de terminaison est défini.</span><span class="sxs-lookup"><span data-stu-id="70969-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="70969-128">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="70969-129">Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="70969-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="70969-130">Définissez cet attribut si vous essayez d'utiliser une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="70969-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="70969-131">Sinon, une exception peut être levée.</span><span class="sxs-lookup"><span data-stu-id="70969-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="70969-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="70969-132">bindingName</span></span>|<span data-ttu-id="70969-133">Chaîne qui spécifie le nom qualifié unique de la liaison pour l'exportation de définition à travers WSDL.</span><span class="sxs-lookup"><span data-stu-id="70969-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="70969-134">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="70969-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="70969-135">bindingNamespace</span></span>|<span data-ttu-id="70969-136">Chaîne qui spécifie le nom qualifié de l'espace de noms de la liaison pour l'exportation de définition à travers WSDL.</span><span class="sxs-lookup"><span data-stu-id="70969-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="70969-137">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="70969-138">contrat</span><span class="sxs-lookup"><span data-stu-id="70969-138">contract</span></span>|<span data-ttu-id="70969-139">Chaîne qui indique le contrat exposé par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="70969-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="70969-140">L'assembly doit implémenter le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="70969-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="70969-141">Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise.</span><span class="sxs-lookup"><span data-stu-id="70969-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="70969-142">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="70969-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="70969-143">endpointConfiguration</span></span>|<span data-ttu-id="70969-144">Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="70969-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="70969-145">Le même nom doit être défini dans la section `<standardEndpoints>`.</span><span class="sxs-lookup"><span data-stu-id="70969-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="70969-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="70969-146">isSystemEndpoint</span></span>|<span data-ttu-id="70969-147">Valeur booléenne qui spécifie si un point de terminaison est un point de terminaison d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="70969-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="70969-148">kind</span><span class="sxs-lookup"><span data-stu-id="70969-148">kind</span></span>|<span data-ttu-id="70969-149">Chaîne qui spécifie le type de point de terminaison standard appliqué.</span><span class="sxs-lookup"><span data-stu-id="70969-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="70969-150">Le type doit être inscrit dans la section `<extensions>` ou dans machine.config. Si rien n'est spécifié, un point de terminaison de service commun est créé.</span><span class="sxs-lookup"><span data-stu-id="70969-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="70969-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="70969-151">listenUriMode</span></span>|<span data-ttu-id="70969-152">Spécifie la manière dont le transport traite le `ListenUri` fourni sur lequel le service effectue son écoute.</span><span class="sxs-lookup"><span data-stu-id="70969-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="70969-153">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="70969-153">Valid values are</span></span><br /><br /> <span data-ttu-id="70969-154">-Explicite</span><span class="sxs-lookup"><span data-stu-id="70969-154">-   Explicit</span></span><br /><span data-ttu-id="70969-155">-Unique</span><span class="sxs-lookup"><span data-stu-id="70969-155">-   Unique</span></span><br /><br /> <span data-ttu-id="70969-156">La valeur par défaut est Explicit.</span><span class="sxs-lookup"><span data-stu-id="70969-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="70969-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="70969-157">listenUri</span></span>|<span data-ttu-id="70969-158">Chaîne qui spécifie l'URI au niveau duquel le point de terminaison de service effectue son écoute.</span><span class="sxs-lookup"><span data-stu-id="70969-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="70969-159">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70969-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="70969-160">name</span><span class="sxs-lookup"><span data-stu-id="70969-160">name</span></span>|<span data-ttu-id="70969-161">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="70969-161">Optional attribute.</span></span> <span data-ttu-id="70969-162">Chaîne qui spécifie le nom du point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="70969-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="70969-163">La valeur par défaut correspond à la concaténation du nom de la liaison et de celui de la description du contrat.</span><span class="sxs-lookup"><span data-stu-id="70969-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="70969-164">Les services peuvent disposer de plusieurs points de terminaison, l'attribut `name` du point de terminaison est donc différent du nom du service.</span><span class="sxs-lookup"><span data-stu-id="70969-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70969-165">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70969-165">Child Elements</span></span>  
  
|<span data-ttu-id="70969-166">Élément</span><span class="sxs-lookup"><span data-stu-id="70969-166">Element</span></span>|<span data-ttu-id="70969-167">Description</span><span class="sxs-lookup"><span data-stu-id="70969-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70969-168">\<en-têtes ></span><span class="sxs-lookup"><span data-stu-id="70969-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="70969-169">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="70969-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="70969-170">\<identité ></span><span class="sxs-lookup"><span data-stu-id="70969-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="70969-171">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="70969-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70969-172">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70969-172">Parent Elements</span></span>  
  
|<span data-ttu-id="70969-173">Élément</span><span class="sxs-lookup"><span data-stu-id="70969-173">Element</span></span>|<span data-ttu-id="70969-174">Description</span><span class="sxs-lookup"><span data-stu-id="70969-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70969-175">\<service ></span><span class="sxs-lookup"><span data-stu-id="70969-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="70969-176">Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="70969-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70969-177">Exemple</span><span class="sxs-lookup"><span data-stu-id="70969-177">Example</span></span>  
 <span data-ttu-id="70969-178">Il s'agit d'un exemple de configuration de point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="70969-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="70969-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70969-179">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [<span data-ttu-id="70969-180">Points de terminaison : Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="70969-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="70969-181">Comment : créer un point de terminaison de Service dans la Configuration</span><span class="sxs-lookup"><span data-stu-id="70969-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
