---
title: Encodage d'objets binaires avec l'encodeur ByteStream
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cf68356ffa5fe20de7bd417c77388cd214ca718
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Encodage d'objets binaires avec l'encodeur ByteStream
L'envoi et la réception de données binaires brutes avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont configurés à l'aide de l'objet <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Architecture de l'encodeur de message en flux d'octets  
 L'encodeur de message binaire utilisé par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne dispose d'aucune fonctionnalité de traitement, de validation ou d'identification des données binaires sous-jacentes dans le message. Le package de données est encodé au format XML, envoyé, reçu et décodé. L'encodeur traite les données une fois qu'elles ont été transmises au transport et avant que le message soit envoyé à la file d'attente des messages. Techniquement, l'encodeur binaire encapsule les données du message en éléments `<binary>` pour l'envoi et supprime les éléments une fois le message reçu.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Utilisation de l'encodeur de message en flux d'octets  
 L'exemple suivant montre un contrat de service qui implémente l'encodeur de message en flux d'octets.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 L'exemple suivant montre le service appelé.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 Dans le cas de l'utilisation d'un service qui implémente une infrastructure de message (tel qu'un routeur), le message est traité sans être inspecté ni validé et sans interaction avec le message, comme indiqué dans l'exemple suivant.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Scénarios  
 L'encodeur en flux d'octets s'avère utile dans les scénarios suivants.  
  
-   Transfert d'une image JPEG entre des ordinateurs à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Dans ce scénario, l'image arrive par transport depuis une source externe et les données sont transmises par les octets bruts qui forment l'image. Un service reçoit les données binaires et affiche l'image.  
  
-   Lecture d'informations à partir d'une file d'attente de messages et traitement de ces informations. Le message est lu à partir du gestionnaire de files d'attente de messages et passé au canal de file d'attente de messages à gérer. Le canal de file d'attente de messages agit comme un gestionnaire de files d'attente dans la pile de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Dans le cas de l'envoi d'un message sur un canal de file d'attente de messages, l'expéditeur n'a aucun contrôle sur les octets reçus du gestionnaire de files d'attente. Si le processus de réception n'arrive pas à lire les octets bruts, le message sera reçu avec un formatage erroné et ne sera pas traité ; on suppose que le processus de réception a la capacité de traduire les octets reçus dans un format utilisable.
