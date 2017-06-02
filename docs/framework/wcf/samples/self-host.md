---
title: "Self-Host | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "Self Host (exemple) (Windows Communication Foundation)"
  - "service auto-hébergé"
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
caps.latest.revision: 38
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 38
---
# Self-Host
Cet exemple montre comment implémenter un service auto\-hébergé dans une application console.Il est basé sur l'[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).Le fichier de configuration de service Web.config a été renommé App.config et modifié pour configurer une adresse de base que l'hôte utilise.Le code source du service a été modifié pour implémenter une fonction `Main` statique qui crée et ouvre un hôte de service qui fournit l'adresse de base configurée.L'implémentation du service a été modifiée pour écrire la sortie dans la console à chaque opération.Le client n'a été pas modifié, excepté pour configurer l'adresse de point de terminaison correcte du service.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.  
  
 L'exemple implémente une fonction principale statique pour créer un <xref:System.ServiceModel.ServiceHost> pour le type `CalculatorService` donné, comme le montre l'exemple de code suivant.  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
  
```  
  
 Lorsqu'un service est hébergé par IIS \(Internet Information Services\) ou WAS \(Windows Process Activation Service\), l'adresse de base du service est fournie par l'environnement d'hébergement.En cas d'auto\-hébergement, vous devez spécifier l'adresse de base vous\-même.Cela se fait à l'aide de l'élément `add`, enfant de [\<baseAddresses\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), enfant de [\<hôte\>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), enfant de [\<service\>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) comme cela est indiqué dans l'exemple de configuration suivant.  
  
```  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses de l'opération sont affichées dans les fenêtres de console du service et du client.Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## Voir aussi  
 [Hébergement AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)