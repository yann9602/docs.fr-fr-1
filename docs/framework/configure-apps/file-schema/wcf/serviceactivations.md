---
title: '&lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a7d0984a5fafa7f03a589570e2a1aa2546dd8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="f7057-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="f7057-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="f7057-103">Élément de configuration qui vous permet d'ajouter des paramètres qui définissent des paramètres d'activation de services virtuels mappés aux types de service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7057-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="f7057-104">Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="f7057-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="f7057-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f7057-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7057-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f7057-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="f7057-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="f7057-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7057-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7057-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7057-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f7057-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f7057-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f7057-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7057-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f7057-111">Attributes</span></span>  
 <span data-ttu-id="f7057-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f7057-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7057-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f7057-113">Child Elements</span></span>  
  
|<span data-ttu-id="f7057-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f7057-114">Element</span></span>|<span data-ttu-id="f7057-115">Description</span><span class="sxs-lookup"><span data-stu-id="f7057-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7057-116">\<add></span><span class="sxs-lookup"><span data-stu-id="f7057-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="f7057-117">Ajoute un élément de configuration qui spécifie l'activation d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="f7057-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7057-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f7057-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f7057-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f7057-119">Element</span></span>|<span data-ttu-id="f7057-120">Description</span><span class="sxs-lookup"><span data-stu-id="f7057-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7057-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f7057-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="f7057-122">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="f7057-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7057-123">Notes</span><span class="sxs-lookup"><span data-stu-id="f7057-123">Remarks</span></span>  
 <span data-ttu-id="f7057-124">L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="f7057-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f7057-125">Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="f7057-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="f7057-126">Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="f7057-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f7057-127">Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f7057-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f7057-128">De plus, `serviceHostingEnvironment` est une section machinetoApplication qui peut être héritée.</span><span class="sxs-lookup"><span data-stu-id="f7057-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="f7057-129">Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f7057-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="f7057-130">L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="f7057-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f7057-131">Elle requiert des extensions dans relativeAddress, par exemple .svc, .xoml ou .xamlx.</span><span class="sxs-lookup"><span data-stu-id="f7057-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f7057-132">Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension.</span><span class="sxs-lookup"><span data-stu-id="f7057-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f7057-133">En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.</span><span class="sxs-lookup"><span data-stu-id="f7057-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7057-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7057-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
