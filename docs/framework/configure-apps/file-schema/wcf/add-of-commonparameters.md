---
title: "&lt;add&gt; de &lt;commonParameters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;add&gt; de &lt;commonParameters&gt;
Spécifie une paire nom\-valeur de paramètres utilisés globalement dans plusieurs services.  Ce paramètre inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.  
  
## Syntaxe  
  
```  
  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|name|Nom du paramètre spécifié pour un service.|  
|par défaut|Valeur du paramètre spécifié pour un service.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<commonParameters\>](http://msdn.microsoft.com/fr-fr/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|Collection de paramètres communs utilisée par les services.  Cette collection inclut généralement la chaîne de connexion de base de données pouvant être partagée par les services fiables.|  
  
## Notes  
 L'élément `<commonParameters>` définit tous les paramètres utilisés globalement dans plusieurs services, par exemple `ConnectionString` lors de l'utilisation de <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
 Pour les services qui valident des lots de travail dans des magasins de persistance, comme <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> et <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, vous pouvez les activer pour effectuer de nouvelles tentatives de transaction à l'aide du paramètre `EnableRetries` tel qu'indiqué dans l'exemple suivant :  
  
```  
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
  
 Notez que le paramètre `EnableRetries` peut être défini pour un niveau global \(tel qu'indiqué dans la section *CommonParameters*\) ou pour des services individuels qui prennent en charge `EnableRetries` \(tel qu'indiqué dans la section *Services*\).  
  
 Pour plus d'informations sur l'utilisation d'un fichier de configuration pour contrôler le comportement d'un objet <xref:System.Workflow.Runtime.WorkflowRuntime> d'une application hôte Windows Workflow Foundation, consultez [Workflow Configuration Files](http://msdn.microsoft.com/fr-fr/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
## Exemple  
  
```  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>   
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>   
 <xref:System.Workflow.Runtime.WorkflowRuntime>   
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>   
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>   
 [Workflow Configuration Files](http://msdn.microsoft.com/fr-fr/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)   
 [\<commonParameters\>](http://msdn.microsoft.com/fr-fr/d0e1e6fc-985a-4713-b7da-194e30dfab4c)