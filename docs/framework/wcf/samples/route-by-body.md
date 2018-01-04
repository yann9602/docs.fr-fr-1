---
title: Route by Body
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: defd3a3e9df273739aaf3440fd34fad2cad44cd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="route-by-body"></a>Route by Body
Cet exemple montre comment implémenter un service qui accepte des objets de message avec toute action SOAP. Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice. Le service implémente une opération `Calculate` unique qui accepte un paramètre de demande <xref:System.ServiceModel.Channels.Message> et retourne une réponse <xref:System.ServiceModel.Channels.Message>.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé dans IIS.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple illustre la distribution des messages selon le contenu du corps. Le modèle de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] intégré de distribution des messages est basé sur les actions de message. Toutefois, il existe de nombreux services Web qui définissent toutes leurs opérations avec l'action="". Il est impossible de générer un service reposant sur WSDL qui continue à distribuer des messages de demande selon les informations d'action. Cet exemple montre un contrat de service basé sur WSDL (WSDL est contenu dans Service.wsdl, lui-même inclus dans l'exemple). Le contrat de service est la Calculatrice, similaire à celui utilisé dans [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md). Toutefois, le `[OperationContract]` spécifie `Action=""` pour toutes les opérations.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Selon le contrat, le service requiert le comportement de distribution personnalisé `DispatchByBodyBehavior` pour autoriser les messages à être distribués entre des opérations. Ce comportement de distribution initialise le `DispatchByBodyElementOperationSelector` sélecteur d’opération personnalisé avec un tableau des noms d’opération indexés par le QName des éléments wrapper respectifs. `DispatchByBodyElementOperationSelector` examine la balise de début du premier enfant du corps et sélectionne l'opération à l'aide du tableau mentionné précédemment.  
  
 Le client utilise un proxy généré automatiquement à partir du WSDL exporté par le service à l’aide de [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Le fait que les actions de toutes les opérations soient vides n'a aucun impact sur le code client, à l'exception des paramètres d'action du proxy généré automatiquement.  
  
 Le code client effectue plusieurs calculs. Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>Voir aussi
