---
title: "Mise à jour dynamique"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d8aff19cc087cf4aea2befb7a39533422aeabd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-update"></a><span data-ttu-id="4b64d-102">Mise à jour dynamique</span><span class="sxs-lookup"><span data-stu-id="4b64d-102">Dynamic Update</span></span>
<span data-ttu-id="4b64d-103">La mise à jour dynamique fournit un mécanisme pour permettre aux développeurs d'applications de workflow de mettre à jour la définition de workflow d'une instance de workflow persistante.</span><span class="sxs-lookup"><span data-stu-id="4b64d-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="4b64d-104">Il peut s'agir d'une résolution de bogue, de nouvelles spécifications ou de l'adaptation à des modifications inattendues.</span><span class="sxs-lookup"><span data-stu-id="4b64d-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="4b64d-105">Cette rubrique fournit une vue d'ensemble de la fonctionnalité de mise à jour dynamique introduite dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b64d-105">This topic provides an overview of the dynamic update functionality introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="dynamic-update"></a><span data-ttu-id="4b64d-106">Mise à jour dynamique</span><span class="sxs-lookup"><span data-stu-id="4b64d-106">Dynamic Update</span></span>  
 <span data-ttu-id="4b64d-107">Pour appliquer les mises à jour dynamiques à une instance de workflow persistante, un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui contient les instructions du runtime qui décrivent comment modifier l'instance persistante de workflow est créé pour refléter les modifications souhaitées.</span><span class="sxs-lookup"><span data-stu-id="4b64d-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="4b64d-108">Une fois la mise à jour de la carte créée, elle est appliquée aux instances de workflow persistantes souhaitées.</span><span class="sxs-lookup"><span data-stu-id="4b64d-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="4b64d-109">Une fois la mise à jour dynamique appliquée, l'instance de workflow peut reprendre à l'aide de la nouvelle définition de workflow mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b64d-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="4b64d-110">Quatre étapes sont requises pour créer et appliquer la mise à jour d'une carte.</span><span class="sxs-lookup"><span data-stu-id="4b64d-110">There are four steps required to create and apply an update map.</span></span>  
  
1.  [<span data-ttu-id="4b64d-111">Préparer la définition de flux de travail pour la mise à jour dynamique</span><span class="sxs-lookup"><span data-stu-id="4b64d-111">Prepare the workflow definition for dynamic update</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Prepare)  
  
2.  [<span data-ttu-id="4b64d-112">Mettre à jour la définition de flux de travail pour refléter les modifications souhaitées</span><span class="sxs-lookup"><span data-stu-id="4b64d-112">Update the workflow definition to reflect the desired changes</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Update)  
  
3.  [<span data-ttu-id="4b64d-113">Créer le mappage de mise à jour</span><span class="sxs-lookup"><span data-stu-id="4b64d-113">Create the update map</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Create)  
  
4.  [<span data-ttu-id="4b64d-114">Appliquer la mise à jour de la carte pour les instances de workflow persistantes souhaitées</span><span class="sxs-lookup"><span data-stu-id="4b64d-114">Apply the update map to the desired persisted workflow instances</span></span>](../../../docs/framework/windows-workflow-foundation/dynamic-update.md#Apply)  
  
> [!NOTE]
>  <span data-ttu-id="4b64d-115">Notez que les étapes 1 à 3, qui couvrent la conception de la mise à jour de la carte, peuvent être effectuées indépendamment de la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b64d-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="4b64d-116">Un scénario courant consiste pour le développeur de workflow à créer la carte de mise à jour hors connexion, puis pour un administrateur à appliquer la mise à jour ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4b64d-116">A common scenario that that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>  
  
 <span data-ttu-id="4b64d-117">Cette rubrique fournit une vue d'ensemble du processus de mise à jour dynamique pour ajouter une nouvelle activité à une instance persistante d'un workflow XAML compilé.</span><span class="sxs-lookup"><span data-stu-id="4b64d-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>  
  
###  <span data-ttu-id="4b64d-118"><a name="Prepare"></a>Préparer la définition de flux de travail pour la mise à jour dynamique</span><span class="sxs-lookup"><span data-stu-id="4b64d-118"><a name="Prepare"></a> Prepare the workflow definition for dynamic update</span></span>  
 <span data-ttu-id="4b64d-119">La première étape du processus de mise à jour dynamique consiste à développer la définition de workflow souhaitée pour la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="4b64d-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="4b64d-120">Pour ce faire, il suffit d'appeler la méthode <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> et de passer la définition de workflow à modifier.</span><span class="sxs-lookup"><span data-stu-id="4b64d-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="4b64d-121">Cette méthode valide et parcourt l'arborescence de workflow pour identifier tous les objets, tels que les activités et les variables publiques qui doivent être référencées de sorte qu'elles puissent être comparées ultérieurement à la définition modifiée de workflow.</span><span class="sxs-lookup"><span data-stu-id="4b64d-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="4b64d-122">Une fois cette opération terminée, l'arborescence de workflow est clonée et attachée à la définition de workflow d'origine.</span><span class="sxs-lookup"><span data-stu-id="4b64d-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="4b64d-123">Lorsque la mise à jour de la carte est créée, la version mise à jour de la définition du workflow est comparée à la définition de workflow d'origine et la mise à jour de la carte est générée selon les différences.</span><span class="sxs-lookup"><span data-stu-id="4b64d-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>  
  
 <span data-ttu-id="4b64d-124">Pour préparer un workflow XAML pour la mise à jour dynamique, il peut être chargé dans un <xref:System.Activities.ActivityBuilder>, puis le <xref:System.Activities.ActivityBuilder> est passé dans <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b64d-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b64d-125">Pour plus d’informations sur l’utilisation des workflows sérialisés et <xref:System.Activities.ActivityBuilder>, consultez [sérialisation de Workflows et les activités vers et depuis XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="4b64d-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>  
  
 <span data-ttu-id="4b64d-126">Dans l'exemple suivant, une définition de `MortgageWorkflow` (composée de <xref:System.Activities.Statements.Sequence> avec plusieurs activités enfants) est chargée dans <xref:System.Activities.ActivityBuilder>, puis élaborée pour la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="4b64d-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="4b64d-127">Après le retour de la méthode, <xref:System.Activities.ActivityBuilder> contient la définition de workflow d'origine ainsi qu'une copie.</span><span class="sxs-lookup"><span data-stu-id="4b64d-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>  
  
```csharp  
// Load the MortgageWorkflow definition from Xaml into  
// an ActivityBuilder.  
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
{  
    LocalAssembly = Assembly.GetExecutingAssembly()  
};  
  
XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefitinions\MortgageWorkflow.xaml",   
    readerSettings);  
  
ActivityBuilder ab = XamlServices.Load(  
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;  
  
// Prepare the workflow definition for dynamic update.  
DynamicUpdateServices.PrepareForUpdate(ab);  
```  
  
> [!NOTE]
>  <span data-ttu-id="4b64d-128">Pour télécharger l’exemple de code qui accompagne cette rubrique, consultez [exemple de code de mise à jour dynamique](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="4b64d-128">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>  
  
###  <span data-ttu-id="4b64d-129"><a name="Update"></a>Mettre à jour la définition de flux de travail pour refléter les modifications souhaitées</span><span class="sxs-lookup"><span data-stu-id="4b64d-129"><a name="Update"></a> Update the workflow definition to reflect the desired changes</span></span>  
 <span data-ttu-id="4b64d-130">Une fois que la définition de workflow a été élaborée pour la mise à jour, les modifications souhaitées peuvent être apportées.</span><span class="sxs-lookup"><span data-stu-id="4b64d-130">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="4b64d-131">Vous pouvez ajouter ou supprimer des activités, ajouter, déplacer ou supprimer des variables publiques, ajouter ou supprimer des arguments et apporter des modifications à la signature des délégués d'activité.</span><span class="sxs-lookup"><span data-stu-id="4b64d-131">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="4b64d-132">Vous ne pouvez pas supprimer une activité en cours d'exécution ou modifier la signature d'un délégué en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="4b64d-132">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="4b64d-133">Ces modifications peuvent être effectuées à l'aide du code, ou dans un concepteur de workflow réhébergé.</span><span class="sxs-lookup"><span data-stu-id="4b64d-133">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="4b64d-134">Dans l'exemple suivant, une activité `VerifyAppraisal` personnalisée est ajoutée à la séquence qui constitue le corps de `MortgageWorkflow` à partir de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="4b64d-134">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>  
  
```csharp  
// Make desired changes to the definition. In this example, we are  
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.  
VerifyAppraisal va = new VerifyAppraisal  
{  
    Result = new VisualBasicReference<bool>("LoanCriteria")  
};  
  
// Get the Sequence that makes up the body of the workflow.  
Sequence s = ab.Implementation as Sequence;  
  
// Insert the new activity into the Sequence.  
s.Activities.Insert(2, va);  
```  
  
###  <span data-ttu-id="4b64d-135"><a name="Create"></a>Créer le mappage de mise à jour</span><span class="sxs-lookup"><span data-stu-id="4b64d-135"><a name="Create"></a> Create the update map</span></span>  
 <span data-ttu-id="4b64d-136">Une fois que la définition de workflow élaborée pour la mise à jour a été modifiée, la mise à jour de la carte peut être créée.</span><span class="sxs-lookup"><span data-stu-id="4b64d-136">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="4b64d-137">Pour créer une mise à jour de carte dynamique, la méthode <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> est appelée.</span><span class="sxs-lookup"><span data-stu-id="4b64d-137">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="4b64d-138">Retourne un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui contient les informations dont le runtime a besoin pour modifier une instance persistante de workflow de sorte qu'elle puisse être chargée et reprise avec la nouvelle définition de workflow.</span><span class="sxs-lookup"><span data-stu-id="4b64d-138">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="4b64d-139">Dans l'exemple suivant, une carte dynamique est créée pour la définition modifiée de `MortgageWorkflow` de l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="4b64d-139">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>  
  
```csharp  
// Create the update map.  
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);  
```  
  
 <span data-ttu-id="4b64d-140">Cette mise à jour de la carte peut être utilisée immédiatement pour modifier les instances de workflow persistantes, ou elle peut être enregistrée et les mises à jour appliquées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="4b64d-140">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="4b64d-141">Une méthode pour enregistrer la mise à jour de la carte consiste à la sérialiser dans un fichier, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4b64d-141">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>  
  
```csharp  
// Serialize the update map to a file.  
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Create))  
{  
    serializer.WriteObject(fs, map);  
}  
```  
  
 <span data-ttu-id="4b64d-142">Lorsque <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> retourne, la définition clonée de workflow et d'autres informations de mise à jour dynamique qui ont été ajoutées dans l'appel à <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> sont supprimées, et la définition modifiée de workflow est prête à être enregistrée afin qu'elle puisse être utilisée ultérieurement en reprenant les instances de workflow mises à jour.</span><span class="sxs-lookup"><span data-stu-id="4b64d-142">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="4b64d-143">Dans l'exemple suivant, la définition modifiée de workflow est enregistrée dans `MortgageWorkflow_v2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="4b64d-143">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v2.xaml`.</span></span>  
  
```csharp  
// Save the modified workflow definition.  
StreamWriter sw = File.CreateText(@"C:\WorkflowDefitinions\MortgageWorkflow_v1.1.xaml");  
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));  
XamlServices.Save(xw, ab);  
sw.Close();  
```  
  
###  <span data-ttu-id="4b64d-144"><a name="Apply"></a>Appliquer la mise à jour de la carte pour les instances de workflow persistantes souhaitées</span><span class="sxs-lookup"><span data-stu-id="4b64d-144"><a name="Apply"></a> Apply the update map to the desired persisted workflow instances</span></span>  
 <span data-ttu-id="4b64d-145">L'application de la mise à jour de la carte peut être effectuée à tout moment après sa création.</span><span class="sxs-lookup"><span data-stu-id="4b64d-145">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="4b64d-146">Elle peut être effectuée immédiatement à l'aide de l'instance <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> qui a été retournée par <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, ou elle peut être effectuée ultérieurement en utilisant une copie stockée de la mise à jour de la carte.</span><span class="sxs-lookup"><span data-stu-id="4b64d-146">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="4b64d-147">Pour mettre à jour une instance du workflow, chargez-la dans <xref:System.Activities.WorkflowApplicationInstance> à l'aide de <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b64d-147">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4b64d-148">Ensuite, créez un <xref:System.Activities.WorkflowApplication> en utilisant la définition de workflow mise à jour et le <xref:System.Activities.WorkflowIdentity> souhaité.</span><span class="sxs-lookup"><span data-stu-id="4b64d-148">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="4b64d-149">Ce <xref:System.Activities.WorkflowIdentity> peut être différent de celui qui a été utilisé pour rendre persistant le workflow d'origine, et est généralement utilisé pour indiquer que l'instance persistante a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="4b64d-149">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="4b64d-150">Une fois que <xref:System.Activities.WorkflowApplication> est créé, il est chargé à l'aide de la surcharge de <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> qui prend un <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, puis déchargé avec un appel à <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b64d-150">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4b64d-151">Cela applique la mise à jour dynamique et rend persistante l'instance mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="4b64d-151">This applies the dynamic update and persists the updated workflow instance.</span></span>  
  
```csharp  
// Load the serialized update map.  
DynamicUpdateMap map;  
using (FileStream fs = File.Open(@"C:\WorkflowDefitinions\MortgageWorkflow.map", FileMode.Open))  
{  
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
    object updateMap = serializer.ReadObject(fs);  
    if (updateMap == null)  
    {  
        throw new ApplicationException("DynamicUpdateMap is null.");  
    }  
  
    map = (DynamicUpdateMap)updateMap;  
}  
  
// Retrieve a list of workflow instance ids that corresponds to the  
// workflow instances to update. This step is the responsibility of  
// the application developer.  
List<Guid> ids = GetPersistedWorkflowIds();  
foreach (Guid id in ids)  
{  
    // Get a proxy to the persisted workflow instance.  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);  
  
    // If desired, you can inspect the WorkflowIdentity of the instance  
    // using the DefinitionIdentity property to determine whether to apply  
    // the update.  
    Console.WriteLine(instance.DefinitionIdentity);  
  
    // Create a workflow application. You must specify the updated workflow definition, and  
    // you may provide an updated WorkflowIdentity if desired to reflect the update.  
    WorkflowIdentity identity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow v1.1",  
        Version = new Version(1, 1, 0, 0)  
    };  
  
    // Load the persisted workflow instance using the updated workflow definition  
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class  
    // contains the updated definition.  
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
    // Apply the dynamic update on the loaded instance.                
    wfApp.Load(instance, map);  
  
    // Unload the updated instance.  
    wfApp.Unload();  
}  
```  
  
### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="4b64d-152">Reprendre une instance mise à jour de workflow</span><span class="sxs-lookup"><span data-stu-id="4b64d-152">Resuming an Updated Workflow Instance</span></span>  
 <span data-ttu-id="4b64d-153">Une fois la mise à jour dynamique appliquée, l'instance de workflow peut reprendre.</span><span class="sxs-lookup"><span data-stu-id="4b64d-153">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="4b64d-154">Notez que la nouvelle définition mise à jour et <xref:System.Activities.WorkflowIdentity> doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="4b64d-154">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b64d-155">Pour plus d’informations sur l’utilisation de <xref:System.Activities.WorkflowApplication> et <xref:System.Activities.WorkflowIdentity>, consultez[à l’aide de WorkflowIdentity et du Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="4b64d-155">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see[Using WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).</span></span>  
  
 <span data-ttu-id="4b64d-156">Dans l'exemple suivant, le workflow `MortgageWorkflow_v1.1.xaml` de l'exemple précédent a été compilé, et est chargé et repris à l'aide de la définition mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="4b64d-156">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>  
  
```csharp  
// Load the persisted workflow instance using the updated workflow definition  
// and updated WorkflowIdentity.  
WorkflowIdentity identity = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1.1",  
    Version = new Version(1, 1, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure persistence and desired workflow event handlers.  
// (Omitted for brevity.)  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(InstanceId);  
  
// Resume the workflow.  
// wfApp.ResumeBookmark(...);  
```  
  
> [!NOTE]
>  <span data-ttu-id="4b64d-157">Pour télécharger l’exemple de code qui accompagne cette rubrique, consultez [exemple de code de mise à jour dynamique](http://go.microsoft.com/fwlink/?LinkId=227905).</span><span class="sxs-lookup"><span data-stu-id="4b64d-157">To download the sample code that accompanies this topic, see [Dynamic Update sample code](http://go.microsoft.com/fwlink/?LinkId=227905).</span></span>
