---
title: '&lt;add&gt; de &lt;services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7e58638ba4a964a1780606e2f75c0fd453638eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="413ce-102">&lt;add&gt; de &lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="413ce-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="413ce-103">Spécifie les paramètres correspondant à une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour héberger des services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] basés sur le workflow.</span><span class="sxs-lookup"><span data-stu-id="413ce-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="413ce-104">Cet élément est de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="413ce-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="413ce-105">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="413ce-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="413ce-106">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="413ce-106">\<behaviors></span></span>  
<span data-ttu-id="413ce-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="413ce-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="413ce-108">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="413ce-108">\<behavior></span></span>  
<span data-ttu-id="413ce-109">\<Services ></span><span class="sxs-lookup"><span data-stu-id="413ce-109">\<services></span></span>  
<span data-ttu-id="413ce-110">\<add></span><span class="sxs-lookup"><span data-stu-id="413ce-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413ce-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413ce-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="413ce-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="413ce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="413ce-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="413ce-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="413ce-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="413ce-114">Attributes</span></span>  
  
|<span data-ttu-id="413ce-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="413ce-115">Attribute</span></span>|<span data-ttu-id="413ce-116">Description</span><span class="sxs-lookup"><span data-stu-id="413ce-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="413ce-117">type</span><span class="sxs-lookup"><span data-stu-id="413ce-117">type</span></span>|<span data-ttu-id="413ce-118">Chaîne indiquant le nom qualifié du type d'assembly correspondant au service à initialiser.</span><span class="sxs-lookup"><span data-stu-id="413ce-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="413ce-119">Les services spécifiés doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="413ce-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="413ce-120">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="413ce-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="413ce-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="413ce-121">Child Elements</span></span>  
 <span data-ttu-id="413ce-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="413ce-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="413ce-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="413ce-123">Parent Elements</span></span>  
  
|<span data-ttu-id="413ce-124">Élément</span><span class="sxs-lookup"><span data-stu-id="413ce-124">Element</span></span>|<span data-ttu-id="413ce-125">Description</span><span class="sxs-lookup"><span data-stu-id="413ce-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="413ce-126">\<Services ></span><span class="sxs-lookup"><span data-stu-id="413ce-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="413ce-127">Collection de services qui sera ajoutée au moteur de <xref:System.Workflow.Runtime.WorkflowRuntime>.</span><span class="sxs-lookup"><span data-stu-id="413ce-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="413ce-128">Les éléments sont de type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="413ce-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="413ce-129">Les services spécifiés dans la collection sont initialisés par le moteur d'exécution de workflow et ajoutés à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="413ce-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="413ce-130">Par conséquent, les services spécifiés dans la collection doivent suivre certaines règles en ce qui concerne les signatures de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="413ce-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="413ce-131">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="413ce-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="413ce-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="413ce-132">Remarks</span></span>  
 <span data-ttu-id="413ce-133">Le service spécifié dans cet élément est initialisé par le moteur d'exécution de workflow et ajouté à ses services lorsque le constructeur <xref:System.Workflow.Runtime.WorkflowRuntime> approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="413ce-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="413ce-134">Par conséquent, le service spécifié doit suivre certaines règles en ce qui concerne les signatures de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="413ce-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="413ce-135">Pour plus d'informations, voir <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="413ce-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="413ce-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="413ce-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="413ce-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="413ce-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="413ce-138">Fichiers de Configuration de flux de travail</span><span class="sxs-lookup"><span data-stu-id="413ce-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
