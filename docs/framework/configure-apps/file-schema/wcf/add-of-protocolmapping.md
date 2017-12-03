---
title: '&lt;add&gt; de &lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a><span data-ttu-id="a344c-102">&lt;add&gt; de &lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="a344c-102">&lt;add&gt; of &lt;protocolMapping&gt;</span></span>
<span data-ttu-id="a344c-103">Représente un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et un [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] liaison.</span><span class="sxs-lookup"><span data-stu-id="a344c-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span> <span data-ttu-id="a344c-104">Lors de la création de points de terminaison par défaut au moment de l'exécution, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] examine les mappages configurés et sélectionne une liaison à utiliser en tant qu'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="a344c-104">When creating default endpoints at runtime, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="a344c-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a344c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a344c-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="a344c-106">\<protocolMapping></span></span>  
<span data-ttu-id="a344c-107">\<add></span><span class="sxs-lookup"><span data-stu-id="a344c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a344c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a344c-108">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a344c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a344c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a344c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a344c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a344c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a344c-111">Attributes</span></span>  
  
|<span data-ttu-id="a344c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="a344c-112">Element</span></span>|<span data-ttu-id="a344c-113">Description</span><span class="sxs-lookup"><span data-stu-id="a344c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a344c-114">liaison</span><span class="sxs-lookup"><span data-stu-id="a344c-114">binding</span></span>|<span data-ttu-id="a344c-115">Chaîne qui spécifie le type de liaison à utiliser pour un point de terminaison pendant la création de points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="a344c-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="a344c-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a344c-116">bindingConfiguration</span></span>|<span data-ttu-id="a344c-117">Chaîne qui spécifie le nom de la section de configuration de liaison à référencer.</span><span class="sxs-lookup"><span data-stu-id="a344c-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="a344c-118">scheme</span><span class="sxs-lookup"><span data-stu-id="a344c-118">scheme</span></span>|<span data-ttu-id="a344c-119">Schéma de protocole de transport à utiliser pour le point de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="a344c-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a344c-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a344c-120">Child Elements</span></span>  
 <span data-ttu-id="a344c-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a344c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a344c-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a344c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a344c-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a344c-123">Element</span></span>|<span data-ttu-id="a344c-124">Description</span><span class="sxs-lookup"><span data-stu-id="a344c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a344c-125">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="a344c-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="a344c-126">Représente une section de configuration pour définir les mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] liaisons.</span><span class="sxs-lookup"><span data-stu-id="a344c-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a344c-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="a344c-127">Example</span></span>  
 <span data-ttu-id="a344c-128">L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="a344c-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="a344c-129">Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="a344c-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="a344c-130">Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.</span><span class="sxs-lookup"><span data-stu-id="a344c-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a344c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a344c-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
