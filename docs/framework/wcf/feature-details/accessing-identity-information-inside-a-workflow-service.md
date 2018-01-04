---
title: "Accès aux informations d'identité dans un service de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b832127-b35b-468e-a45f-321381170cbc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06638a9f5aa031bec07a9aac510ce832f75980fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-identity-information-inside-a-workflow-service"></a>Accès aux informations d'identité dans un service de workflow
Pour accéder aux informations d'identité dans un service de workflow, vous devez implémenter l'interface <xref:System.ServiceModel.Activities.IReceiveMessageCallback> dans une propriété d'exécution personnalisée. Dans la méthode <xref:System.ServiceModel.Activities.IReceiveMessageCallback.OnReceiveMessage(System.ServiceModel.OperationContext,System.Activities.ExecutionProperties)>, vous pouvez accéder à <xref:System.ServiceModel.OperationContext.ServiceSecurityContext> pour accéder aux informations d'identité. Cette rubrique vous aidera à implémenter cette propriété d'exécution pour récupérer un en-tête personnalisé, ainsi qu'une activité personnalisée qui affichera cette propriété à l'activité <xref:System.ServiceModel.Activities.Receive> au moment de l'exécution.  L’activité personnalisée implémentera le même comportement qu’une <!--zz <xref:System.ServiceModel.Activities.Sequence>--> `System.ServiceModel.Activities.Sequence` activité, excepté lorsqu’un <xref:System.ServiceModel.Activities.Receive> est placé à l’intérieur, le <xref:System.ServiceModel.Activities.IReceiveMessageCallback> est appelée et les informations d’identité sont récupérées.  
  
### <a name="implement-ireceivemessagecallback"></a>Implémenter IReceiveMessageCallback  
  
1.  Créez une solution [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] vide.  
  
2.  Ajoutez à la solution une nouvelle application console nommée `Service`.  
  
3.  Ajoutez des références aux assemblys suivants :  
  
    1.  System.Runtime.Serialization  
  
    2.  System.ServiceModel  
  
    3.  System.ServiceModel.Activities  
  
4.  Ajoutez une classe nommée `AccessIdentityCallback` et implémentez <xref:System.ServiceModel.Activities.IReceiveMessageCallback> tel qu'illustré dans l'exemple suivant.  
  
    ```csharp  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
       public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
       {  
          try  
          {  
             Console.WriteLine("Received a message from a workflow with the following identity");  
             Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
             Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
             Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
          }            
          catch (Exception ex)  
          {  
             Console.WriteLine("An exception occurred: " + ex.Message);  
          }  
        }  
    }  
    ```  
  
     Ce code utilise le <xref:System.ServiceModel.OperationContext> passé dans la méthode pour accéder aux informations d'identité.  
  
### <a name="implement-a-native-activity-to-add-the-ireceivemessagecallback-implementation-to-the-nativeactivitycontext"></a>Implémenter une activité native pour ajouter l'implémentation de IReceiveMessageCallback à NativeActivityContext  
  
1.  Ajoutez une nouvelle classe dérivée de <xref:System.Activities.NativeActivity> nommée `AccessIdentityScope`.  
  
2.  Ajoutez des variables locales pour effectuer le suivi des activités enfants, des variables, de l'index de l'activité actuelle, et un rappel  <xref:System.Activities.CompletionCallback>.  
  
    ```  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
    }  
    ```  
  
3.  Implémenter le constructeur  
  
    ```  
    public AccessIdentityScope() : base()  
    {  
        this.children = new Collection<Activity>();  
        this.variables = new Collection<Variable>();  
        this.currentIndex = new Variable<int>();  
    }  
    ```  
  
4.  Implémentez les propriétés `Activities` et `Variables`.  
  
    ```  
    public Collection<Activity> Activities  
    {  
         get { return this.children; }  
    }  
  
    public Collection<Variable> Variables  
    {  
        get { return this.variables; }  
    }  
    ```  
  
5.  Substituer la méthode <xref:System.Activities.NativeActivity.CacheMetadata%2A>  
  
    ```  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
        base.CacheMetadata(metadata);  
        //add the private implementation variable: currentIndex   
        metadata.AddImplementationVariable(this.currentIndex);  
    }  
    ```  
  
6.  Substituer la méthode <xref:System.Activities.NativeActivity.Execute%2A>  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
    {  
       // Add the IReceiveMessageCallback implementation as an Execution property   
       context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
       InternalExecute(context, null);  
    }  
  
    void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
    {  
       //grab the index of the current Activity  
       int currentActivityIndex = this.currentIndex.Get(context);  
       if (currentActivityIndex == Activities.Count)  
       {  
          //if the currentActivityIndex is equal to the count of MySequence's Activities  
          //MySequence is complete  
          return;  
       }  
  
       if (this.onChildComplete == null)  
       {  
          //on completion of the current child, have the runtime call back on this method  
          this.onChildComplete = new CompletionCallback(InternalExecute);  
       }  
  
       //grab the next Activity in MySequence.Activities and schedule it  
       Activity nextChild = Activities[currentActivityIndex];  
       context.ScheduleActivity(nextChild, this.onChildComplete);  
  
       //increment the currentIndex  
       this.currentIndex.Set(context, ++currentActivityIndex);  
    }  
    ```  
  
### <a name="implement-the-workflow-service"></a>Implémenter le service de workflow  
  
1.  Ouvrir `Program` classe.  
  
2.  Définissez les constantes suivantes :  
  
    ```  
    class Program  
    {  
       const string addr = "http://localhost:8080/Service";  
       static XName contract = XName.Get("IService", "http://tempuri.org");  
    }  
    ```  
  
3.  Ajoutez une méthode statique nommée `GetWorkflowService` qui crée le service de workflow.  
  
    ```  
    static Activity GetServiceWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       // Create the Receive activity  
       Receive echoRequest = new Receive  
       {  
          CanCreateInstance = true,  
          ServiceContractName = contract,  
          OperationName = "Echo",  
          Content = new ReceiveParametersContent()  
          {  
             Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
          }  
       };  
  
       return new AccessIdentityScope  
       {  
          Variables = { echoString },  
          Activities =  
          {  
             echoRequest,  
             new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
             new SendReply  
             {  
                Request = echoRequest,  
                Content = new SendParametersContent()  
                {  
                   Parameters = { { "result", new InArgument<string>(echoString) } }   
                }  
             }  
          }  
       };  
     }  
    ```  
  
4.  Dans la méthode `Main` existante, hébergez le service de workflow.  
  
    ```  
    static void Main(string[] args)  
    {  
       string addr = "http://localhost:8080/Service";  
  
       using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
       {  
          WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
          host.AddServiceEndpoint(contract, binding, addr);  
  
          host.Open();  
          Console.WriteLine("Service waiting at: " + addr);  
          Console.WriteLine("Press [ENTER] to exit");  
          Console.ReadLine();  
          host.Close();  
       }  
    }  
    ```  
  
### <a name="implement-a-workflow-client"></a>Implémenter un client de workflow  
  
1.  Créez un projet d'application console nommé `Client`.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    1.  System.Activities  
  
    2.  System.ServiceModel  
  
    3.  System.ServiceModel.Activities  
  
3.  Ouvrez le fichier Program.cs généré et ajoutez une méthode statique nommée `GetClientWorkflow` pour créer le workflow client.  
  
    ```  
    static Activity GetClientWorkflow()  
    {  
       Variable<string> echoString = new Variable<string>();  
  
       Endpoint clientEndpoint = new Endpoint  
       {  
          Binding = new WSHttpBinding(SecurityMode.Message),  
          AddressUri = new Uri("http://localhost:8080/Service")  
       };  
  
       Send echoRequest = new Send  
       {  
          Endpoint = clientEndpoint,  
          ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
          OperationName = "Echo",  
          Content = new SendParametersContent()  
          {  
             Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
          }  
       };  
  
       return new Sequence  
       {  
          Variables = { echoString },  
          Activities =  
          {                      
             new CorrelationScope  
             {  
                Body = new Sequence  
                {  
                   Activities =   
                   {  
                      echoRequest,  
                      new ReceiveReply  
                      {  
                         Request = echoRequest,  
                         Content = new ReceiveParametersContent  
                         {  
                            Parameters = { { "result", new OutArgument<string>(echoString) } }  
                         }  
                      }  
                   }  
                }  
             },                      
             new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
             }  
          };  
       }  
    }  
    ```  
  
4.  Ajoutez le code d'hébergement suivant à la méthode `Main()`.  
  
    ```  
    static void Main(string[] args)  
    {  
       Activity workflow = GetClientWorkflow();  
       WorkflowInvoker.Invoke(workflow);  
       WorkflowInvoker.Invoke(workflow);  
       Console.WriteLine("Press [ENTER] to exit");  
       Console.ReadLine();  
    }  
    ```  
  
## <a name="example"></a>Exemple  
 L'intégralité du code source utilisé dans cette rubrique est présentée ci-dessous.  
  
```  
// AccessIdentityCallback.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    class AccessIdentityCallback : IReceiveMessageCallback  
    {  
        public const string HeaderName = "InstanceIdHeader";  
        public const string HeaderNS = "http://Microsoft.Samples.AccessingOperationContext";  
  
        public void OnReceiveMessage(System.ServiceModel.OperationContext operationContext, System.Activities.ExecutionProperties activityExecutionProperties)  
        {  
            try  
            {  
                // Guid instanceId = operationContext.IncomingMessageHeaders.GetHeader<Guid>(HeaderName, HeaderNS);  
                Console.WriteLine("Received a message from a workflow with the following identity" ); // with instanceId = {0}", instanceId);  
                Console.WriteLine("Windows Identity Name: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.Name);  
                Console.WriteLine("Windows Identity User: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.User);  
                Console.WriteLine("Windows Identity IsAuthenticated: {0}", operationContext.ServiceSecurityContext.WindowsIdentity.IsAuthenticated);  
            }  
            catch (MessageHeaderException)  
            {  
                Console.WriteLine("This message must not be from a workflow.");  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("An exception occurred: " + ex.Message);  
            }  
        }  
    }  
}  
```  
  
```  
// AccessIdentityScope.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System.Activities;  
using System.Collections.ObjectModel;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{  
    public sealed class AccessIdentityScope : NativeActivity  
    {  
        Collection<Activity> children;  
        Collection<Variable> variables;  
        Variable<int> currentIndex;  
        CompletionCallback onChildComplete;  
  
        public AccessIdentityScope()  
            : base()  
        {  
            this.children = new Collection<Activity>();  
            this.variables = new Collection<Variable>();  
            this.currentIndex = new Variable<int>();  
        }  
  
        public Collection<Activity> Activities  
        {  
            get  
            {  
                return this.children;  
            }  
        }  
  
        public Collection<Variable> Variables  
        {  
            get  
            {  
                return this.variables;  
            }  
        }  
  
        protected override void CacheMetadata(NativeActivityMetadata metadata)  
        {  
            //call base.CacheMetadata to add the Activities and Variables to this activity's metadata  
            base.CacheMetadata(metadata);  
            //add the private implementation variable: currentIndex   
            metadata.AddImplementationVariable(this.currentIndex);  
        }                     
  
        protected override void Execute(  
            NativeActivityContext context)  
        {  
            context.Properties.Add("AccessIdentityCallback", new AccessIdentityCallback());  
            InternalExecute(context, null);  
        }  
  
        void InternalExecute(NativeActivityContext context, ActivityInstance instance)  
        {  
            //grab the index of the current Activity  
            int currentActivityIndex = this.currentIndex.Get(context);  
            if (currentActivityIndex == Activities.Count)  
            {  
                //if the currentActivityIndex is equal to the count of MySequence's Activities  
                //MySequence is complete  
                return;  
            }  
  
            if (this.onChildComplete == null)  
            {  
                //on completion of the current child, have the runtime call back on this method  
                this.onChildComplete = new CompletionCallback(InternalExecute);  
            }  
  
            //grab the next Activity in MySequence.Activities and schedule it  
            Activity nextChild = Activities[currentActivityIndex];  
            context.ScheduleActivity(nextChild, this.onChildComplete);  
  
            //increment the currentIndex  
            this.currentIndex.Set(context, ++currentActivityIndex);  
        }  
    }  
}  
```  
  
```  
// Service.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Service  
{      
    class Program  
    {  
        const string addr = "http://localhost:8080/Service";  
        static XName contract = XName.Get("IService", "http://tempuri.org");  
  
        static void Main(string[] args)  
        {  
            string addr = "http://localhost:8080/Service";  
  
            using (WorkflowServiceHost host = new WorkflowServiceHost(GetServiceWorkflow()))  
            {  
                WSHttpBinding binding = new WSHttpBinding(SecurityMode.Message);  
                host.AddServiceEndpoint(contract, binding, addr);  
  
                host.Open();  
                Console.WriteLine("Service waiting at: " + addr);  
                Console.WriteLine("Press [ENTER] to exit");  
                Console.ReadLine();  
                host.Close();  
            }  
  
        }  
  
        static Activity GetServiceWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Receive echoRequest = new Receive  
            {  
                CanCreateInstance = true,  
                ServiceContractName = contract,  
                OperationName = "Echo",  
                Content = new ReceiveParametersContent()  
                {  
                    Parameters = { { "echoString", new OutArgument<string>(echoString) } }  
                }  
            };  
  
            return new AccessIdentityScope  
            {  
                Variables = { echoString },  
                Activities =  
                {  
                    echoRequest,  
                    new WriteLine { Text = new InArgument<string>( (e) => "Received: " + echoString.Get(e) ) },  
                    new SendReply  
                    {  
                        Request = echoRequest,  
                        Content = new SendParametersContent()  
                        {  
                            Parameters = { { "result", new InArgument<string>(echoString) } }   
                        }  
                    }  
                }  
            };  
        }  
    }  
}  
```  
  
```  
// client.cs   
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
  
using System;  
using System.Activities;  
using System.Activities.Statements;  
using System.ServiceModel;  
using System.ServiceModel.Activities;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.AccessingOperationContext.Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Activity workflow = GetClientWorkflow();  
            WorkflowInvoker.Invoke(workflow);  
            WorkflowInvoker.Invoke(workflow);  
            Console.WriteLine("Press [ENTER] to exit");  
            Console.ReadLine();  
        }  
  
        static Activity GetClientWorkflow()  
        {  
            Variable<string> echoString = new Variable<string>();  
  
            Endpoint clientEndpoint = new Endpoint  
            {  
                Binding = new WSHttpBinding(SecurityMode.Message),  
                AddressUri = new Uri("http://localhost:8080/Service")  
            };  
  
            Send echoRequest = new Send  
            {  
                Endpoint = clientEndpoint,  
                ServiceContractName = XName.Get("IService", "http://tempuri.org"),  
                OperationName = "Echo",  
                Content = new SendParametersContent()  
                {  
                    Parameters = { { "echoString", new InArgument<string>("Hello, World") } }   
                }  
            };  
  
            return new Sequence  
            {  
                Variables = { echoString },  
                Activities =  
                {                      
                    new CorrelationScope  
                    {  
                        Body = new Sequence  
                        {  
                            Activities =   
                            {  
                                echoRequest,  
                                new ReceiveReply  
                                {  
                                    Request = echoRequest,  
                                    Content = new ReceiveParametersContent  
                                    {  
                                        Parameters = { { "result", new OutArgument<string>(echoString) } }  
                                    }  
                                }  
                            }  
                        }  
                    },                      
                    new WriteLine { Text = new InArgument<string>( (e) => "Received Text: " + echoString.Get(e) ) },                      
                }  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Accès à OperationContext](../../../../docs/framework/windows-workflow-foundation/samples/accessing-operationcontext.md)  
 [Création de workflows, d’activités et d’expressions à l’aide du code impératif](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
