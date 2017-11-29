---
title: "Stocker l'extensibilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f6700fe67d151e78c8b216d93a4cd7098ed6401d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="store-extensibility"></a><span data-ttu-id="c4983-102">Stocker l'extensibilité</span><span class="sxs-lookup"><span data-stu-id="c4983-102">Store Extensibility</span></span>
<span data-ttu-id="c4983-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> permet aux utilisateurs de promouvoir des propriétés personnalisées spécifiques à l'application qui peuvent être utilisées pour rechercher des instances dans la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="c4983-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> allows users to promote custom, application-specific properties that can be used to query for instances in the persistence database.</span></span> <span data-ttu-id="c4983-104">L'acte de promouvoir une propriété entraîne la disponibilité de la valeur dans une vue spéciale de la base de données.</span><span class="sxs-lookup"><span data-stu-id="c4983-104">The act of promoting a property causes the value to be available within a special view in the database.</span></span> <span data-ttu-id="c4983-105">Ces propriétés promues (propriétés qui peuvent être utilisées dans des requêtes utilisateur) peuvent être de types simples tel qu'Int64, Guid, String et DateTime ou d'un type binaire sérialisé (byte[]).</span><span class="sxs-lookup"><span data-stu-id="c4983-105">These promoted properties (properties that can be used in user queries) can be of simple types such as Int64, Guid, String, and DateTime or of a serialized binary type (byte[]).</span></span>  
  
 <span data-ttu-id="c4983-106">La classe <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a la méthode <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> que vous pouvez utiliser pour encourager une propriété comme une propriété qui peut être utilisée dans les requêtes.</span><span class="sxs-lookup"><span data-stu-id="c4983-106">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class has the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> method that you can use to promote a property as a property that can be used in queries.</span></span> <span data-ttu-id="c4983-107">L'exemple suivant est un exemple de bout en bout d'extensibilité de magasin.</span><span class="sxs-lookup"><span data-stu-id="c4983-107">The following example is an end-to-end example of store extensibility.</span></span>  
  
1.  <span data-ttu-id="c4983-108">Dans ce scénario d'exemple, une application du traitement (DP) du document a des workflows, qui chacun utilise des activités personnalisées pour le traitement de document.</span><span class="sxs-lookup"><span data-stu-id="c4983-108">In this example scenario, a document processing (DP) application has workflows, each of which uses custom activities for document processing.</span></span> <span data-ttu-id="c4983-109">Ces workflows ont un ensemble de variables d'état qui doivent être rendues visibles à l'utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="c4983-109">These workflows have a set of state variables that need to be made visible to the end user.</span></span> <span data-ttu-id="c4983-110">Pour cela, l'application de DP fournit une extension d'instance de type <xref:System.Activities.Persistence.PersistenceParticipant>, utilisée par les activités pour fournir les variables d'état.</span><span class="sxs-lookup"><span data-stu-id="c4983-110">To achieve this, the DP application provides an instance extension of type <xref:System.Activities.Persistence.PersistenceParticipant>, which is used by activities to supply the state variables.</span></span>  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  <span data-ttu-id="c4983-111">La nouvelle extension est ensuite ajoutée à l’hôte.</span><span class="sxs-lookup"><span data-stu-id="c4983-111">The new extension is then added to the host.</span></span>  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     <span data-ttu-id="c4983-112">Pour plus d’informations sur l’ajout d’un participant de persistance personnalisé, consultez la [Participants de persistance](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="c4983-112">For more details about adding a custom persistence participant, see the [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) sample.</span></span>  
  
3.  <span data-ttu-id="c4983-113">Les activités personnalisées dans l’application de DP remplissent différents champs d’état dans le **Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="c4983-113">The custom activities in the DP application populate various status fields in the **Execute** method.</span></span>  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  <span data-ttu-id="c4983-114">Lorsqu’une instance de workflow atteint un point de persistance, le **CollectValues** méthode de la **DocumentStatusExtension** participant de persistance enregistre ces propriétés dans les données de persistance collection.</span><span class="sxs-lookup"><span data-stu-id="c4983-114">When a workflow instance reaches a persistence point, the **CollectValues** method of the **DocumentStatusExtension** persistence participant saves these properties into the persistence data collection.</span></span>  
  
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
    >  <span data-ttu-id="c4983-115">Toutes ces propriétés sont transmises à **SqlWorkflowInstanceStore** par l’infrastructure de persistance via la **SaveWorkflowCommand.InstanceData** collection.</span><span class="sxs-lookup"><span data-stu-id="c4983-115">All these properties are passed to **SqlWorkflowInstanceStore** by the persistence framework through the **SaveWorkflowCommand.InstanceData** collection.</span></span>  
  
5.  <span data-ttu-id="c4983-116">L’application de DP initialise le magasin d’instances de Workflow SQL et appelle le **promouvoir** méthode pour promouvoir ces données.</span><span class="sxs-lookup"><span data-stu-id="c4983-116">The DP application initializes the SQL Workflow Instance Store and invokes the **Promote** method to promote this data.</span></span>  
  
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
  
     <span data-ttu-id="c4983-117">En fonction de ces informations de promotion, **SqlWorkflowInstanceStore** place les propriétés de données dans les colonnes de la [InstancePromotedProperties](#InstancePromotedProperties) vue.</span><span class="sxs-lookup"><span data-stu-id="c4983-117">Based on this promotion information, **SqlWorkflowInstanceStore** places the data properties in the columns of the [InstancePromotedProperties](#InstancePromotedProperties) view.</span></span>
  
6.  <span data-ttu-id="c4983-118">Pour interroger un sous-ensemble des données de la table de promotions, l'application de DP ajoute une vue personnalisée au-dessus de la vue de promotions.</span><span class="sxs-lookup"><span data-stu-id="c4983-118">To query a subset of the data from the promotion table, the DP application adds a customized view on top of the promotion view.</span></span>  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <span data-ttu-id="c4983-119"><a name="InstancePromotedProperties"></a>Vue [System.Activities.DurableInstancing.InstancePromotedProperties]</span><span class="sxs-lookup"><span data-stu-id="c4983-119"><a name="InstancePromotedProperties"></a> [System.Activities.DurableInstancing.InstancePromotedProperties] view</span></span>  
  
|<span data-ttu-id="c4983-120">Nom de la colonne</span><span class="sxs-lookup"><span data-stu-id="c4983-120">Column Name</span></span>|<span data-ttu-id="c4983-121">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="c4983-121">Column Type</span></span>|<span data-ttu-id="c4983-122">Description</span><span class="sxs-lookup"><span data-stu-id="c4983-122">Description</span></span>|  
|-----------------|-----------------|-----------------|  
|<span data-ttu-id="c4983-123">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c4983-123">InstanceId</span></span>|<span data-ttu-id="c4983-124">GUID</span><span class="sxs-lookup"><span data-stu-id="c4983-124">GUID</span></span>|<span data-ttu-id="c4983-125">Instance de workflow à laquelle cette promotion appartient.</span><span class="sxs-lookup"><span data-stu-id="c4983-125">The workflow instance that this promotion belongs to.</span></span>|  
|<span data-ttu-id="c4983-126">PromotionName</span><span class="sxs-lookup"><span data-stu-id="c4983-126">PromotionName</span></span>|<span data-ttu-id="c4983-127">nvarchar(400)</span><span class="sxs-lookup"><span data-stu-id="c4983-127">nvarchar(400)</span></span>|<span data-ttu-id="c4983-128">Nom de la promotion elle-même.</span><span class="sxs-lookup"><span data-stu-id="c4983-128">The name of the promotion itself.</span></span>|  
|<span data-ttu-id="c4983-129">Value1, Value2, Value3,.., Value32</span><span class="sxs-lookup"><span data-stu-id="c4983-129">Value1, Value2, Value3,..,Value32</span></span>|<span data-ttu-id="c4983-130">sql_variant</span><span class="sxs-lookup"><span data-stu-id="c4983-130">sql_variant</span></span>|<span data-ttu-id="c4983-131">Valeur de la propriété encouragée elle-même.</span><span class="sxs-lookup"><span data-stu-id="c4983-131">The value of the promoted property itself.</span></span> <span data-ttu-id="c4983-132">La plupart des types de données primitifs SQL, à l'exception des objets BLOB binaires et les chaînes dont la longueur dépasse 8 000 octets peuvent tenir dans sql_variant.</span><span class="sxs-lookup"><span data-stu-id="c4983-132">Most SQL primitive data types except binary blobs and strings over 8000 bytes in length can fit in sql_variant.</span></span>|  
|<span data-ttu-id="c4983-133">Value33, Value34, Value35, …, Value64</span><span class="sxs-lookup"><span data-stu-id="c4983-133">Value33, Value34, Value35, …, Value64</span></span>|<span data-ttu-id="c4983-134">varbinary(max)</span><span class="sxs-lookup"><span data-stu-id="c4983-134">varbinary(max)</span></span>|<span data-ttu-id="c4983-135">Valeur de propriétés promues déclarées explicitement en tant que varbinary(max).</span><span class="sxs-lookup"><span data-stu-id="c4983-135">The value of promoted properties that are explicitly declared as varbinary(max).</span></span>|
