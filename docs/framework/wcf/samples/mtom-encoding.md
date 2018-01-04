---
title: MTOM Encoding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed65e2098a95a05f7cc5efa6d9014f67bf5ed261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mtom-encoding"></a>MTOM Encoding
Cet exemple montre l'utilisation de l'encodage de message MTOM (Message Transmission Optimization Mechanism) à l'aide de WSHttpBinding. MTOM est un mécanisme permettant de transmettre des pièces jointes binaires de grande taille avec des messages SOAP sous forme d'octets bruts, et d'obtenir ainsi des messages plus petits.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Par défaut, WSHttpBinding envoie et reçoit des messages sous forme de texte XML normal. Pour permettre l'envoi et la réception de messages MTOM, définissez l'attribut `messageEncoding` sur la configuration de la liaison (tel qu'indiqué dans l'exemple de code suivant), ou directement sur la liaison à l'aide de la propriété `MessageEncoding`. Le service ou le client peut maintenant envoyer et recevoir des messages MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 L'encodeur MTOM permet d'optimiser des tableaux d'octets et des flux. Dans cet exemple, l'opération utilise un paramètre `Stream` et peut donc être optimisée.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```  
  
 Le contrat choisi pour cet exemple transmet les données binaires au service et reçoit le nombre d'octets téléchargé comme valeur de retour. Lorsque le service est installé et que le client est exécuté, il imprime le nombre 1 000, qui indique que tous l'ensemble des 1 000 octets ont été reçus. Le reste de la sortie répertorie les tailles de message optimisées et non optimisées des diverses charges utiles.  
  
```  
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 Le but de l'utilisation de MTOM est d'optimiser la transmission de charges utiles binaires de grande taille. L'envoi d'un message SOAP à l'aide de MTOM entraîne une surcharge significative pour les charges utiles binaires de petite taille, mais s'avère très avantageux lorsqu'elles passent à quelques milliers d'octets. La raison à cela est que le texte XML normal encode des données binaires à l'aide de Base64, qui requiert quatre caractères tous les trois octets, et augmente la taille des données d'un tiers. MTOM peut transmettre des données binaires sous forme d'octets bruts, ce qui permet de gagner du temps lors de l'encodage et du décodage et d'obtenir des messages plus petits. Le seuil de quelques milliers d'octets est petit comparé aux photographies numériques et documents professionnels actuels.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Voir aussi
