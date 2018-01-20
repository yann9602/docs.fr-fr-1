---
title: '&lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dcce701d8c051381317173b37fd37b840bcfa89d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="5a2a7-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="5a2a7-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="5a2a7-103">Représente une collection de paramètres utilisés globalement dans plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="5a2a7-104">Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="5a2a7-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a2a7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a2a7-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5a2a7-106">\<behaviors></span></span>  
<span data-ttu-id="5a2a7-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5a2a7-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="5a2a7-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5a2a7-108">\<behavior></span></span>  
<span data-ttu-id="5a2a7-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="5a2a7-109">\<workflowRuntime></span></span>  
<span data-ttu-id="5a2a7-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="5a2a7-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a2a7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a2a7-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a2a7-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5a2a7-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5a2a7-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a2a7-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="5a2a7-114">Attributes</span></span>  
 <span data-ttu-id="5a2a7-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a2a7-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5a2a7-116">Child Elements</span></span>  
  
|<span data-ttu-id="5a2a7-117">Élément</span><span class="sxs-lookup"><span data-stu-id="5a2a7-117">Element</span></span>|<span data-ttu-id="5a2a7-118">Description</span><span class="sxs-lookup"><span data-stu-id="5a2a7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a2a7-119">\<add></span><span class="sxs-lookup"><span data-stu-id="5a2a7-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="5a2a7-120">Ajoute à la collection une paire nom-valeur de paramètres communs utilisés par les services.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a2a7-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5a2a7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5a2a7-122">Élément</span><span class="sxs-lookup"><span data-stu-id="5a2a7-122">Element</span></span>|<span data-ttu-id="5a2a7-123">Description</span><span class="sxs-lookup"><span data-stu-id="5a2a7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a2a7-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="5a2a7-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="5a2a7-125">Spécifie les paramètres correspondant à une instance de <xref:System.Workflow.Runtime.WorkflowRuntime> pour héberger des services [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] basés sur le workflow.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a2a7-126">Notes</span><span class="sxs-lookup"><span data-stu-id="5a2a7-126">Remarks</span></span>  
 <span data-ttu-id="5a2a7-127">L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a2a7-128">Le service de suivi SQL n'utilise pas toujours la valeur `ConnectionString` si elle est spécifiée dans la section `<commonParameters>`.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="5a2a7-129">En effet, certaines de ses opérations, comme la récupération de la propriété `StateMachineWorkflowInstance.StateHistory`, peuvent échouer.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="5a2a7-130">Pour résoudre ce problème, spécifiez l'attribut `ConnectionString` dans la section de configuration pour le fournisseur de suivi, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="5a2a7-131">Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5a2a7-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="5a2a7-132">Notez que la `EnableRetries` paramètre peut être défini à un niveau global (comme indiqué dans le *Paramètres_courants* section) ou pour des services individuels qui prennent en charge `EnableRetries` (comme indiqué dans le *Services*section).</span><span class="sxs-lookup"><span data-stu-id="5a2a7-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="5a2a7-133">L'exemple de code suivant indique comment modifier les paramètres communs par programme.</span><span class="sxs-lookup"><span data-stu-id="5a2a7-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="5a2a7-134">Pour plus d’informations sur l’utilisation d’un fichier de configuration pour contrôler le comportement d’un <xref:System.Workflow.Runtime.WorkflowRuntime> objet d’une application hôte Windows Workflow Foundation, consultez [les fichiers de Configuration de flux de travail](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="5a2a7-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a2a7-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="5a2a7-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a2a7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a2a7-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="5a2a7-137">Fichiers de Configuration de flux de travail</span><span class="sxs-lookup"><span data-stu-id="5a2a7-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="5a2a7-138">\<add></span><span class="sxs-lookup"><span data-stu-id="5a2a7-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
