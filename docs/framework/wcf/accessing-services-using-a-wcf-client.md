---
title: "Acc&#232;s aux services &#224; l&#39;aide d&#39;un client WCF | Microsoft Docs"
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
  - "clients (WCF), consommation de services"
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# Acc&#232;s aux services &#224; l&#39;aide d&#39;un client WCF
Après la création d'un service, l'étape suivante consiste à créer un proxy client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  Une application cliente utilise le proxy client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pour communiquer avec le service.  En général, les applications clientes importent les métadonnées d'un service pour générer le code client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] qui permet d'appeler le service.  
  
 Les principales étapes pour créer un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sont les suivantes :  
  
1.  Compiler le code de service.  
  
2.  Générez le proxy client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
3.  Instanciez le proxy client WCF.  
  
 Le proxy client WCF peut être généré manuellement à l'aide de l'outil Service Model Metadata Utility Tool \(SvcUtil.exe\). Pour plus d'informations, consultez [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  Le proxy client WCF peut également être généré dans Visual Studio à l'aide de la fonctionnalité Ajouter une référence de service.  Pour générer le proxy client WCF à l'aide de l'une de ces méthodes, le service doit s'exécuter.  Si le service est auto\-hébergé, vous devez exécuter l'hôte.  Si le service est hébergé dans IIS\/WAS, aucune action n'est nécessaire.  
  
## Outil Service Model Metadata Tool  
 L'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) est un outil de ligne de commande qui permet de générer du code à partir de métadonnées.  Voici un exemple d'utilisation d'une commande Svcutil.exe de base.  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 Vous pouvez également utiliser Svcutil.exe avec des fichiers WSDL \(Web Services Description Language\) et XSD \(XML Schema Definition\) sur le système de fichiers.  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 Le résultat est un fichier de code qui contient le code client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] que l'application cliente peut utiliser pour appeler le service.  
  
 L'outil permet également de générer des fichiers de configuration.  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 Si un seul nom de fichier est fourni, il s'agit du nom du fichier de sortie.  Si deux noms de fichiers sont fournis, le premier est un fichier de configuration d'entrée dont le contenu est fusionné avec la configuration générée et écrit dans le deuxième fichier.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] la configuration, consultez [Configuration de liaisons pour les services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Les demandes de métadonnées non sécurisées représentent certains risques comme toute demande réseau non sécurisée. Si vous n'êtes pas certain de l'identité du point de terminaison avec lequel vous communiquez, il est possible que les informations que vous récupérez soient des métadonnées provenant d'un service malveillant.  
  
## Ajouter une référence de service dans Visual Studio  
 Lorsque le service est en cours d'exécution, cliquez avec le bouton droit sur le projet qui contient le proxy client WCF et sélectionnez **Ajouter une référence de service**.  Dans la boîte de dialogue **Ajouter une référence de service**, tapez l'URL du service que vous souhaitez appeler et cliquez sur le bouton **Aller à**.  La boîte de dialogue affiche une liste de services disponibles à l'adresse que vous spécifiez.  Double\-cliquez sur le service pour afficher les contrats et les opérations disponibles, spécifiez un espace de noms pour le code généré et cliquez sur le bouton **OK**.  
  
## Exemple  
 L'exemple de code suivant montre un contrat de service créé pour un service.  
  
```csharp  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    // Other methods are not shown here.  
}  
```  
  
```vb  
' Define a service contract.  
<ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")> _  
Public Interface ICalculator  
    <OperationContract()>  _  
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double   
    ' Other methods are not shown here.  
End Interface   
```  
  
 L'utilitaire de métadonnées ServiceModel et Ajouter une référence de service dans Visual Studio génèrent la classe cliente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] suivante.  La classe hérite de la classe générique <xref:System.ServiceModel.ClientBase%601> et implémente l'interface `ICalculator`.  L'outil génère également l'interface `ICalculator` \(qui n'est pas présentée ici\).  
  
```csharp  
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator  
{  
    public CalculatorClient(){}  
  
    public CalculatorClient(string configurationName) :   
            base(configurationName)  
    {}  
  
    public CalculatorClient(System.ServiceModel.Binding binding) :   
            base(binding)  
    {}  
  
    public CalculatorClient(System.ServiceModel.EndpointAddress address,  
    System.ServiceModel.Binding binding) :   
            base(address, binding)  
    {}  
  
    public double Add(double n1, double n2)  
    {  
        return base.InnerChannel.Add(n1, n2);  
    }  
}  
  
```  
  
```vb  
Partial Public Class CalculatorClient  
    Inherits System.ServiceModel.ClientBase(Of ICalculator)  
    Implements ICalculator  
  
    Public Sub New()  
        MyBase.New  
    End Sub  
  
    Public Sub New(ByVal configurationName As String)  
        MyBase.New(configurationName)  
    End Sub  
  
    Public Sub New(ByVal binding As System.ServiceModel.Binding)  
        MyBase.New(binding)  
    End Sub  
  
    Public Sub New(ByVal address As _  
    System.ServiceModel.EndpointAddress, _  
    ByVal binding As System.ServiceModel.Binding)  
        MyBase.New(address, binding)  
    End Sub  
  
    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As _  
    Double Implements ICalculator.Add  
        Return MyBase.InnerChannel.Add(n1, n2)  
    End Function   
End Class  
  
```  
  
## Utilisation du client WCF  
 Pour utiliser le client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], créez une instance du client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], puis appelez ses méthodes, tel qu'indiqué dans le code suivant.  
  
```csharp  
// Create a client object with the given client endpoint configuration.  
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = calcClient.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
```  
  
```vb  
' Create a client object with the given client endpoint configuration.  
Dim calcClient As CalculatorClient = _  
New CalculatorClient("CalculatorEndpoint")  
  
' Call the Add service operation.  
Dim value1 As Double = 100.00D  
Dim value2 As Double = 15.99D  
Dim result As Double = calcClient.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
```  
  
## Débogage d'exceptions levées par un Client  
 De nombreuses exceptions levées par un client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sont provoquées par une exception sur le service.  En voici quelques exemples :  
  
-   <xref:System.Net.Sockets.SocketException> : une connexion existante a été arrêtée de force par l'hôte distant.  
  
-   <xref:System.ServiceModel.CommunicationException> : la connexion sous\-jacente s'est arrêtée de façon inattendue.  
  
-   <xref:System.ServiceModel.CommunicationObjectAbortedException> : la connexion de socket a été abandonnée.  Cela peut être dû à une erreur lors du traitement de votre message, l'expiration du délai de réception par l'hôte distant ou un problème de ressource sur le réseau sous\-jacent.  
  
 Lorsque ces types d'exceptions se produisent, le meilleur moyen de les résoudre consiste à activer le suivi du côté service et de déterminer l'exception qui s'y est produite.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] le suivi, consultez [Suivi](../../../docs/framework/wcf/diagnostics/tracing/index.md) et [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## Voir aussi  
 [Comment : créer un client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [Comment : accéder aux services ayant un contrat duplex](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [Comment : appeler des opérations de service de façon asynchrone](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)   
 [Comment : accéder aux services avec des contrats unidirectionnels et demande\-réponse](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)   
 [Comment : accéder à un service WSE 3.0](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)   
 [Fonctionnement du code client généré](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)   
 [Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)   
 [Spécification du comportement du client au moment de l'exécution](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)   
 [Configuration des comportements clients](../../../docs/framework/wcf/configuring-client-behaviors.md)