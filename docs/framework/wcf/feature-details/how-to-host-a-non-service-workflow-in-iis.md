---
title: "Procédure : héberger un workflow sans service dans IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362562c-767d-401b-8257-916616568fd4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b7ffdc00a7723fd6b514fbb5577c48da15d719c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-non-service-workflow-in-iis"></a>Procédure : héberger un workflow sans service dans IIS
Les workflows qui ne sont pas des services de workflow peuvent être hébergés sous IIS/WAS. Cela peut s'avérer utile lorsque vous avez besoin d'héberger un workflow écrit par une autre personne. Cela peut être le cas si vous hébergez à nouveau le concepteur de workflow et permettez aux utilisateurs de créer leurs propres workflows.  L'hébergement dans IIS de workflows sans service permet la prise en charge de fonctionnalités telles que le recyclage de processus, l'arrêt en cas d'inactivité, le contrôle d'état de processus et l'activation basée sur message. Les services de workflow hébergés dans IIS contiennent des activités <xref:System.ServiceModel.Activities.Receive> et sont activés lorsque IIS reçoit un message. Les workflows sans service ne contiennent pas d'activités de messagerie et, par défaut, ne peuvent pas être activés par l'envoi d'un message.  Pour créer une instance du workflow, vous devez dériver une classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> et définir un contrat de service contenant des opérations. Cette rubrique vous guide dans la création d’un workflow simple, la définition d’un contrat de service un client peut utiliser pour activer le flux de travail et la dériver une classe de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> qui utilise le contrat de service pour écouter les demandes de création de workflow.  
  
### <a name="create-a-simple-workflow"></a>Créer un workflow simple  
  
1.  Créez une solution [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] vide appelée `CreationEndpointTest`.  
  
2.  Ajoutez à la solution un nouveau projet d'application de service de workflow WCF appelée `SimpleWorkflow`. Le concepteur de workflow s'ouvre.  
  
3.  Supprimez les activités ReceiveRequest et SendResponse. Ces activités font d'un workflow un service de workflow. Elles ne nous sont plus utiles dans la mesure où nous ne travaillons pas avec un service de workflow.  
  
4.  Affectez au DisplayName de l’activité de séquence à « Workflow séquentiel ».  
  
5.  Renommez Service1.xamlx en Workflow1.xamlx.  
  
6.  Cliquez sur le concepteur en dehors de l’activité de séquence et définissez les propriétés Name et ConfigurationName valeur « Workflow1 »  
  
7.  Faites glisser une activité <xref:System.Activities.Statements.WriteLine> dans <xref:System.Activities.Statements.Sequence>. Le <xref:System.Activities.Statements.WriteLine> activité se trouvent dans le **Primitives** section de la boîte à outils. Définir le <xref:System.Activities.Statements.WriteLine.Text%2A> propriété de la <xref:System.Activities.Statements.WriteLine> activité à « Hello, world ».  
  
     Le workflow doit maintenant ressembler au diagramme suivant.  
  
     ![Un flux de travail simple](../../../../docs/framework/wcf/feature-details/media/simpleworkflow.png "SimpleWorkflow")  
  
### <a name="create-the-workflow-creation-service-contract"></a>Créer le contrat de service de création de workflow  
  
1.  Ajoutez à la solution `Shared` un nouveau projet de bibliothèque de classes appelé `CreationEndpointTest`.  
  
2.  Ajoutez au projet `Shared` une référence à System.ServiceModel.dll, System.Configuration et System.ServiceModel.Activities.  
  
3.  Renommez le fichier Class1.cs en IWorkflowCreation.cs et ajoutez le code suivant au fichier.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
  
    namespace Shared  
    {  
        //service contract exposed from the endpoint  
        [ServiceContract(Name = "IWorkflowCreation")]  
        public interface IWorkflowCreation  
        {  
            [OperationContract(Name = "Create")]  
            Guid Create(IDictionary<string, object> inputs);  
  
            [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
            void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
        }  
    }  
    ```  
  
     Ce contrat définit deux opérations qui créent toutes deux une instance du workflow sans service que vous venez de créer. L'une crée une instance avec un ID d'instance généré, l'autre vous permet de spécifier l'ID d'instance de la nouvelle instance de workflow.  Ces deux méthodes vous permettent de passer des paramètres à la nouvelle instance de workflow. Ce contrat sera exposé par le <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pour permettre aux clients de créer des instances d’un workflow sans service.  
  
### <a name="derive-a-class-from-workflowhostingendpoint"></a>Dériver une classe de WorkflowHostingEndpoint  
  
1.  Ajouter une nouvelle classe nommée `CreationEndpoint` dérivé <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> à la `Shared` projet.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Globalization;  
    using System.ServiceModel;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Channels;  
  
    namespace Shared  
    {  
        public class CreationEndpoint : WorkflowHostingEndpoint  
        {  
        }  
    }  
    ```  
  
2.  Ajoutez à la classe <xref:System.Uri> une variable `defaultBaseUri` statique locale appelée `CreationEndpoint`.  
  
    ```  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
    }  
    ```  
  
3.  Ajoutez le constructeur suivant à la classe `CreationEndpoint`. Notez que nous spécifions le contrat de service `IWorkflowCreation` dans l'appel au constructeur de base.  
  
    ```  
    public CreationEndpoint(Binding binding, EndpointAddress address)  
       : base(typeof(IWorkflowCreation), binding, address)  
       {  
       }  
    ```  
  
4.  Ajoutez le constructeur par défaut suivant à la classe `CreationEndpoint`.  
  
    ```  
    public CreationEndpoint()  
       : this(GetDefaultBinding(),  
       new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative))))  
       {  
       }  
    ```  
  
5.  Ajoutez une propriété `DefaultBaseUri` statique à la classe `CreationEndpoint`. Cette propriété permet de stocker un URI de base par défaut au cas où il n'en serait pas fourni.  
  
    ```  
    static Uri DefaultBaseUri  
    {  
       get  
       {  
          if (defaultBaseUri == null)  
          {  
             defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                Process.GetCurrentProcess().Id,  
                AppDomain.CurrentDomain.Id));  
          }  
          return defaultBaseUri;  
       }  
     }  
    ```  
  
6.  Créez la méthode suivante afin d'obtenir la liaison par défaut à utiliser pour le point de terminaison de création.  
  
    ```  
    //defaults to NetNamedPipeBinding  
    public static Binding GetDefaultBinding()  
    {  
       return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
    }  
    ```  
  
7.  Substituez la méthode <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> pour retourner l'ID de l'instance de workflow. Si le `Action` se termine d’en-tête par « Créer » renvoie un GUID vide, si le `Action` en-tête se termine par « createwithinstanceid », retournez le GUID passé à la méthode. Sinon, levez une exception <xref:System.InvalidOperationException>. Ces en-têtes `Action` correspondent aux deux opérations définies dans le contrat de service `IWorkflowCreation`.  
  
    ```  
    protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
    {  
       //Create was called by client  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
       {  
          return Guid.Empty;  
       }  
       //CreateWithInstanceId was called by client  
       else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
       {  
          return (Guid)inputs[1];  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
    }  
    ```  
  
8.  Substituez la méthode <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> pour créer un <xref:System.ServiceModel.Activities.WorkflowCreationContext> et ajoutez les arguments pour le workflow, envoyez l'ID de l'instance au client, puis retournez le <xref:System.ServiceModel.Activities.WorkflowCreationContext>.  
  
    ```  
    protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
    {  
       WorkflowCreationContext creationContext = new WorkflowCreationContext();  
       if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create") || (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId")))  
       {  
          Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
          if (arguments != null && arguments.Count > 0)  
          {  
             foreach (KeyValuePair<string, object> pair in arguments)  
             {  
                //arguments to pass to the workflow  
                creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
             }  
          }  
          //reply to client with instanceId  
          responseContext.SendResponse(instanceId, null);  
       }  
       else  
       {  
          throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
       }  
       return creationContext;  
    }  
    ```  
  
### <a name="create-a-standard-endpoint-element-to-allow-you-to-configure-the-workflowcreationendpoint"></a>Créer un élément de point de terminaison standard vous permettant de configurer WorkflowCreationEndpoint  
  
1.  Ajoutez au projet `CreationEndpoint` une référence à Shared.  
  
2.  Ajoutez au projet `CreationEndpointElement` une nouvelle classe nommée <xref:System.ServiceModel.Configuration.StandardEndpointElement>, dérivée de `CreationEndpoint`. Cette classe représente l'élément `CreationEndpoint` d'un fichier web.config.  
  
    ```  
    using System;  
    using System.Configuration;  
    using System.ServiceModel.Activities;  
    using System.ServiceModel.Configuration;  
    using System.ServiceModel.Description;  
    using Shared;  
  
    namespace CreationEndpointTest  
    {  
        //config element for CreationEndpoint  
        public class CreationEndpointElement : StandardEndpointElement  
        {  
       }  
    ```  
  
3.  Ajoutez une propriété appelée `EndpointType` pour retourner le type du point de terminaison.  
  
    ```  
    protected override Type EndpointType  
    {  
       get { return typeof(CreationEndpoint); }  
    }  
    ```  
  
4.  Substituez la méthode <xref:System.ServiceModel.Configuration.StandardEndpointElement.CreateServiceEndpoint%2A> et retournez un nouveau `CreationEndpoint`.  
  
    ```  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
    {  
       return new CreationEndpoint();  
    }  
    ```  
  
5.  Surchargez les méthodes <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnApplyConfiguration%2A>, <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A> et <xref:System.ServiceModel.Configuration.StandardEndpointElement.OnInitializeAndValidate%2A>. Ces méthodes ont seulement besoin d'être définies ; il n'est pas nécessaire de leur ajouter du code.  
  
    ```  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
    ```  
  
6.  Ajoutez la classe de collection de `CreationEndpoint` au fichier CreationEndpointElement.cs du projet `CreationEndpoint`. Cette classe est utilisée par la configuration pour stocker un certain nombre d'instances de `CreationEndpoint` dans un fichier web.config.  
  
    ```  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
    ```  
  
7.  Générez la solution.  
  
### <a name="host-the-workflow-in-iis"></a>Héberger le workflow dans IIS  
  
1.  Créez une application appelée `MyCreationEndpoint` dans IIS.  
  
2.  Copiez le fichier workflow1.xaml généré par le concepteur de workflow dans le répertoire de l'application et renommez-le workflow1.xamlx.  
  
3.  Copiez les fichiers shared.dll et CreationEndpoint.dll dans le répertoire bin de l'application (créez le répertoire bin s'il n'existe pas).  
  
4.  Remplacez le contenu du fichier Web.config du projet `CreationEndpoint` par le code suivant.  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.web>  
        <compilation debug="true" targetFramework="4.0" />  
      </system.web>   
    </configuration>  
    ```  
  
5.  Après l'élément `<system.web>`, inscrivez `CreationEndpoint` en ajoutant le code de configuration suivant.  
  
    ```xml  
    <system.serviceModel>  
        <!--register CreationEndpoint-->  
        <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
        <extensions>  
          <endpointExtensions>  
            <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, CreationEndpoint, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </endpointExtensions>  
        </extensions>  
    </system.serviceModel>  
    ```  
  
     Cela inscrit la classe `CreationEndpointCollection` pour vous permettre de configurer un `CreationEndpoint` dans un fichier web.config.  
  
6.  Ajouter un `<service>` élément (une fois la \</extensions > balise) avec un `CreationEndpoint` qui écoutera les messages entrants.  
  
    ```xml  
    <services>  
          <!-- add endpoint to service-->  
          <service name="Workflow1" behaviorConfiguration="basicConfig" >  
            <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
          </service>  
        </services>  
    ```  
  
7.  Ajouter un \<comportements > élément (une fois la  \< /services > balise) pour activer les métadonnées de service.  
  
    ```xml  
    <behaviors>  
          <serviceBehaviors>  
            <behavior name="basicConfig">  
              <serviceMetadata httpGetEnabled="true" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
    ```  
  
8.  Copiez le fichier web.config dans le répertoire de votre application IIS.  
  
9. Vérifiez si le point de terminaison de création fonctionne en démarrant Internet Explorer et en accédant à http://localhost/MyCreationEndpoint/Workflow1.xamlx. Internet Explorer doit afficher l'écran suivant :  
  
     ![Test du service](../../../../docs/framework/wcf/feature-details/media/testservice.gif "TestService")  
  
### <a name="create-a-client-that-will-call-the-creationendpoint"></a>Créer un client qui appellera CreationEndpoint  
  
1.  Ajoutez à la solution `CreationEndpointTest` une nouvelle application Console.  
  
2.  Ajoutez des références à System.ServiceModel.dll, à System.ServiceModel.Activities et au projet `Shared`.  
  
3.  Dans le `Main` méthode créer un <xref:System.ServiceModel.ChannelFactory%601> de type `IWorkflowCreation` et appelez <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Un proxy sera retourné. Vous pourrez alors appeler `Create` sur ce proxy pour créer l'instance de workflow hébergée sous IIS :  
  
    ```  
    using System.Text;  
    using Shared;  
    using System.ServiceModel;  
  
    namespace CreationEndpointClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                try  
                {  
                    //client using BasicHttpBinding  
                    IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/CreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                    Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                    Console.WriteLine("Press return to exit ...");  
                    Console.ReadLine();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine(ex);  
                    Console.ReadLine();  
                }  
            }  
        }  
    }  
    ```  
  
4.  Exécutez CreationEndpointClient. La sortie doit se présenter comme suit :  
  
    ```Output  
    Workflow Instance created using CreationEndpoint added in config. Instance Id: 0875dac0-2b8b-473e-b3cc-abcb235e9693Press return to exit ...  
    ```  
  
    > [!NOTE]
    >  Vous ne verrez pas la sortie du workflow, car il s'exécute sous IIS, qui n'a pas de sortie de console.  
  
## <a name="example"></a>Exemple  
 Voici le code complet de cet exemple.  
  
```xaml  
<!-— workflow1.xamlx -->  
<WorkflowService mc:Ignorable="sap"   
                 ConfigurationName="Workflow1"   
                 sap:VirtualizedContainerService.HintSize="263,230"   
                 Name="Workflow1"   
                 mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces"   
                 xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"   
                 xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
                 xmlns:mv="clr-namespace:Microsoft.VisualBasic;assembly=System"   
                 xmlns:mva="clr-namespace:Microsoft.VisualBasic.Activities;assembly=System.Activities"   
                 xmlns:p="http://schemas.microsoft.com/netfx/2009/xaml/activities"   
                 xmlns:s="clr-namespace:System;assembly=mscorlib"   
                 xmlns:s1="clr-namespace:System;assembly=System"   
                 xmlns:s2="clr-namespace:System;assembly=System.Xml"   
                 xmlns:s3="clr-namespace:System;assembly=System.Core"   
                 xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities"   
                 xmlns:sap="http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation"   
                 xmlns:scg="clr-namespace:System.Collections.Generic;assembly=System"   
                 xmlns:scg1="clr-namespace:System.Collections.Generic;assembly=System.ServiceModel"   
                 xmlns:scg2="clr-namespace:System.Collections.Generic;assembly=System.Core"   
                 xmlns:scg3="clr-namespace:System.Collections.Generic;assembly=mscorlib"   
                 xmlns:sd="clr-namespace:System.Data;assembly=System.Data"   
                 xmlns:sl="clr-namespace:System.Linq;assembly=System.Core"   
                 xmlns:st="clr-namespace:System.Text;assembly=mscorlib"   
                 xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <p:Sequence DisplayName="Sequential Service"   
              sad:XamlDebuggerXmlReader.FileName="c:\projects\CreationEndpointTest\CreationEndpoint\Service1.xamlx"   
              sap:VirtualizedContainerService.HintSize="233,200"   
              mva:VisualBasic.Settings="Assembly references and imported namespaces serialized as XML namespaces">  
    <p:Sequence.Variables>  
      <p:Variable x:TypeArguments="CorrelationHandle" Name="handle" />  
      <p:Variable x:TypeArguments="x:Int32" Name="data" />  
    </p:Sequence.Variables>  
    <sap:WorkflowViewStateService.ViewState>  
      <scg3:Dictionary x:TypeArguments="x:String, x:Object">  
        <x:Boolean x:Key="IsExpanded">True</x:Boolean>  
      </scg3:Dictionary>  
    </sap:WorkflowViewStateService.ViewState>  
    <p:WriteLine sap:VirtualizedContainerService.HintSize="211,61" Text="Hello, world" />  
  </p:Sequence>  
</WorkflowService>  
```  
  
```csharp  
// CreationEndpointElement.cs  
using System;  
using System.Configuration;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Description;  
using Shared;  
  
namespace CreationEndpointTest  
{  
    //config element for CreationEndpoint  
    public class CreationEndpointElement : StandardEndpointElement  
    {  
        protected override Type EndpointType  
        {  
            get { return typeof(CreationEndpoint); }  
        }  
  
        protected override ConfigurationPropertyCollection Properties  
        {  
            get  
            {  
                ConfigurationPropertyCollection properties = base.Properties;  
                properties.Add(new ConfigurationProperty("name", typeof(String), null, ConfigurationPropertyOptions.IsRequired));  
                return properties;  
            }  
        }  
  
        protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contractDescription)  
        {  
            return new CreationEndpoint();  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
        {  
        }  
  
        protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
        {  
        }  
    }  
  
    public class CreationEndpointCollection : StandardEndpointCollectionElement<CreationEndpoint, CreationEndpointElement>  
    {  
    }  
}  
```  
  
```xml  
<!-- web.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <!--register CreationEndpoint-->  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
    <extensions>  
      <endpointExtensions>  
        <add name="creationEndpoint" type="CreationEndpointTest.CreationEndpointCollection, Shared, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <!-- add endpoint to service-->  
      <service name="Workflow1" behaviorConfiguration="basicConfig" >  
        <endpoint kind="creationEndpoint" binding="basicHttpBinding" address=""/>  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="basicConfig">  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```csharp  
// IWorkflowCreation.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
  
namespace Shared  
{  
    //service contract exposed from the endpoint  
    [ServiceContract(Name = "IWorkflowCreation")]  
    public interface IWorkflowCreation  
    {  
        [OperationContract(Name = "Create")]  
        Guid Create(IDictionary<string, object> inputs);  
  
        [OperationContract(Name = "CreateWithInstanceId", IsOneWay = true)]  
        void CreateWithInstanceId(IDictionary<string, object> inputs, Guid instanceId);  
    }  
}  
```  
  
```csharp  
// CreationEndpoint.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel.Activities;  
using System.ServiceModel.Channels;  
using System.ServiceModel;  
using System.Globalization;  
using System.Diagnostics;  
  
namespace Shared  
{  
    public class CreationEndpoint : WorkflowHostingEndpoint  
    {  
        static Uri defaultBaseUri;  
  
        public CreationEndpoint(Binding binding, EndpointAddress address)  
            : base(typeof(IWorkflowCreation), binding, address) { }  
  
        public CreationEndpoint()  
            : this(GetDefaultBinding(),  
                new EndpointAddress(new Uri(DefaultBaseUri, new Uri(Guid.NewGuid().ToString(), UriKind.Relative)))) { }  
  
        static Uri DefaultBaseUri  
        {  
            get  
            {  
                if (defaultBaseUri == null)  
                {  
                    defaultBaseUri = new Uri(string.Format(CultureInfo.InvariantCulture, "net.pipe://localhost/workflowCreationEndpoint/{0}/{1}",  
                        Process.GetCurrentProcess().Id,  
                        AppDomain.CurrentDomain.Id));  
                }  
                return defaultBaseUri;  
            }  
        }  
  
        //defaults to NetNamedPipeBinding  
        public static Binding GetDefaultBinding()  
        {  
            return new NetNamedPipeBinding(NetNamedPipeSecurityMode.None) { TransactionFlow = true };  
        }  
  
        protected override Guid OnGetInstanceId(object[] inputs, OperationContext operationContext)  
        {  
            //Create was called by client  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                return Guid.Empty;  
            }  
  
            //CreateWithInstanceId was called by client  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                return (Guid)inputs[1];  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
        }  
  
        protected override WorkflowCreationContext OnGetCreationContext(object[] inputs, OperationContext operationContext, Guid instanceId, WorkflowHostingResponseContext responseContext)  
        {  
            WorkflowCreationContext creationContext = new WorkflowCreationContext();  
            if (operationContext.IncomingMessageHeaders.Action.EndsWith("Create"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to the workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
                //reply to client with instanceId  
                responseContext.SendResponse(instanceId, null);  
            }  
            else if (operationContext.IncomingMessageHeaders.Action.EndsWith("CreateWithInstanceId"))  
            {  
                Dictionary<string, object> arguments = (Dictionary<string, object>)inputs[0];  
                if (arguments != null && arguments.Count > 0)  
                {  
                    foreach (KeyValuePair<string, object> pair in arguments)  
                    {  
                        //arguments to pass to workflow  
                        creationContext.WorkflowArguments.Add(pair.Key, pair.Value);  
                    }  
                }  
            }  
            else  
            {  
                throw new InvalidOperationException("Invalid Action: " + operationContext.IncomingMessageHeaders.Action);  
            }  
            return creationContext;  
        }  
    }  
}  
```  
  
```csharp  
// CreationEndpointClient.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Shared;  
using System.ServiceModel;  
  
namespace CreationClient  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                //client using BasicHttpBinding  
                IWorkflowCreation client = new ChannelFactory<IWorkflowCreation>(new BasicHttpBinding(), new EndpointAddress("http://localhost/MyCreationEndpoint/Workflow1.xamlx")).CreateChannel();  
  
                Console.WriteLine("Workflow Instance created using CreationEndpoint added in config. Instance Id: {0}", client.Create(null));  
                Console.WriteLine("Press return to exit ...");  
                Console.ReadLine();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex);  
                Console.ReadLine();  
            }  
  
        }  
    }  
  
}  
```  
  
 Cet exemple peut sembler déroutant, parce que vous n'y implémentez pas de service qui implémente `IWorkflowCreation`. La raison en est que `CreationEndpoint` le fait pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hébergement dans les services IIS (Internet Information Services)](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [Bonnes pratiques pour l’hébergement dans Internet Information Services](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Instructions relatives à l’hébergement dans Internet Information Services](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [Architecture de Windows Workflow](../../../../docs/framework/windows-workflow-foundation/architecture.md)  
 [Reprise de signet WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)  
 [Réhébergement du concepteur de flux de travail](../../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Vue d’ensemble de Windows Workflow](../../../../docs/framework/windows-workflow-foundation/overview.md)
