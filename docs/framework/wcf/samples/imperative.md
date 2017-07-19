---
title: "Imperative | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f7ce807-c0e4-407a-92a6-22abafb40b51
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Imperative
Cet exemple montre comment définir <xref:System.ServiceModel.WsHttpBinding> pour un service à l'aide du code, au lieu de définir la liaison `wsHttpBinding` dans la configuration.Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le code suivant montre comment définir une liaison dans le code de façon impérative.  
  
```  
public static void Main()  
{  
    WSHttpBinding binding = new WSHttpBinding();  
    binding.Name = "binding1";  
    binding.HostNameComparisonMode =  
        HostNameComparisonMode.StrongWildcard;  
    binding.Security.Mode = SecurityMode.Message;  
    binding.ReliableSession.Enabled = false;  
    binding.TransactionFlow = false;  
  
    Uri baseAddress =   
        new Uri("http://localhost:8000/servicemodelsamples/service");  
  
    // Create a ServiceHost for the CalculatorService type and provide the base address.  
    using(ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
    {  
        serviceHost.AddServiceEndpoint(typeof(ICalculator),   
                                       binding, baseAddress);  
        // Open the ServiceHostBase to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
        // Close the ServiceHostBase to shutdown the service.  
        serviceHost.Close();                        
    }             
}  
  
```  
  
 Le client crée un canal pour communiquer avec le service, tel qu'indiqué dans l'exemple de code suivant.  
  
```  
WSHttpBinding binding = new WSHttpBinding();  
binding.Name = "binding1";  
binding.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
binding.Security.Mode = SecurityMode.Message;  
binding.ReliableSession.Enabled = false;  
binding.TransactionFlow = false;  
  
String url = "http://localhost:8000/servicemodelsamples/service";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding,address);  
ICalculator channel = channelFactory.CreateChannel();  
  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur le bouton ENTER de la fenêtre du client pour l'arrêter.  
  
```  
  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans la rubrique [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Imperative`  
  
## Voir aussi