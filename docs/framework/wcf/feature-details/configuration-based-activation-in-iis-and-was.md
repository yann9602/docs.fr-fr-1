---
title: "Activation basée sur la configuration dans les services IIS et WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0938b98a3f079d03653df55f10c26a4a62db5bf3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="5c771-102">Activation basée sur la configuration dans les services IIS et WAS</span><span class="sxs-lookup"><span data-stu-id="5c771-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="5c771-103">Généralement, lorsque vous hébergez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service), vous devez fournir un fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="5c771-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="5c771-104">Le fichier .svc contient le nom du service et une fabrique hôte de service personnalisée facultative.</span><span class="sxs-lookup"><span data-stu-id="5c771-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="5c771-105">Ce fichier supplémentaire facilite encore la gestion.</span><span class="sxs-lookup"><span data-stu-id="5c771-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="5c771-106">Grâce à la fonctionnalité d'activation basée sur la configuration, le fichier .svc et, par conséquent, les surcharges associées ne sont plus indispensables.</span><span class="sxs-lookup"><span data-stu-id="5c771-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="5c771-107">Activation basée sur la configuration</span><span class="sxs-lookup"><span data-stu-id="5c771-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="5c771-108">L'activation basée sur la configuration prend les métadonnées qui étaient placées dans le fichier .svc et les met dans le fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="5c771-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="5c771-109">Dans le <`serviceHostingEnvironment`> élément est un <`serviceActivations`> élément.</span><span class="sxs-lookup"><span data-stu-id="5c771-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="5c771-110">Dans le <`serviceActivations`> élément sont un ou plusieurs <`add`> éléments, un pour chaque service hébergé.</span><span class="sxs-lookup"><span data-stu-id="5c771-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="5c771-111">Le <`add`> élément contient des attributs qui vous permettent de définir l’adresse relative pour le service et le type de service ou une fabrique d’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="5c771-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="5c771-112">L'exemple de code de configuration suivant montre comment cette section est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5c771-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c771-113">Chaque <`add`> élément doit spécifier un service ou un attribut factory.</span><span class="sxs-lookup"><span data-stu-id="5c771-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="5c771-114">Il est possible de spécifier les deux.</span><span class="sxs-lookup"><span data-stu-id="5c771-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="5c771-115">Grâce à ce code dans le fichier Web.config, vous pouvez placer le code source du service dans le répertoire App_Code de l'application ou un assembly compilé dans le répertoire Bin de l'application.</span><span class="sxs-lookup"><span data-stu-id="5c771-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="5c771-116">Lors d'une activation basée sur la configuration, le code inline dans les fichiers .svc n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5c771-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="5c771-117">Le `relativeAddress` attribut doit être défini comme une adresse relative «\<sous-répertoire > / service.svc » ou « ~ /\<sub/service.svc ».</span><span class="sxs-lookup"><span data-stu-id="5c771-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="5c771-118">Une exception de configuration est levée si vous inscrivez une adresse relative sans extension connue, associée à WCF.</span><span class="sxs-lookup"><span data-stu-id="5c771-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="5c771-119">L'adresse relative spécifiée est relative à la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="5c771-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="5c771-120">En raison du modèle hiérarchique de configuration, les adresses relatives enregistrées au niveau de l'ordinateur et du site sont héritées par les applications virtuelles.</span><span class="sxs-lookup"><span data-stu-id="5c771-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="5c771-121">Les inscriptions dans un fichier de configuration sont prioritaires sur les paramètres d'un fichier .svc, .xamlx, .xoml ou autre.</span><span class="sxs-lookup"><span data-stu-id="5c771-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="5c771-122">Toute '\' (barre oblique inverse) qui se trouve dans un URI envoyé aux services IIS/WAS est automatiquement convertie en '/' (barre oblique).</span><span class="sxs-lookup"><span data-stu-id="5c771-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="5c771-123">Si une adresse relative contenant un signe '\' est ajoutée et que vous envoyez à IIS un URI utilisant cette adresse relative, la barre oblique inverse est convertie en barre oblique et IIS ne peut pas le faire correspondre à l'adresse relative.</span><span class="sxs-lookup"><span data-stu-id="5c771-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="5c771-124">IIS envoie des informations de suivi qui indiquent qu'aucune correspondance n'a été trouvée.</span><span class="sxs-lookup"><span data-stu-id="5c771-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c771-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c771-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="5c771-126">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="5c771-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="5c771-127">Vue d’ensemble des Services de Workflow hébergement</span><span class="sxs-lookup"><span data-stu-id="5c771-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="5c771-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="5c771-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="5c771-129">Fonctionnalités d’hébergement de Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="5c771-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
