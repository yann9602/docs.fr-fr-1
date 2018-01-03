---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc5d5cc77fcb227efd36106f1f8cb31efad24cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="7265c-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="7265c-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="7265c-103">Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.</span><span class="sxs-lookup"><span data-stu-id="7265c-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="7265c-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7265c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7265c-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="7265c-105">\<behaviors></span></span>  
<span data-ttu-id="7265c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7265c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7265c-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="7265c-107">\<behavior></span></span>  
<span data-ttu-id="7265c-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="7265c-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7265c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7265c-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7265c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7265c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7265c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7265c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7265c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="7265c-112">Attributes</span></span>  
  
|<span data-ttu-id="7265c-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="7265c-113">Attribute</span></span>|<span data-ttu-id="7265c-114">Description</span><span class="sxs-lookup"><span data-stu-id="7265c-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="7265c-115">Entier qui spécifie le nombre maximal d'opérations de réception qui peuvent être regroupées dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="7265c-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="7265c-116">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="7265c-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7265c-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7265c-117">Child Elements</span></span>  
 <span data-ttu-id="7265c-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7265c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7265c-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7265c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7265c-120">Élément</span><span class="sxs-lookup"><span data-stu-id="7265c-120">Element</span></span>|<span data-ttu-id="7265c-121">Description</span><span class="sxs-lookup"><span data-stu-id="7265c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7265c-122">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="7265c-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7265c-123">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7265c-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7265c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="7265c-124">Remarks</span></span>  
 <span data-ttu-id="7265c-125">Un transport configuré avec le traitement par lots de la transaction fait des tentatives de traitement par lot de plusieurs opérations de réception en une transaction.</span><span class="sxs-lookup"><span data-stu-id="7265c-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="7265c-126">Ainsi, le coût relativement élevé de la création d’une transaction et de sa validation dans chaque opération de réception est évité.</span><span class="sxs-lookup"><span data-stu-id="7265c-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7265c-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="7265c-127">Example</span></span>  
 <span data-ttu-id="7265c-128">L'exemple suivant explique comment ajouter le comportement de traitement par lot avec transaction à un service dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7265c-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
        </baseAddresses>  
      </host>  
  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />  
  
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="endpointBehavior">  
        <transactedBatching maxBatchSize="10" />  
      </behavior>  
    </endpointBehaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7265c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7265c-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
