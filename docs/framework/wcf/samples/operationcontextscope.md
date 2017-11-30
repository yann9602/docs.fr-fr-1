---
title: OperationContextScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f636fe5bc79c18634f2239bc403c5189531737b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="operationcontextscope"></a>OperationContextScope
L'exemple OperationContextScope montre comment envoyer des informations supplémentaires sur un appel [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à l'aide d'en-têtes. Dans cet exemple, le serveur et le client sont tous deux des applications consoles.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple montre comment un client peut envoyer des informations supplémentaires en tant qu'<xref:System.ServiceModel.Channels.MessageHeader> à l'aide de <xref:System.ServiceModel.OperationContextScope>. Un objet <xref:System.ServiceModel.OperationContextScope> est créé en étendant sa portée à un canal. Les en-têtes qui doivent être translatés au service distant peuvent être ajoutés à la collection <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>. Les en-têtes ajoutés à cette collection peuvent être récupérés sur le service en accédant aux <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>. Ses appels sont passés sur plusieurs canaux et les en-têtes ajoutés au client s'appliquent uniquement au canal utilisé pour créer la <xref:System.ServiceModel.OperationContextScope>.  
  
## <a name="messageheaderreader"></a>MessageHeaderReader  
 Il s'agit de l'exemple de service qui reçoit un message du client et essaie de chercher l'en-tête dans la collection <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>. Le client passe le GUID qu'il a envoyé dans l'en-tête et le service récupère l'en-tête personnalisé et, la cas échéant, le compare avec le GUID passé comme argument par le client.  
  
```  
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =   
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,   
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+   
         "Does it match with GUID sent as parameter: {1}",   
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a>MessageHeaderClient  
 C’est l’implémentation de client qui utilise le proxy généré par [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour communiquer avec le service distant. Il crée en premier deux objets proxy de `MessageHeaderReaderClient`.  
  
```  
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 Le client crée ensuite une portée OperationContextScope et l'étend à `client1`. Il ajoute un <xref:System.ServiceModel.Channels.MessageHeader> aux <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> et passe un appel sur les deux clients. Elle garantit que l’en-tête est envoyé uniquement au `client1` et non sous `client2` en vérifiant la valeur de retour à partir de la `RetrieveHeader` appeler.  
  
```  
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetreieveHeader on both the proxies. Since the OperationContextScope is tied to   
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 Cet exemple est auto-hébergé. L'exemple suivant illustre une sortie de l'exécution de l'exemple :  
  
```  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
  
## <a name="see-also"></a>Voir aussi
