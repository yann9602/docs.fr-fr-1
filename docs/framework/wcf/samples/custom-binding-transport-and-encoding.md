---
title: Custom Binding Transport and Encoding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82db4ec7dfd1dd10837f2b2424615f8afbe81932
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-binding-transport-and-encoding"></a>Custom Binding Transport and Encoding
Une liaison personnalisée est définie par une liste ordonnée d’éléments de liaison discrets. Cet exemple montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d’encodage de message.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur le [auto-hébergement](../../../../docs/framework/wcf/samples/self-host.md)et a été modifié pour configurer les trois points de terminaison pour prendre en charge les transports HTTP, TCP et NamedPipe avec des liaisons personnalisées. La configuration client a été modifiée de la même façon, et le code client a été modifié pour communiquer avec chacun des trois points de terminaison.  
  
 L'exemple montre comment configurer une liaison personnalisée qui prend en charge un transport et un encodage de message spécifiques. Pour ce faire, configurez un transport et un encodage de message pour l'élément `binding`. Le classement des éléments de liaison est important pour définir une liaison personnalisée, car chacun représente une couche dans la pile de canaux (voir [des liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)). Cet exemple configure trois liaisons personnalisées : un transport HTTP avec encodage texte, un transport TCP avec encodage texte et un transport NamedPipe avec encodage binaire.  
  
 La configuration du service définit les liaisons personnalisées comme suit :  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Le client communique avec chacun des trois points de terminaison, en accédant d'abord à HTTP, puis à TCP et enfin à NamedPipe. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
 La liaison `namedPipeTransport` ne prend pas en charge les opérations d'un ordinateur à un autre. Elle est uniquement utilisée pour la communication sur le même ordinateur. Par conséquent, lorsque vous exécutez l'exemple sur plusieurs ordinateurs, mettez en commentaire les lignes suivantes dans le fichier de code client :  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
>  Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition c#, C++ ou Visual Basic .NET de la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
  
## <a name="see-also"></a>Voir aussi
