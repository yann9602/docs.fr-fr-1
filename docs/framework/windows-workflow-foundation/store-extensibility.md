---
title: "Stocker l&#39;extensibilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Stocker l&#39;extensibilit&#233;
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> permet aux utilisateurs de promouvoir des propriétés personnalisées spécifiques à l'application qui peuvent être utilisées pour rechercher des instances dans la base de données de persistance.L'acte de promouvoir une propriété entraîne la disponibilité de la valeur dans une vue spéciale de la base de données.Ces propriétés promues \(propriétés qui peuvent être utilisées dans des requêtes utilisateur\) peuvent être de types simples tel qu'Int64, Guid, String et DateTime ou d'un type binaire sérialisé \(byte\[\]\).  
  
 La classe <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a la méthode <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> que vous pouvez utiliser pour encourager une propriété comme une propriété qui peut être utilisée dans les requêtes.L'exemple suivant est un exemple de bout en bout d'extensibilité de magasin.  
  
1.  Dans ce scénario d'exemple, une application du traitement \(DP\) du document a des workflows, qui chacun utilise des activités personnalisées pour le traitement de document.Ces workflows ont un ensemble de variables d'état qui doivent être rendues visibles à l'utilisateur final.Pour cela, l'application de DP fournit une extension d'instance de type <xref:System.Activities.Persistence.PersistenceParticipant>, utilisée par les activités pour fournir les variables d'état.  
  
    ```  
  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
  
    ```  
  
2.  La nouvelle extension est ensuite ajoutée à l'hôte.  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
  
    ```  
  
     Pour plus d'informations sur l'ajout d'un participant de persistance personnalisé, consultez l'exemple [Participants de persistance](../../../docs/framework/windows-workflow-foundation//persistence-participants.md).  
  
3.  Les activités personnalisées dans l'application de DP remplissent différents champs d'état dans la méthode **Execute**.  
  
    ```  
  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = “Approved”;  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
  
    ```  
  
4.  Lorsqu'une instance de workflow atteint un point de persistance, la méthode **CollectValues** du participant de persistance **DocumentStatusExtension** enregistre ces propriétés dans la collection de données de persistance.  
  
    ```  
  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
  
    ```  
  
    > [!NOTE]
    >  Toutes ces propriétés sont transmises à **SqlWorkflowInstanceStore** par l'infrastructure de persistance via la collection **SaveWorkflowCommand.InstanceData**.  
  
5.  L'application de DP initialise le magasin d'instances de workflow SQL et appelle la méthode **Promote** pour promouvoir ces données.  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     En fonction de ces informations de promotion, **SqlWorkflowInstanceStore** place les propriétés de données dans les colonnes de la [Vue [System.Activities.DurableInstancing.InstancePromotedProperties]](../../../docs/framework/windows-workflow-foundation//store-extensibility.md#InstancePromotedProperties).  
  
6.  Pour interroger un sous\-ensemble des données de la table de promotions, l'application de DP ajoute une vue personnalisée au\-dessus de la vue de promotions.  
  
    ```  
  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
  
    ```  
  
##  <a name="InstancePromotedProperties"></a> Vue \[System.Activities.DurableInstancing.InstancePromotedProperties\]  
  
|Nom de la colonne|Type de colonne|Description|  
|-----------------------|---------------------|-----------------|  
|InstanceId|GUID|Instance de workflow à laquelle cette promotion appartient.|  
|PromotionName|nvarchar\(400\)|Nom de la promotion elle\-même.|  
|Value1, Value2, Value3,.., Value32|sql\_variant|Valeur de la propriété encouragée elle\-même.La plupart des types de données primitifs SQL, à l'exception des objets BLOB binaires et les chaînes dont la longueur dépasse 8 000 octets peuvent tenir dans sql\_variant.|  
|Value33, Value34, Value35, …, Value64|varbinary\(max\)|Valeur de propriétés promues déclarées explicitement en tant que varbinary\(max\).|