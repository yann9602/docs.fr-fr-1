---
title: "Demande-réponse non typé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45e68bd28a4ab5a0e7425bf06b02b8c3d3d25311
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="untyped-requestreply"></a>Untyped Request/Reply
Cet exemple montre comment définir des contrats d'opération qui utilisent la classe Message.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md). Le contrat de service définit une opération qui prend un type de message comme argument et retourne un message. L'opération recueille toutes les données requises pour calculer la somme du corps du message puis envoie la somme dans le corps du message de retour.  
  
```  
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Sur le service, l'opération récupère le tableau d'entiers passé dans le message d'entrée puis calcule la somme. Pour envoyer un message de réponse, l'exemple crée un nouveau message avec la version de message et l'action appropriées et inclut la somme calculée dans son corps. C'est ce que montre l'exemple de code suivant.  
  
```  
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be   
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,   
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 Le client utilise le code généré par [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un proxy pour le service distant. Pour envoyer un message de demande, le client doit connaître la version du message, qui dépend du canal sous-jacent. Donc, il crée une <xref:System.ServiceModel.OperationContextScope> étendue au canal proxy qu'il a créé, ce qui crée un <xref:System.ServiceModel.OperationContext> avec la version de message correcte indiquée à la propriété `OutgoingMessageHeaders.MessageVersion`. Le client passe un tableau d'entrées dans le corps du message de demande puis appelle `ComputeSum` sur le proxy. Le client récupère ensuite la somme des entrées qu'il a passées en accédant à la méthode `GetBody<T>` depuis le message de réponse. C'est ce que montre l'exemple de code suivant.  
  
```  
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,   
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",   
                                                       response);  
}  
```  
  
 Cet exemple est un exemple hébergé sur le Web donc seul le fichier exécutable client doit être exécuté. L'exemple suivant illustre la sortie sur le client.  
  
```  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Cet exemple est un exemple hébergé sur le Web : suivez le lien fourni à l'étape 3 pour voir comment générer et exécuter l'exemple.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
  
## <a name="see-also"></a>Voir aussi
