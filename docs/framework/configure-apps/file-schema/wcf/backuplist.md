---
title: '&lt;backupList&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00a4c84ee5c9a833cc789c8871df79a3886fa0e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbackuplistgt"></a><span data-ttu-id="6a0f7-102">&lt;backupList&gt;</span><span class="sxs-lookup"><span data-stu-id="6a0f7-102">&lt;backupList&gt;</span></span>
<span data-ttu-id="6a0f7-103">Représente une section de configuration pour définir une liste de sauvegarde qui énumère un ensemble de points de terminaison que vous souhaitez que le Service de routage à utiliser au cas où le point de terminaison principal ne peut pas être atteint.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-103">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="6a0f7-104">Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="6a0f7-105">Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="6a0f7-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6a0f7-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6a0f7-107">\<routage ></span><span class="sxs-lookup"><span data-stu-id="6a0f7-107">\<routing></span></span>  
<span data-ttu-id="6a0f7-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="6a0f7-108">\<backupLists></span></span>  
<span data-ttu-id="6a0f7-109">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="6a0f7-109">\<backupList></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a0f7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a0f7-110">Syntax</span></span>  
  
```xml 
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a0f7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6a0f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6a0f7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a0f7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="6a0f7-113">Attributes</span></span>  
  
|<span data-ttu-id="6a0f7-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a0f7-114">Attribute</span></span>|<span data-ttu-id="6a0f7-115">Description</span><span class="sxs-lookup"><span data-stu-id="6a0f7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a0f7-116">name</span><span class="sxs-lookup"><span data-stu-id="6a0f7-116">name</span></span>|<span data-ttu-id="6a0f7-117">Chaîne qui spécifie le nom permettant d'identifier la liste de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a0f7-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6a0f7-118">Child Elements</span></span>  
  
|<span data-ttu-id="6a0f7-119">Élément</span><span class="sxs-lookup"><span data-stu-id="6a0f7-119">Element</span></span>|<span data-ttu-id="6a0f7-120">Description</span><span class="sxs-lookup"><span data-stu-id="6a0f7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a0f7-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="6a0f7-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="6a0f7-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6a0f7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6a0f7-123">Élément</span><span class="sxs-lookup"><span data-stu-id="6a0f7-123">Element</span></span>|<span data-ttu-id="6a0f7-124">Description</span><span class="sxs-lookup"><span data-stu-id="6a0f7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a0f7-125">\<routage ></span><span class="sxs-lookup"><span data-stu-id="6a0f7-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="6a0f7-126">Liste de points de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a0f7-127">Notes</span><span class="sxs-lookup"><span data-stu-id="6a0f7-127">Remarks</span></span>  
 <span data-ttu-id="6a0f7-128">Cette section contient une collection ordonnée de points de terminaison auxquels un message sera transmis si une exception de communication se produit lors de l’envoi au point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="6a0f7-129">Si un envoi au point de terminaison principal est répertorié dans le `endpointName` attribut de [ \<Ajouter >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) échoue avec une exception de communication, le Service de routage essaiera d’envoyer le message au premier point de terminaison dans ce section de configuration.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="6a0f7-130">Si l’opération échoue également avec une exception de communication, le service de routage essaie d’envoyer le message au point de terminaison suivant contenu dans cette section jusqu’à ce que la tentative d’envoi aboutisse, retourne une erreur autre qu’une exception de communication, ou que tous les points de terminaison de la collection retournent une erreur.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="6a0f7-131">Dans l’exemple suivant, si un envoi au point de terminaison primaire appelé « Destination » retourne une exception de communication, le service essaiera d’envoyer le message à « alternateServiceQueue ».</span><span class="sxs-lookup"><span data-stu-id="6a0f7-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="6a0f7-132">Si cette tentative retourne également une exception de communication, le service de routage essaiera d’envoyer le message au point de terminaison suivant dans la collection.</span><span class="sxs-lookup"><span data-stu-id="6a0f7-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a0f7-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a0f7-133">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
