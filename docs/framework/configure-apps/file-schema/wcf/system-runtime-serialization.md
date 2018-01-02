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
ms.workload: dotnet
ms.openlocfilehash: ab66252ebc5b87c197b3e4ac7b6def9355e5f201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimeserializationgt"></a><span data-ttu-id="55d32-102">&lt;System.Runtime.Serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="55d32-102">&lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="55d32-103">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="55d32-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="55d32-104">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="55d32-104">system.runtime.serialization</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d32-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55d32-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55d32-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55d32-106">Attributes and Elements</span></span>  
 <span data-ttu-id="55d32-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55d32-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55d32-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="55d32-108">Attributes</span></span>  
 <span data-ttu-id="55d32-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55d32-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55d32-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55d32-110">Child Elements</span></span>  
  
|<span data-ttu-id="55d32-111">Élément</span><span class="sxs-lookup"><span data-stu-id="55d32-111">Element</span></span>|<span data-ttu-id="55d32-112">Description</span><span class="sxs-lookup"><span data-stu-id="55d32-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55d32-113">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="55d32-113">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="55d32-114">Active l’ajout de types connus à utiliser lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="55d32-114">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55d32-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55d32-115">Parent Elements</span></span>  
  
|<span data-ttu-id="55d32-116">Élément</span><span class="sxs-lookup"><span data-stu-id="55d32-116">Element</span></span>|<span data-ttu-id="55d32-117">Description</span><span class="sxs-lookup"><span data-stu-id="55d32-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55d32-118">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="55d32-118">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="55d32-119">Élément de niveau supérieur de la configuration.</span><span class="sxs-lookup"><span data-stu-id="55d32-119">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55d32-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55d32-120">See Also</span></span>  
 <xref:System.Runtime.Serialization>  
 [<span data-ttu-id="55d32-121">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="55d32-121">Using Data Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="55d32-122">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="55d32-122">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
