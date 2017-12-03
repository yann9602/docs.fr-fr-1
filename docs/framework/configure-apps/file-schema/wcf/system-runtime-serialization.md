---
title: '&lt;System.Runtime.Serialization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a6eb2b152f2ab11bbe0e08ff1ad22f94d45057e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="5a24f-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="5a24f-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="5a24f-103">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a24f-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="5a24f-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="5a24f-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a24f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a24f-105">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer">  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
             <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a24f-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a24f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5a24f-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a24f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a24f-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a24f-108">Attributes</span></span>  
 <span data-ttu-id="5a24f-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="5a24f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a24f-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a24f-110">Child Elements</span></span>  
  
|<span data-ttu-id="5a24f-111">Élément</span><span class="sxs-lookup"><span data-stu-id="5a24f-111">Element</span></span>|<span data-ttu-id="5a24f-112">Description</span><span class="sxs-lookup"><span data-stu-id="5a24f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a24f-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5a24f-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="5a24f-114">Active l’ajout de types connus à utiliser lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="5a24f-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a24f-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a24f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5a24f-116">Élément</span><span class="sxs-lookup"><span data-stu-id="5a24f-116">Element</span></span>|<span data-ttu-id="5a24f-117">Description</span><span class="sxs-lookup"><span data-stu-id="5a24f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a24f-118">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="5a24f-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="5a24f-119">Élément de niveau supérieur de la configuration.</span><span class="sxs-lookup"><span data-stu-id="5a24f-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a24f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a24f-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="5a24f-121">À l’aide de contrats de données</span><span class="sxs-lookup"><span data-stu-id="5a24f-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="5a24f-122">Types connus de contrat de données</span><span class="sxs-lookup"><span data-stu-id="5a24f-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
