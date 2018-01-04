---
title: "Procédure : créer un magasin d'instances personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db9f09236764697aff4e57ace593827193c6e07d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="d6deb-102">Procédure : créer un magasin d'instances personnalisé</span><span class="sxs-lookup"><span data-stu-id="d6deb-102">How to: Create a Custom Instance Store</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="d6deb-103"> contient <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, un magasin d'instance qui utilise SQL Server pour rendre les données de workflow persistantes.</span><span class="sxs-lookup"><span data-stu-id="d6deb-103"> contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="d6deb-104">Si votre application est requise pour la persistance des données de workflow sur un autre support, tel qu'une autre base de données ou un système de fichiers, vous pouvez implémenter un magasin d'instances personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d6deb-104">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="d6deb-105">Un magasin d'instances personnalisé est créé en étendant la classe abstraite <xref:System.Runtime.DurableInstancing.InstanceStore> et en implémentant les méthodes nécessaires pour l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="d6deb-105">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="d6deb-106">Pour une implémentation complète d’un magasin d’instances personnalisé, consultez la [processus d’achat d’entreprise](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="d6deb-106">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span>  
  
## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="d6deb-107">Implémentation de la méthode BeginTryCommand</span><span class="sxs-lookup"><span data-stu-id="d6deb-107">Implementing the BeginTryCommand method</span></span>  
 <span data-ttu-id="d6deb-108"><xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> est envoyé au magasin d'instances par le moteur de persistance.</span><span class="sxs-lookup"><span data-stu-id="d6deb-108">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="d6deb-109">Le type du paramètre `command` indique la commande qui est exécutée ; ce paramètre peut être des types suivants :</span><span class="sxs-lookup"><span data-stu-id="d6deb-109">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>  
  
-   <span data-ttu-id="d6deb-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un workflow doit être rendu persistant sur le support de stockage.</span><span class="sxs-lookup"><span data-stu-id="d6deb-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="d6deb-111">Les données de persistance de workflow sont fournies à la méthode dans le membre <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> du paramètre `command` .</span><span class="sxs-lookup"><span data-stu-id="d6deb-111">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>  
  
-   <span data-ttu-id="d6deb-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un workflow doit être chargé à partir du support de stockage.</span><span class="sxs-lookup"><span data-stu-id="d6deb-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="d6deb-113">l'ID d'instance du workflow à charger est fourni à la méthode dans le paramètre `instanceId` de la propriété <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> du paramètre `context`.</span><span class="sxs-lookup"><span data-stu-id="d6deb-113">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>  
  
-   <span data-ttu-id="d6deb-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un <xref:System.ServiceModel.Activities.WorkflowServiceHost> doit être enregistré en tant que propriétaire de verrou.</span><span class="sxs-lookup"><span data-stu-id="d6deb-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="d6deb-115">L'ID d'instance du workflow actuel doit être fourni au magasin d'instances à l'aide de la méthode <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> du paramètre `context`.</span><span class="sxs-lookup"><span data-stu-id="d6deb-115">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>  
  
     <span data-ttu-id="d6deb-116">L'extrait de code suivant montre comment implémenter la commande CreateWorkflowOwner pour assigner un propriétaire de verrou explicite.</span><span class="sxs-lookup"><span data-stu-id="d6deb-116">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>  
  
    ```  
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");  
    ...  
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()  
    {  
        InstanceOwnerMetadata =  
        {  
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },  
        }  
    };  
    InstanceHandle ownerHandle = store.CreateInstanceHandle();  
    store.DefaultInstanceOwner = store.Execute(  
                                   ownerHandle,  
                                   createCommand,  
                                   TimeSpan.FromSeconds(30)).InstanceOwner;  
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });  
    ```  
  
-   <span data-ttu-id="d6deb-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsque l'ID d'instance d'un propriétaire de verrou peut être supprimé du magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="d6deb-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="d6deb-118">Comme avec <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, l'ID du propriétaire du verrou doit être fourni par l'application.</span><span class="sxs-lookup"><span data-stu-id="d6deb-118">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>  
  
     <span data-ttu-id="d6deb-119">L'extrait de code suivant montre comment libérer un verrou à l'aide de <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span><span class="sxs-lookup"><span data-stu-id="d6deb-119">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>  
  
    ```  
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)  
    {  
        handle.Free();  
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);  
        try  
        {  
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.  
            Thread.Sleep(10000);  
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));  
        }  
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }  
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }  
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }  
        catch (Exception ex) { Log.Inform(ex.Message); }  
        finally  
        {  
            handle.Free();  
            store.DefaultInstanceOwner = null;  
        }  
    }  
    ```  
  
     <span data-ttu-id="d6deb-120">La méthode ci-dessus doit être appelée dans un bloc Try/Catch lorsqu'une instance enfant est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d6deb-120">The above method should be called in a Try/Catch block when a child instance is run.</span></span>  
  
    ```  
    try  
    {  
        childInstance.Run();  
    }  
    catch (Exception)  
    {  
        throw ;  
    }  
    finally  
    {  
        FreeHandleAndDeleteOwner(store, ownerHandle);  
    }  
    ```  
  
-   <span data-ttu-id="d6deb-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'une instance de workflow doit être chargée à l'aide de la clé d'instance du workflow.</span><span class="sxs-lookup"><span data-stu-id="d6deb-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="d6deb-122">L'ID de la clé d'instance peut être déterminé à l'aide du paramètre <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> de la commande.</span><span class="sxs-lookup"><span data-stu-id="d6deb-122">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>  
  
-   <span data-ttu-id="d6deb-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> : Le moteur de persistance envoie cette commande au magasin d'instances pour récupérer des paramètres d'activation des workflows persistants afin qu'un hôte de workflow puisse ensuite charger les workflows.</span><span class="sxs-lookup"><span data-stu-id="d6deb-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="d6deb-124">Cette commande est envoyée par le moteur en réponse au magasin d'instances qui déclenche <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> à l'hôte lorsqu'il localise une instance qui peut être activée.</span><span class="sxs-lookup"><span data-stu-id="d6deb-124">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="d6deb-125">Le magasin d'instances doit être interrogé pour déterminer s'il existe des workflows qui peuvent être activés.</span><span class="sxs-lookup"><span data-stu-id="d6deb-125">The instance store should be polled to determine if there are workflows that can be activated.</span></span>  
  
-   <span data-ttu-id="d6deb-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances pour charger les instances de workflow exécutables.</span><span class="sxs-lookup"><span data-stu-id="d6deb-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="d6deb-127">Cette commande est envoyée par le moteur en réponse au magasin d'instances qui déclenche <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> à l'hôte lorsqu'il localise une instance qui peut être exécutée.</span><span class="sxs-lookup"><span data-stu-id="d6deb-127">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="d6deb-128">Le magasin d'instances doit interroger les workflows qui peuvent être exécutés.</span><span class="sxs-lookup"><span data-stu-id="d6deb-128">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="d6deb-129">L'extrait de code suivant montre comment interroger un magasin d'instances pour les workflows qui peuvent être exécutés ou activés.</span><span class="sxs-lookup"><span data-stu-id="d6deb-129">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
                    if (hasRunnable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))  
                {  
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="d6deb-130">Dans l'extrait de code ci-dessus, le magasin d'instances interroge les événements disponibles et examine chacun d'eux pour déterminer s'il s'agit d'un événement <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>.</span><span class="sxs-lookup"><span data-stu-id="d6deb-130">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="d6deb-131">Le cas échéant, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> est appelé pour signaler à l'hôte d'envoyer une commande au magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="d6deb-131">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span>  <span data-ttu-id="d6deb-132">L'extrait de code suivant illustre une implémentation d'un gestionnaire pour cette commande.</span><span class="sxs-lookup"><span data-stu-id="d6deb-132">The following code snippet demonstrates an implementation of a handler for this command.</span></span>  
  
    ```  
    If (command is TryLoadRunnableWorkflowCommand)  
    {  
        Owner owner;  
        CheckOwner(context, command.Name, out owner);                          
        // Checking instance.Owner is like an InstanceLockQueryResult.  
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));  
  
        XName ownerService = null;  
        InstanceValue value;  
        Instance runnableInstance = default(Instance);  
        bool foundRunnableInstance = false;  
  
        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);  
        if (value != null && value.Value is XName)  
        {  
            ownerService = (XName)value.Value;  
        }  
  
        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)  
        {  
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)  
            {  
                continue;  
            }  
  
            if (ownerService != null)  
            {  
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);  
                if (value == null || ((XName)value.Value) != ownerService)  
                {  
                    continue;  
                }  
            }  
  
            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);  
            if (value != null && value.Value != null && value.Value is string)  
            {  
                continue;  
            }  
  
            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);  
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")  
            {  
                runnableInstance = instance.Value;  
                foundRunnableInstance = true;  
            }  
  
            if (!foundRunnableInstance)  
            {  
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);  
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)  
                {                          
                    runnableInstance = instance.Value;  
                    foundRunnableInstance = true;  
                }  
            }  
  
            if (foundRunnableInstance)  
            {  
                runnableInstance.LockVersion++;  
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;  
                MemoryStore.instances[instance.Key] = runnableInstance;  
                context.BindInstance(instance.Key);  
                context.BindAcquiredLock(runnableInstance.LockVersion);  
  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)  
                {  
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)  
                {  
                    if (keyEntry.Value.Completed)  
                    {  
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                    else  
                    {  
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                }  
            }  
  
            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);  
            break;  
        }  
    }  
    ```  
  
     <span data-ttu-id="d6deb-133">Dans l'extrait de code ci-dessus, le magasin d'instances recherche les instances exécutables.</span><span class="sxs-lookup"><span data-stu-id="d6deb-133">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="d6deb-134">Si une instance est trouvée, elle est liée au contexte d'exécution et chargée.</span><span class="sxs-lookup"><span data-stu-id="d6deb-134">If an instance is found, it is bound to the execution context and loaded.</span></span>  
  
## <a name="using-a-custom-instance-store"></a><span data-ttu-id="d6deb-135">Utilisation d'un magasin d'instances personnalisé</span><span class="sxs-lookup"><span data-stu-id="d6deb-135">Using a custom instance store</span></span>  
 <span data-ttu-id="d6deb-136">Pour implémenter un magasin d'instances personnalisé, assignez une instance du magasin d'instances à <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, et implémentez la méthode <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6deb-136">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span>  <span data-ttu-id="d6deb-137">Consultez le [Comment : créer et exécuter un Workflow de longue durée](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) didacticiel pour plus de détails.</span><span class="sxs-lookup"><span data-stu-id="d6deb-137">See the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>  
  
## <a name="a-sample-instance-store"></a><span data-ttu-id="d6deb-138">Exemple de magasin d'instances</span><span class="sxs-lookup"><span data-stu-id="d6deb-138">A sample instance store</span></span>  
 <span data-ttu-id="d6deb-139">L’exemple de code suivant est une implémentation de magasin instance terminée, obtenue à partir du [processus d’achat d’entreprise](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="d6deb-139">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="d6deb-140">Ce magasin d'instances rend des données de workflow persistantes dans un fichier à l'aide du XML.</span><span class="sxs-lookup"><span data-stu-id="d6deb-140">This instance store persists workflow data to a file using XML.</span></span>  
  
```  
using System;  
using System.Activities.DurableInstancing;  
using System.Collections.Generic;  
using System.IO;  
using System.Runtime.DurableInstancing;  
using System.Runtime.Serialization;  
using System.ServiceModel.Persistence;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.WF.PurchaseProcess  
{  
  
    public class XmlWorkflowInstanceStore : InstanceStore  
    {  
        Guid ownerInstanceID;  
  
        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())  
        {  
  
        }  
  
        public XmlWorkflowInstanceStore(Guid id)  
        {  
            ownerInstanceID = id;  
        }  
  
        //Synchronous version of the Begin/EndTryCommand functions  
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)  
        {  
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));  
        }  
  
        //The persistence engine will send a variety of commands to the configured InstanceStore,  
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.  
        //This method is where we will handle those commands  
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)  
        {  
            IDictionary<XName, InstanceValue> data = null;  
  
            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle  
            if (command is CreateWorkflowOwnerCommand)  
            {  
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());  
            }  
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key  
            else if (command is SaveWorkflowCommand)  
            {  
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;  
                data = saveCommand.InstanceData;  
  
                Save(data);  
            }  
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle  
            else if (command is LoadWorkflowCommand)  
            {  
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
  
                try  
                {  
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))  
                    {  
                        data = LoadInstanceDataFromFile(inputStream);  
                        //load the data into the persistence Context  
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);  
                    }  
                }  
                catch (Exception exception)  
                {  
                    throw new PersistenceException(exception.Message);  
                }  
            }  
  
            return new CompletedAsyncResult<bool>(true, callback, state);  
        }  
  
        protected override bool EndTryCommand(IAsyncResult result)  
        {  
            return CompletedAsyncResult<bool>.End(result);  
        }  
  
        //Reads data from xml file and creates a dictionary based off of that.  
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)  
        {  
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();  
  
            NetDataContractSerializer s = new NetDataContractSerializer();  
  
            XmlReader rdr = XmlReader.Create(inputStream);  
            XmlDocument doc = new XmlDocument();  
            doc.Load(rdr);  
  
            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");  
            foreach (XmlElement instanceElement in instances)  
            {  
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");  
                XName key = (XName)DeserializeObject(s, keyElement);  
  
                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");  
                object value = DeserializeObject(s, valueElement);  
                InstanceValue instVal = new InstanceValue(value);  
  
                data.Add(key, instVal);  
            }  
  
            return data;  
        }  
  
        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)  
        {  
            object deserializedObject = null;  
  
            MemoryStream stm = new MemoryStream();  
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);  
            element.WriteContentTo(wtr);  
            wtr.Flush();  
            stm.Position = 0;  
  
            deserializedObject = serializer.Deserialize(stm);  
  
            return deserializedObject;  
        }  
  
        //Saves the persistence data to an xml file.  
        void Save(IDictionary<XName, InstanceValue> instanceData)  
        {  
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
            XmlDocument doc = new XmlDocument();  
            doc.LoadXml("<InstanceValues/>");  
  
            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)  
            {  
                XmlElement newInstance = doc.CreateElement("InstanceValue");  
  
                XmlElement newKey = SerializeObject("key", valPair.Key, doc);  
                newInstance.AppendChild(newKey);  
  
                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);  
                newInstance.AppendChild(newValue);  
  
                doc.DocumentElement.AppendChild(newInstance);  
            }  
            doc.Save(fileName);  
       }  
  
        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)  
        {  
            NetDataContractSerializer s = new NetDataContractSerializer();  
            XmlElement newElement = doc.CreateElement(elementName);  
            MemoryStream stm = new MemoryStream();  
  
            s.Serialize(stm, o);  
            stm.Position = 0;  
            StreamReader rdr = new StreamReader(stm);  
            newElement.InnerXml = rdr.ReadToEnd();  
  
            return newElement;  
        }  
    }  
}  
```
