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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c383d3af92ba2f76f8ba09bc194220c170beaa0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-instance-store"></a>Procédure : créer un magasin d'instances personnalisé
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] contient <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, un magasin d'instance qui utilise SQL Server pour rendre les données de workflow persistantes. Si votre application est requise pour la persistance des données de workflow sur un autre support, tel qu'une autre base de données ou un système de fichiers, vous pouvez implémenter un magasin d'instances personnalisé. Un magasin d'instances personnalisé est créé en étendant la classe abstraite <xref:System.Runtime.DurableInstancing.InstanceStore> et en implémentant les méthodes nécessaires pour l'implémentation. Pour une implémentation complète d’un magasin d’instances personnalisé, consultez la [processus d’achat d’entreprise](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemple.  
  
## <a name="implementing-the-begintrycommand-method"></a>Implémentation de la méthode BeginTryCommand  
 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> est envoyé au magasin d'instances par le moteur de persistance. Le type du paramètre `command` indique la commande qui est exécutée ; ce paramètre peut être des types suivants :  
  
-   <xref:System.Activities.DurableInstancing.SaveWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un workflow doit être rendu persistant sur le support de stockage. Les données de persistance de workflow sont fournies à la méthode dans le membre <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> du paramètre `command` .  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un workflow doit être chargé à partir du support de stockage. l'ID d'instance du workflow à charger est fourni à la méthode dans le paramètre `instanceId` de la propriété <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> du paramètre `context`.  
  
-   <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'un <xref:System.ServiceModel.Activities.WorkflowServiceHost> doit être enregistré en tant que propriétaire de verrou. L'ID d'instance du workflow actuel doit être fourni au magasin d'instances à l'aide de la méthode <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> du paramètre `context`.  
  
     L'extrait de code suivant montre comment implémenter la commande CreateWorkflowOwner pour assigner un propriétaire de verrou explicite.  
  
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
  
-   <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsque l'ID d'instance d'un propriétaire de verrou peut être supprimé du magasin d'instances. Comme avec <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, l'ID du propriétaire du verrou doit être fourni par l'application.  
  
     L'extrait de code suivant montre comment libérer un verrou à l'aide de <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.  
  
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
  
     La méthode ci-dessus doit être appelée dans un bloc Try/Catch lorsqu'une instance enfant est exécutée.  
  
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
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand> : Le moteur de persistance envoie cette commande au magasin d'instances lorsqu'une instance de workflow doit être chargée à l'aide de la clé d'instance du workflow. L'ID de la clé d'instance peut être déterminé à l'aide du paramètre <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> de la commande.  
  
-   <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand> : Le moteur de persistance envoie cette commande au magasin d'instances pour récupérer des paramètres d'activation des workflows persistants afin qu'un hôte de workflow puisse ensuite charger les workflows. Cette commande est envoyée par le moteur en réponse au magasin d'instances qui déclenche <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> à l'hôte lorsqu'il localise une instance qui peut être activée. Le magasin d'instances doit être interrogé pour déterminer s'il existe des workflows qui peuvent être activés.  
  
-   <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand> : Le moteur de persistance envoie cette commande au magasin d'instances pour charger les instances de workflow exécutables. Cette commande est envoyée par le moteur en réponse au magasin d'instances qui déclenche <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> à l'hôte lorsqu'il localise une instance qui peut être exécutée. Le magasin d'instances doit interroger les workflows qui peuvent être exécutés. L'extrait de code suivant montre comment interroger un magasin d'instances pour les workflows qui peuvent être exécutés ou activés.  
  
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
  
     Dans l'extrait de code ci-dessus, le magasin d'instances interroge les événements disponibles et examine chacun d'eux pour déterminer s'il s'agit d'un événement <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent>. Le cas échéant, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> est appelé pour signaler à l'hôte d'envoyer une commande au magasin d'instances.  L'extrait de code suivant illustre une implémentation d'un gestionnaire pour cette commande.  
  
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
  
     Dans l'extrait de code ci-dessus, le magasin d'instances recherche les instances exécutables. Si une instance est trouvée, elle est liée au contexte d'exécution et chargée.  
  
## <a name="using-a-custom-instance-store"></a>Utilisation d'un magasin d'instances personnalisé  
 Pour implémenter un magasin d'instances personnalisé, assignez une instance du magasin d'instances à <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, et implémentez la méthode <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>.  Consultez le [Comment : créer et exécuter un Workflow de longue durée](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) didacticiel pour plus de détails.  
  
## <a name="a-sample-instance-store"></a>Exemple de magasin d'instances  
 L’exemple de code suivant est une implémentation de magasin instance terminée, obtenue à partir du [processus d’achat d’entreprise](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) exemple. Ce magasin d'instances rend des données de workflow persistantes dans un fichier à l'aide du XML.  
  
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
