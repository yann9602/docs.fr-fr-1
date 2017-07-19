---
title: "Vue d&#39;ensemble de la cr&#233;ation de points de terminaison | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "points de terminaison (WCF), vue d'ensemble"
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# Vue d&#39;ensemble de la cr&#233;ation de points de terminaison
Toute communication avec un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] se produit par l'intermédiaire des *points de terminaison* du service.  Les points de terminaison fournissent aux clients l'accès aux fonctionnalités offertes par un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Cette section décrit la structure d'un point de terminaison et explique comment définir un point de terminaison dans la configuration et dans le code.  
  
## Structure d'un point de terminaison  
 Chaque point de terminaison contient une adresse qui indique où rechercher le point de terminaison, une liaison qui spécifie le mode de communication d'un client avec le point de terminaison, et un contrat qui identifie les méthodes disponibles.  
  
-   **Adresse**.  L'adresse identifie le point de terminaison de manière unique et indique aux consommateurs potentiels l'emplacement du service.  Elle est représentée dans le modèle objet [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] par l'adresse <xref:System.ServiceModel.EndpointAddress> qui contient un URI \(Uniform Resource Identifier\) et les propriétés d'adresse qui incluent une identité, certains éléments WSDL \(Web Services Description Language\) et une collection d'en\-têtes facultatifs.  Les en\-têtes facultatifs fournissent des données d'adressage détaillées supplémentaires pour identifier ou interagir avec le point de terminaison.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Spécification d'une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Liaison**.  La liaison spécifie le mode de communication avec le point de terminaison.  La liaison spécifie comment le point de terminaison communique avec le monde, y compris quel protocole de transport utiliser \(par exemple, TCP ou HTTP\), quel encodage utiliser pour les messages \(par exemple, texte ou binaire\), et quelles conditions de sécurité sont nécessaires \(par exemple, SSL \[Secure Sockets Layer\] ou la sécurité des messages SOAP\).  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Contrat de service**.  Le contrat de service définit les fonctionnalités que le point de terminaison expose au client.  Un contrat spécifie les opérations qu'un client peut appeler, la forme du message et le type de paramètres d'entrée ou de données requis pour appeler l'opération, ainsi que le type du traitement ou le message de réponse auquel le client peut s'attendre.  Trois types de contrats de base correspondent aux modèles d'échange de messages \(MEPs, message exchange patterns\) de base : datagramme \(unidirectionnel\), demande\/réponse et duplex \(bidirectionnel\).  Le contrat de service peut aussi employer des contrats de données et de message pour requérir des types de données spécifiques et des formats de message lors de son accès.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] la définition d'un contrat de service, consultez [Conception de contrats de service](../../../docs/framework/wcf/designing-service-contracts.md).  Notez qu'un client peut aussi devoir implémenter un contrat défini par le service, appelé un contrat de rappel, pour recevoir des messages du service dans un MEP duplex.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Services duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Le point de terminaison pour un service peut être spécifié de manière impérative en utilisant le code ou de façon déclarative par la configuration.  Si aucun point de terminaison n'est spécifié, le runtime fournit les points de terminaison par défaut en ajoutant un point de terminaison par défaut pour chaque adresse de base pour chaque contrat de service implémenté par le service.  La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.  En général, il est plus pratique de définir des points de terminaison de service à l'aide de la configuration plutôt que du code.  Le fait de conserver les informations de liaison et d'adressage hors du code leur permet de changer sans devoir recompiler ou de redéployer l'application.  
  
> [!NOTE]
>  Lorsque vous ajoutez un point de terminaison de service qui effectue un emprunt d'identité, vous devez utiliser une des méthodes <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> ou la méthode <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> pour charger correctement le contrat dans un nouvel objet <xref:System.ServiceModel.Description.ServiceDescription>.  
  
## Définition de points de terminaison dans le code  
 L'exemple suivant illustre comment spécifier un point de terminaison dans le code avec les éléments suivants :  
  
-   Définissez un contrat pour un type de service `IEcho` qui accepte le nom d'un tiers et renvoie la réponse "Hello \<nom\>\!".  
  
-   Implémentez un service `Echo` du type défini par le contrat `IEcho`.  
  
-   Spécifiez une adresse de point de terminaison http:\/\/localhost:8000\/Echo pour le service.  
  
-   Configurez le service `Echo` à l'aide d'une liaison <xref:System.ServiceModel.WSHttpBinding>.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  L'hôte de service est créé avec une adresse de base, puis le reste de l'adresse, relatif à l'adresse de base, est spécifié dans le cadre d'un point de terminaison.  Ce partitionnement de l'adresse permet de définir plus simplement plusieurs points de terminaison pour les services à un hôte.  
  
> [!NOTE]
>  Les propriétés de <xref:System.ServiceModel.Description.ServiceDescription> dans l'application de service ne doivent pas être modifiées à l'issue de la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ServiceHostBase>.  Certains membres, tels que la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> et les méthodes `AddServiceEndpoint` sur <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.ServiceHost>, lèvent une exception s'ils sont modifiés au\-delà de ce point.  D'autres membres peuvent être modifiés, mais le résultat n'est pas défini.  
>   
>  De la même façon, sur le client les valeurs <xref:System.ServiceModel.Description.ServiceEndpoint> ne doivent pas être modifiées après l'appel à <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ChannelFactory>.  La propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> lève une exception si elle est modifiée au\-delà de ce point.  Les autres valeurs de description du client peuvent être modifiées sans erreur, mais le résultat n'est pas défini.  
>   
>  Aussi bien pour le service que le client, il est recommandé de modifier la description avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## Définition de points de terminaison dans la configuration  
 Lorsque vous créez une application, vous souhaitez souvent remettre des décisions à l'administrateur chargé de son déploiement.  Par exemple, il est souvent impossible de déterminer à l'avance à quoi correspond une adresse de service \(URI\).  Au lieu de d'encoder de manière irréversible une adresse, il est préférable de permettre à un administrateur de le faire après avoir créé un service.  Cette souplesse est obtenue par le biais de la configuration.  Pour plus d'informations, consultez [Configuration des services](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Utilisez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) avec le commutateur `/config:`*filename* `[,`*filename*`]` pour créer des fichiers de configuration rapidement.  
  
## Utilisation des points de terminaison par défaut  
 Si aucun point de terminaison n'est spécifié dans le code ou dans la configuration, le runtime fournit les points de terminaison par défaut en ajoutant un point de terminaison par défaut pour chaque adresse de base pour chaque contrat de service implémenté par le service.  L'adresse de base peut être spécifiée dans le code ou dans la configuration, et les points de terminaison par défaut sont ajoutés lors de l'appel de <xref:System.ServiceModel.ServiceHost.Open%2A> sur le <xref:System.ServiceModel.ServiceHost>.  Cet exemple est le même que celui de la section précédente, mais, étant donné qu'aucun point de terminaison n'est spécifié, les points de terminaison par défaut sont ajoutés.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 Si des points de terminaison sont fournis explicitement, les points de terminaison par défaut peuvent toujours être ajoutés en appelant <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sur le <xref:System.ServiceModel.ServiceHost> avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] les points de terminaison par défaut, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## Voir aussi  
 [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)