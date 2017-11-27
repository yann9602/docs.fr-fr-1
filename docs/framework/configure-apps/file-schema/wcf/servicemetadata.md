---
title: '&lt;serviceMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a771b3b89c9031a011185a579e70767081d20597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicemetadatagt"></a><span data-ttu-id="4e402-102">&lt;serviceMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="4e402-102">&lt;serviceMetadata&gt;</span></span>
<span data-ttu-id="4e402-103">Spécifie la publication de métadonnées de service et des informations associées.</span><span class="sxs-lookup"><span data-stu-id="4e402-103">Specifies the publication of service metadata and associated information.</span></span>  
  
<span data-ttu-id="4e402-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4e402-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4e402-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="4e402-105">\<behaviors></span></span>  
<span data-ttu-id="4e402-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4e402-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4e402-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4e402-107">\<behavior></span></span>  
<span data-ttu-id="4e402-108">\<serviceMetadata ></span><span class="sxs-lookup"><span data-stu-id="4e402-108">\<serviceMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e402-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e402-109">Syntax</span></span>  
  
```xml
<serviceMetadata externalMetadataLocation="String"  
                 httpGetBinding="String" 
                 httpGetBindingConfiguration="String"  
                 httpGetEnabled="Boolean" 
                 httpGetUrl="String" 
                 httpsGetBinding="String" 
                 httpsGetBindingConfiguration="String"  
                 httpsGetEnabled="Boolean"   
                 httpsGetUrl="String"  
                 policyVersion="Policy12/Policy15" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e402-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e402-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4e402-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e402-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e402-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e402-112">Attributes</span></span>  
  
|<span data-ttu-id="4e402-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e402-113">Attribute</span></span>|<span data-ttu-id="4e402-114">Description</span><span class="sxs-lookup"><span data-stu-id="4e402-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e402-115">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="4e402-115">externalMetadataLocation</span></span>|<span data-ttu-id="4e402-116">Uri contenant l'emplacement d'un fichier WSDL renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX au lieu du WSDL généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4e402-116">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="4e402-117">Lorsque cet attribut n'est pas défini, le WSDL par défaut est renvoyé.</span><span class="sxs-lookup"><span data-stu-id="4e402-117">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="4e402-118">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="4e402-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="4e402-119">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="4e402-119">httpGetBinding</span></span>|<span data-ttu-id="4e402-120">Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="4e402-120">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="4e402-121">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e402-121">This setting is optional.</span></span> <span data-ttu-id="4e402-122">En l'absence de spécification, les liaisons par défaut seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="4e402-122">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="4e402-123">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="4e402-123">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="4e402-124">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e402-124">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="4e402-125">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4e402-125">httpGetBindingConfiguration</span></span>|<span data-ttu-id="4e402-126">Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4e402-126">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="4e402-127">Le même nom doit être défini dans la section `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="4e402-127">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="4e402-128">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="4e402-128">httpGetEnabled</span></span>|<span data-ttu-id="4e402-129">Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="4e402-129">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="4e402-130">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="4e402-130">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4e402-131">Si l'attribut httpGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».</span><span class="sxs-lookup"><span data-stu-id="4e402-131">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="4e402-132">Par exemple, si l'adresse du service est "http://localhost:8080/CalculatorService", l'adresse des métadonnées HTTP/Get est "http://localhost:8080/CalculatorService?wsdl".</span><span class="sxs-lookup"><span data-stu-id="4e402-132">For example, if the service address is "http://localhost:8080/CalculatorService", the HTTP/Get metadata address is "http://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="4e402-133">Si cette propriété est `false`, ou l’adresse du service n’est pas basé sur HTTP ou HTTPS, « ? wsdl » est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4e402-133">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="4e402-134">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="4e402-134">httpGetUrl</span></span>|<span data-ttu-id="4e402-135">URI indiquant l'adresse utilisée pour publier les métadonnées correspondant à la récupération à l'aide d'une demande HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="4e402-135">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="4e402-136">Si l'URI relatif est spécifié, il sera traité comme étant relatif à l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="4e402-136">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="4e402-137">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="4e402-137">httpsGetBinding</span></span>|<span data-ttu-id="4e402-138">Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="4e402-138">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="4e402-139">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e402-139">This setting is optional.</span></span> <span data-ttu-id="4e402-140">En l'absence de spécification, les liaisons par défaut seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="4e402-140">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="4e402-141">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="4e402-141">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="4e402-142">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e402-142">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="4e402-143">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4e402-143">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="4e402-144">Chaîne qui définit le nom de la liaison spécifiée dans l'attribut `httpsGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4e402-144">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="4e402-145">Le même nom doit être défini dans la section `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="4e402-145">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="4e402-146">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="4e402-146">httpsGetEnabled</span></span>|<span data-ttu-id="4e402-147">Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="4e402-147">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="4e402-148">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="4e402-148">The default is `false`.</span></span><br /><br /> <span data-ttu-id="4e402-149">Si l'attribut httpsGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».</span><span class="sxs-lookup"><span data-stu-id="4e402-149">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="4e402-150">Par exemple, si l'adresse du service est "https://localhost:8080/CalculatorService", l'adresse des métadonnées HTTP/Get est "https://localhost:8080/CalculatorService?wsdl".</span><span class="sxs-lookup"><span data-stu-id="4e402-150">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="4e402-151">Si cette propriété est `false`, ou l’adresse du service n’est pas basé sur HTTP ou HTTPS, « ? wsdl » est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4e402-151">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="4e402-152">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="4e402-152">httpsGetUrl</span></span>|<span data-ttu-id="4e402-153">URI indiquant l'adresse utilisée pour publier les métadonnées afin d'effectuer une récupération à l'aide d'une demande HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="4e402-153">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="4e402-154">policyVersion</span><span class="sxs-lookup"><span data-stu-id="4e402-154">policyVersion</span></span>|<span data-ttu-id="4e402-155">Chaîne indiquant la version de la spécification WS-Policy utilisée.</span><span class="sxs-lookup"><span data-stu-id="4e402-155">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="4e402-156">Cet attribut est de type <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="4e402-156">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e402-157">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e402-157">Child Elements</span></span>  
 <span data-ttu-id="4e402-158">None</span><span class="sxs-lookup"><span data-stu-id="4e402-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e402-159">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e402-159">Parent Elements</span></span>  
  
|<span data-ttu-id="4e402-160">Élément</span><span class="sxs-lookup"><span data-stu-id="4e402-160">Element</span></span>|<span data-ttu-id="4e402-161">Description</span><span class="sxs-lookup"><span data-stu-id="4e402-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e402-162">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="4e402-162">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4e402-163">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="4e402-163">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e402-164">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e402-164">Remarks</span></span>  
 <span data-ttu-id="4e402-165">Cet élément de configuration permet de contrôler les métadonnées qui publient les fonctionnalités d’un service.</span><span class="sxs-lookup"><span data-stu-id="4e402-165">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="4e402-166">Pour empêcher la divulgation involontaire de métadonnées de service potentiellement sensibles, la publication de métadonnées est désactivée par défaut dans la configuration des services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4e402-166">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="4e402-167">Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="4e402-167">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="4e402-168">À l'aide de cet élément de configuration, vous pouvez activer ce comportement de publication pour votre service.</span><span class="sxs-lookup"><span data-stu-id="4e402-168">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="4e402-169">Pour obtenir un exemple détaillé de la configuration de ce comportement, consultez [comportement de publication de métadonnées](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="4e402-169">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="4e402-170">Les attributs facultatifs `httpGetBinding` et `httpsGetBinding` vous permettent de configurer les liaisons utilisées pour la récupération de métadonnées via HTTP GET (ou HTTPS GET).</span><span class="sxs-lookup"><span data-stu-id="4e402-170">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="4e402-171">S'ils ne sont pas spécifiés, les liaisons par défaut (`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS) sont utilisées pour la récupération des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4e402-171">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="4e402-172">Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées.</span><span class="sxs-lookup"><span data-stu-id="4e402-172">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="4e402-173">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="4e402-173">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="4e402-174">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e402-174">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="4e402-175">Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS (SSL over HTTP).</span><span class="sxs-lookup"><span data-stu-id="4e402-175">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="4e402-176">Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="4e402-176">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="4e402-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Ensuite, ajoutez cet élément à la configuration du service et affectez la valeur `httpsGetEnabled` à l'attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="4e402-177">([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="4e402-178">Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `httpsGetUrl`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4e402-178">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml
<behaviors>  
  <serviceBehaviors>  
    <behavior name="NewBehavior">  
      <serviceMetadata httpsGetEnabled="true"   
                       httpsGetUrl="https://myComputerName/myEndpoint" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="example"></a><span data-ttu-id="4e402-179">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e402-179">Example</span></span>  
 <span data-ttu-id="4e402-180">L’exemple suivant configurer un service pour exposer des métadonnées à l’aide de la \<serviceMetadata > élément.</span><span class="sxs-lookup"><span data-stu-id="4e402-180">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="4e402-181">Il configure également un point de terminaison afin d'exposer le contrat `IMetadataExchange` comme implémentation d'un protocole WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="4e402-181">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="4e402-182">L'exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dans laquelle le mode de sécurité a la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="4e402-182">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="4e402-183">Une adresse relative de « mex » est utilisée dans le point de terminaison. Lorsqu'elle est résolue par rapport à l'adresse de base des services, l'adresse de point de terminaison est http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="4e402-183">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService" 
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <!-- The serviceMetadata behavior publishes metadata through   
               the IMetadataExchange contract. When this behavior is   
               present, you can expose this contract through an endpoint   
               as shown above. Setting httpGetEnabled to true publishes   
               the service's WSDL at the <baseaddress>?wsdl  
               eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e402-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e402-184">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 [<span data-ttu-id="4e402-185">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="4e402-185">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="4e402-186">Comportement de publication des métadonnées</span><span class="sxs-lookup"><span data-stu-id="4e402-186">Metadata Publishing Behavior</span></span>](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
