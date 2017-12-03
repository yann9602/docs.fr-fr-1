---
title: '&lt;add&gt; de &lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="f07e7-102">&lt;add&gt; de &lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="f07e7-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="f07e7-103">Élément de configuration qui vous permet de définir des paramètres d'activation de services virtuels mappés aux types de service [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f07e7-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="f07e7-104">Cela permet d'activer des services hébergés dans WAS/IIS sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="f07e7-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="f07e7-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f07e7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f07e7-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f07e7-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f07e7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f07e7-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f07e7-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f07e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f07e7-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f07e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f07e7-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f07e7-110">Attributes</span></span>  
  
|<span data-ttu-id="f07e7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f07e7-111">Attribute</span></span>|<span data-ttu-id="f07e7-112">Description</span><span class="sxs-lookup"><span data-stu-id="f07e7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f07e7-113">factory</span><span class="sxs-lookup"><span data-stu-id="f07e7-113">factory</span></span>|<span data-ttu-id="f07e7-114">Chaîne qui spécifie le nom de type CLR de la fabrique qui génère un élément d'activation de service.</span><span class="sxs-lookup"><span data-stu-id="f07e7-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="f07e7-115">service</span><span class="sxs-lookup"><span data-stu-id="f07e7-115">service</span></span>|<span data-ttu-id="f07e7-116">Le ServiceType qui implémente le service (Typename qualifié complet ou Typename court (s'il est placé dans le dossier App_Code).</span><span class="sxs-lookup"><span data-stu-id="f07e7-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="f07e7-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="f07e7-117">relativeAddress</span></span>|<span data-ttu-id="f07e7-118">L'adresse relative dans l'application IIS active (par exemple « Service.svc ».</span><span class="sxs-lookup"><span data-stu-id="f07e7-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="f07e7-119">Dans WCF 4.0 cette adresse relative doit contenir une des extensions de fichiers connues (.svc, .xamlx,…). Aucun fichier physique ne doit exister pour relativeUrl.</span><span class="sxs-lookup"><span data-stu-id="f07e7-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f07e7-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f07e7-120">Child Elements</span></span>  
 <span data-ttu-id="f07e7-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f07e7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f07e7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f07e7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f07e7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="f07e7-123">Element</span></span>|<span data-ttu-id="f07e7-124">Description</span><span class="sxs-lookup"><span data-stu-id="f07e7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f07e7-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f07e7-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="f07e7-126">Section de configuration qui décrit les paramètres d'activation.</span><span class="sxs-lookup"><span data-stu-id="f07e7-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f07e7-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="f07e7-127">Remarks</span></span>  
 <span data-ttu-id="f07e7-128">L'exemple suivant indique comment configurer des paramètres d'activation dans le fichier web.config.</span><span class="sxs-lookup"><span data-stu-id="f07e7-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="f07e7-129">Cette configuration vous permet d'activer GreetingService sans utiliser de fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="f07e7-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="f07e7-130">Notez que `<serviceHostingEnvironment>` est une configuration au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="f07e7-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f07e7-131">Vous devez placer le `web.config` qui contient la configuration sous la racine de l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f07e7-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f07e7-132">De plus, `serviceHostingEnvironment` est une section machinetoApplication qui peut être héritée.</span><span class="sxs-lookup"><span data-stu-id="f07e7-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="f07e7-133">Si vous inscrivez un seul service à la racine de l'ordinateur, chaque service dans l'application hérite de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="f07e7-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="f07e7-134">L'activation basée sur la configuration prend en charge l'activation via un protocole HTTP ou non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="f07e7-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f07e7-135">Elle requiert des extensions dans relativeAddress, par exemple .svc, .xoml ou .xamlx.</span><span class="sxs-lookup"><span data-stu-id="f07e7-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f07e7-136">Vous pouvez mapper vos propres extensions au buildProviders connu, qui vous permet ensuite d’activer le service sur n’importe quelle extension.</span><span class="sxs-lookup"><span data-stu-id="f07e7-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f07e7-137">En cas de conflit, la section `<serviceActivations>` remplace les inscriptions .svc.</span><span class="sxs-lookup"><span data-stu-id="f07e7-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f07e7-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f07e7-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
