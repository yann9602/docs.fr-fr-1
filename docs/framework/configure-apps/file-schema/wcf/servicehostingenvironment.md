---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5770cb8fd68eb68145f3f7fbcf197302883efe9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="34f9d-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="34f9d-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="34f9d-103">Cet élément définit le type instancié par l'environnement d'hébergement de service correspondant à un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="34f9d-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="34f9d-104">Si cet élément est vide, c'est le type par défaut qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="34f9d-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="34f9d-105">Cet élément ne peut être utilisé qu'au niveau des fichiers de configuration de l'application ou de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="34f9d-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="34f9d-106">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="34f9d-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="34f9d-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="34f9d-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f9d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34f9d-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34f9d-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="34f9d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34f9d-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="34f9d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34f9d-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="34f9d-111">Attributes</span></span>  
  
|<span data-ttu-id="34f9d-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="34f9d-112">Attribute</span></span>|<span data-ttu-id="34f9d-113">Description</span><span class="sxs-lookup"><span data-stu-id="34f9d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34f9d-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="34f9d-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="34f9d-115">Valeur booléenne indiquant si le mode de compatibilité ASP.NET a été activé pour l'application actuelle.</span><span class="sxs-lookup"><span data-stu-id="34f9d-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="34f9d-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="34f9d-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="34f9d-117">Lorsque cet attribut a la valeur `true`, les demandes transmises aux services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] passent par le pipeline HTTP ASP.NET ; en outre, les communications via des protocoles non-HTTP sont interdites.</span><span class="sxs-lookup"><span data-stu-id="34f9d-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="34f9d-118">Pour plus d’informations, consultez [Services WCF et ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="34f9d-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="34f9d-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="34f9d-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="34f9d-120">Entier indiquant la quantité minimale de mémoire disponible nécessaire au système pour permettre l'activation d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="34f9d-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="34f9d-121">**Attention :** spécification de cet attribut avec une confiance partielle dans le fichier web.config d’un [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service entraîne un <xref:System.Security.SecurityException> lorsque le service est exécuté.</span><span class="sxs-lookup"><span data-stu-id="34f9d-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="34f9d-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="34f9d-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="34f9d-123">Valeur booléenne qui spécifie si plusieurs liaisons IIS par site sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="34f9d-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="34f9d-124">Les services IIS se composent de sites Web, qui sont des conteneurs d'applications virtuelles contenant des répertoires virtuels.</span><span class="sxs-lookup"><span data-stu-id="34f9d-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="34f9d-125">L'application dans un site est accessible par le biais d'une ou de plusieurs liaisons IIS.</span><span class="sxs-lookup"><span data-stu-id="34f9d-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="34f9d-126">Une liaison IIS fournit deux informations : un protocole de liaison et des informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="34f9d-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="34f9d-127">Le protocole de liaison définit le schéma selon lequel la communication est établie et les informations de liaison sont les informations utilisées pour accéder au site.</span><span class="sxs-lookup"><span data-stu-id="34f9d-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="34f9d-128">HTTP peut être un exemple de protocole de liaison, tandis que les informations de liaison peuvent contenir une adresse IP, un port, un en-tête d'hôte, etc.</span><span class="sxs-lookup"><span data-stu-id="34f9d-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="34f9d-129">IIS prend en charge la spécification de plusieurs liaisons IIS par site, ce qui entraîne plusieurs adresses de base par schéma.</span><span class="sxs-lookup"><span data-stu-id="34f9d-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="34f9d-130">Toutefois, un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hébergé sur un site n'autorise la liaison qu'avec un seul baseAddress par schéma.</span><span class="sxs-lookup"><span data-stu-id="34f9d-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="34f9d-131">Pour autoriser plusieurs liaisons IIS par site pour un service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], affectez à cet attribut la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="34f9d-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="34f9d-132">Notez que la spécification de plusieurs liaisons de site est prise en charge uniquement pour le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="34f9d-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="34f9d-133">L'adresse des points de terminaison dans le fichier de configuration doit être un URI complet.</span><span class="sxs-lookup"><span data-stu-id="34f9d-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34f9d-134">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="34f9d-134">Child Elements</span></span>  
  
|<span data-ttu-id="34f9d-135">Élément</span><span class="sxs-lookup"><span data-stu-id="34f9d-135">Element</span></span>|<span data-ttu-id="34f9d-136">Description</span><span class="sxs-lookup"><span data-stu-id="34f9d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34f9d-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="34f9d-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="34f9d-138">Collection des éléments de configuration qui spécifient des filtres de préfixe pour les adresses de base utilisée par l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="34f9d-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="34f9d-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="34f9d-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="34f9d-140">Section de configuration qui décrit les paramètres d'activation.</span><span class="sxs-lookup"><span data-stu-id="34f9d-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="34f9d-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="34f9d-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="34f9d-142">Collection des éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="34f9d-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34f9d-143">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="34f9d-143">Parent Elements</span></span>  
  
|<span data-ttu-id="34f9d-144">Élément</span><span class="sxs-lookup"><span data-stu-id="34f9d-144">Element</span></span>|<span data-ttu-id="34f9d-145">Description</span><span class="sxs-lookup"><span data-stu-id="34f9d-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34f9d-146">serviceModel</span><span class="sxs-lookup"><span data-stu-id="34f9d-146">serviceModel</span></span>|<span data-ttu-id="34f9d-147">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="34f9d-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34f9d-148">Remarques</span><span class="sxs-lookup"><span data-stu-id="34f9d-148">Remarks</span></span>  
 <span data-ttu-id="34f9d-149">Par défaut, les services WCF sont exécutés conjointement à ASP.NET dans les domaines d'application hébergés (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="34f9d-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="34f9d-150">Bien que WCF et ASP.NET puissent coexister sur le même domaine AppDomain, les demandes WCF ne sont pas traitées par défaut par le pipeline HTTP d'ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="34f9d-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="34f9d-151">En conséquence, plusieurs éléments de la plate-forme d'application ASP.NET ne sont pas disponibles pour les services WCF.</span><span class="sxs-lookup"><span data-stu-id="34f9d-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="34f9d-152">Il s'agit des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="34f9d-152">These include</span></span>  
  
-   <span data-ttu-id="34f9d-153">Autorisation de l'URL/du fichier ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34f9d-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="34f9d-154">Emprunt d'identité ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34f9d-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="34f9d-155">État de session basé sur les cookies</span><span class="sxs-lookup"><span data-stu-id="34f9d-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="34f9d-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="34f9d-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="34f9d-157">Extensibilité de pipeline via HttpModule personnalisé</span><span class="sxs-lookup"><span data-stu-id="34f9d-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="34f9d-158">Si vos services WCF doivent fonctionner dans le contexte ASP.NET et communiquer uniquement via HTTP, vous pouvez utiliser le mode de compatibilité ASP.NET de WCF.</span><span class="sxs-lookup"><span data-stu-id="34f9d-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="34f9d-159">Ce mode est activé lorsque l'attribut `aspNetCompatibilityEnabled` a la valeur `true` au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="34f9d-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="34f9d-160">Les implémentations de service doivent déclarer leur capacité de fonctionner en mode de compatibilité à l'aide de la classe <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="34f9d-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="34f9d-161">Lorsque le mode de compatibilité est activé :</span><span class="sxs-lookup"><span data-stu-id="34f9d-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="34f9d-162">L'autorisation de l'URL/du fichier ASP.NET est appliquée avant l'autorisation WCF.</span><span class="sxs-lookup"><span data-stu-id="34f9d-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="34f9d-163">Une décision d'autorisation est basée sur l'identité de la demande au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="34f9d-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="34f9d-164">Les identités au niveau du message sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="34f9d-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="34f9d-165">Les opérations de service WCF commencent à s'exécuter dans le contexte d'emprunt d'identité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="34f9d-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="34f9d-166">Si les emprunts d'identité ASP.NET et WCF sont tous deux activés pour un service spécifique, c'est le contexte d'emprunt d'identité WCF qui est appliqué.</span><span class="sxs-lookup"><span data-stu-id="34f9d-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="34f9d-167">HttpContext.Current peut être utilisé à partir du code de service WCF ; cette opération permet d'empêcher l'exposition des points de terminaison non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="34f9d-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="34f9d-168">Les demandes WCF sont traitées par le pipeline ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="34f9d-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="34f9d-169">Les HttpModules ayant été configurés pour agir sur les requêtes entrantes peuvent également traiter des demandes WCF.</span><span class="sxs-lookup"><span data-stu-id="34f9d-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="34f9d-170">Ils peuvent inclure des composants de plate-forme ASP.NET (par exemple, <xref:System.Web.SessionState.SessionStateModule>), ainsi que des modules tiers personnalisés.</span><span class="sxs-lookup"><span data-stu-id="34f9d-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34f9d-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="34f9d-171">Example</span></span>  
 <span data-ttu-id="34f9d-172">L'exemple de code suivant indique comment activer le Mode de compatibilité ASP.</span><span class="sxs-lookup"><span data-stu-id="34f9d-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="34f9d-173">Code</span><span class="sxs-lookup"><span data-stu-id="34f9d-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34f9d-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f9d-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="34f9d-175">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="34f9d-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="34f9d-176">Services WCF et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="34f9d-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
