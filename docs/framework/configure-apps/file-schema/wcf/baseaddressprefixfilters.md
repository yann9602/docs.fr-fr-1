---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a1c2e5e887ceaadf3db6f51991d53c3db8fb6ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="38940-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="38940-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="38940-103">Représente une collection d'éléments de configuration spécifiant des filtres directs qui fournissent un mécanisme permettant de sélectionner les liaisons de services IIS appropriées lors de l'hébergement d'une l'application [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dans IIS.</span><span class="sxs-lookup"><span data-stu-id="38940-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="38940-104">\<baseAddressPrefixFilters > ne pas reconnaître le « localhost », utilisez le nom d’ordinateur complet à la place.</span><span class="sxs-lookup"><span data-stu-id="38940-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="38940-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38940-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="38940-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="38940-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38940-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38940-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38940-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38940-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38940-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38940-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38940-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="38940-110">Attributes</span></span>  
 <span data-ttu-id="38940-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38940-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38940-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38940-112">Child Elements</span></span>  
  
|<span data-ttu-id="38940-113">Élément</span><span class="sxs-lookup"><span data-stu-id="38940-113">Element</span></span>|<span data-ttu-id="38940-114">Description</span><span class="sxs-lookup"><span data-stu-id="38940-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38940-115">\<add></span><span class="sxs-lookup"><span data-stu-id="38940-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="38940-116">Ajoute un élément de configuration spécifiant un filtre de préfixe pour les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="38940-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38940-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38940-117">Parent Elements</span></span>  
  
|<span data-ttu-id="38940-118">Élément</span><span class="sxs-lookup"><span data-stu-id="38940-118">Element</span></span>|<span data-ttu-id="38940-119">Description</span><span class="sxs-lookup"><span data-stu-id="38940-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38940-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="38940-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="38940-121">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="38940-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38940-122">Notes</span><span class="sxs-lookup"><span data-stu-id="38940-122">Remarks</span></span>  
 <span data-ttu-id="38940-123">Un filtre de préfixe permet aux fournisseurs d'hébergement partagé de spécifier les URI que le service doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="38940-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="38940-124">Il permet aux hôtes partagés d'héberger plusieurs applications avec différentes adresses de base pour la même méthode sur le même site.</span><span class="sxs-lookup"><span data-stu-id="38940-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="38940-125">Les sites Web IIS sont des conteneurs d'applications virtuelles qui contiennent des répertoires virtuels.</span><span class="sxs-lookup"><span data-stu-id="38940-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="38940-126">L'application dans un site est accessible par le biais d'une ou de plusieurs liaisons IIS.</span><span class="sxs-lookup"><span data-stu-id="38940-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="38940-127">Les liaisons IIS fournissent deux informations : un protocole de liaison et des informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="38940-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="38940-128">Le protocole de liaison (par exemple, HTTP) définit le modèle sur lequel la communication se produit, tandis que les informations de liaison (par exemple, adresse IP, port, en-tête de l'hôte) contiennent les données servant à accéder au site.</span><span class="sxs-lookup"><span data-stu-id="38940-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="38940-129">IIS prend en charge la spécification de plusieurs liaisons IIS pour chaque site, ce qui génère plusieurs adresses de base pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="38940-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="38940-130">Étant donné qu'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hébergé sur un site autorise la liaison avec une seule adresse de base pour chaque modèle, vous pouvez utiliser la fonctionnalité du filtre de préfixe pour choisir l'adresse de base requise du service hébergé.</span><span class="sxs-lookup"><span data-stu-id="38940-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="38940-131">Les adresses de base entrantes, fournies par IIS, sont filtrées selon le filtre de la liste de préfixes facultative.</span><span class="sxs-lookup"><span data-stu-id="38940-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="38940-132">Par exemple, votre site peut contenir les adresses de base suivantes.</span><span class="sxs-lookup"><span data-stu-id="38940-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="38940-133">Vous pouvez utiliser le fichier de configuration suivant pour spécifier un filtre de préfixe au niveau AppDomain.</span><span class="sxs-lookup"><span data-stu-id="38940-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="38940-134">Dans cet exemple, `net.tcp://test1.fabrikam.com:8000` et `http://test2.fabrikam.com:9000` sont les seules adresses de base pouvant être passées pour leur modèle respectif.</span><span class="sxs-lookup"><span data-stu-id="38940-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="38940-135">Par défaut, si aucun préfixe n'est spécifié, toutes les adresses sont transmises.</span><span class="sxs-lookup"><span data-stu-id="38940-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="38940-136">La spécification du préfixe autorise uniquement la transmission de l'adresse de base correspondante pour ce modèle.</span><span class="sxs-lookup"><span data-stu-id="38940-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38940-137">Le filtre ne prend pas en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="38940-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="38940-138">En outre, les adresses de base fournies par IIS peuvent avoir des adresses liées à d'autres modèles non présents dans la liste `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="38940-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="38940-139">Ces adresses ne sont pas éliminées par filtrage.</span><span class="sxs-lookup"><span data-stu-id="38940-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38940-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38940-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="38940-141">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="38940-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
