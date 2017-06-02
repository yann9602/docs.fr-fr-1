---
title: "Typed Client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62c40e8f-e9b4-4b1a-939a-93c37393d343
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# Typed Client
Cet exemple montre comment obtenir des informations à partir d'un client typé généré par [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.Dans cet exemple, le client est une application console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La propriété `Endpoint` du client permet d'accéder aux informations sur le point de terminaison de service avec lequel le client communique, et notamment aux informations d'adresse, de liaison et de contrat.La propriété `InnerChannel` du client est une instance de <xref:System.ServiceModel.IClientChannel> qui permet d'accéder aux informations sur le canal sous\-jacent, tel que son identificateur d'état et de session.  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
...  
Console.WriteLine("Client - endpoint:  " + client.Endpoint.Address);  
Console.WriteLine("Client - binding:  " + client.Endpoint.Binding.Name);  
Console.WriteLine("Client - contract: " + client.Endpoint.Contract.Name);  
  
IClientChannel channel = client.InnerChannel;  
Console.WriteLine("Client channel - state: " + channel.State);  
Console.WriteLine("Client channel - session identifier: " + channel.SessionId);  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.Appuyez sur ENTER dans la fenêtre du client pour arrêter le client.  
  
```  
  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Client - endpoint:  http://localhost/servicemodelsamples/service.svc  
Client - binding:  WSHttpBinding  
Client - contract: ICalculator  
Client channel - state: Opened  
Client channel - session identifier: urn:uuid:ae16fbc4-2964-4e87-9fb1-c5aa78fc567e  
  
Press <ENTER> to terminate client.  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Client\TypedClient`  
  
## Voir aussi