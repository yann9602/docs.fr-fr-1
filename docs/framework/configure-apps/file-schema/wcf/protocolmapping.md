---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 88eb76a5657bd4a83bebb32ce30f73d32693be9b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="52951-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="52951-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="52951-103">Représente une section de configuration pour définir un ensemble de mappage de protocole par défaut entre les schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="52951-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="52951-104">Lors de la création de points de terminaison par défaut au moment de l'exécution, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] examine les mappages configurés et sélectionne une liaison à utiliser en tant qu'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="52951-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="52951-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="52951-105">\<system.serviceModel></span></span>  
<span data-ttu-id="52951-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="52951-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52951-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52951-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52951-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="52951-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52951-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="52951-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52951-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="52951-110">Attributes</span></span>  
 <span data-ttu-id="52951-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="52951-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="52951-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52951-112">Child Elements</span></span>  
  
|<span data-ttu-id="52951-113">Élément</span><span class="sxs-lookup"><span data-stu-id="52951-113">Element</span></span>|<span data-ttu-id="52951-114">Description</span><span class="sxs-lookup"><span data-stu-id="52951-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52951-115">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="52951-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="52951-116">Contient un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et une liaison WCF.</span><span class="sxs-lookup"><span data-stu-id="52951-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52951-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52951-117">Parent Elements</span></span>  
  
|<span data-ttu-id="52951-118">Élément</span><span class="sxs-lookup"><span data-stu-id="52951-118">Element</span></span>|<span data-ttu-id="52951-119">Description</span><span class="sxs-lookup"><span data-stu-id="52951-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52951-120">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52951-120">system.ServiceModel</span></span>|<span data-ttu-id="52951-121">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="52951-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="52951-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="52951-122">Example</span></span>  
 <span data-ttu-id="52951-123">L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="52951-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="52951-124">Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="52951-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="52951-125">Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.</span><span class="sxs-lookup"><span data-stu-id="52951-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52951-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52951-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
