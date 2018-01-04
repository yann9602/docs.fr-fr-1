---
title: Self-Host
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b662c034e4c3d7c21c9a48537cd7f80f4bb6b659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="self-host"></a>Self-Host
Cet exemple montre comment implémenter un service auto-hébergé dans une application console. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md). Le fichier de configuration de service Web.config a été renommé App.config et modifié pour configurer une adresse de base que l'hôte utilise. Le code source du service a été modifié pour implémenter une fonction `Main` statique qui crée et ouvre un hôte de service qui fournit l'adresse de base configurée. L'implémentation du service a été modifiée pour écrire la sortie dans la console à chaque opération. Le client n'a été pas modifié, excepté pour configurer l'adresse de point de terminaison correcte du service.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
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
  
 Lorsqu'un service est hébergé par IIS (Internet Information Services) ou WAS (Windows Process Activation Service), l'adresse de base du service est fournie par l'environnement d'hébergement. En cas d'auto-hébergement, vous devez spécifier l'adresse de base vous-même. Cette opération est effectuée à l’aide de la `add` élément, enfant de [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), enfant de [ \<hôte >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), enfant de [ \<service > ](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) comme illustré dans l’exemple de configuration suivantes.  
  
```xml  
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
  
 Lorsque vous exécutez l'exemple, les requêtes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
