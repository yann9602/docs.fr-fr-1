---
title: "ByteStream Encoder | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ByteStream Encoder
Cet exemple montre comment créer un `ByteStreamHttpBinding`, un <xref:System.ServiceModel.Channels.Binding> qui illustre les fonctionnalités de l'encodeur de flux d'octets.  
  
## Discussion  
 Cet exemple montre comment créer un <xref:System.ServiceModel.Channels.Binding> standard à l'aide des éléments de liaison standard <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  Cet exemple montre comment utiliser l'encodeur de flux d'octets pour charger et télécharger une image.  L'encodeur de flux d'octets ne prend en charge que le transport HTTP et ne prend pas en charge les fonctionnalités telles que la messagerie fiable ou la sécurité.  Le seul <xref:System.ServiceModel.Channels.MessageVersion> pris en charge est <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  
  
> [!IMPORTANT]
>  Si vous exécutez cet exemple dans [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], veillez à exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges élevés.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez le fichier ByteStreamHttpBinding.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Démarrez une nouvelle instance du projet ByteStreamHttpBindingServer en cliquant avec le bouton droit sur le projet dans l'Explorateur de solutions et en sélectionnant **Débogage**, puis **Démarrer une nouvelle instance** dans le menu contextuel.  
  
3.  Démarrez une nouvelle instance du projet ByteStreamHttpBindingClient en cliquant avec le bouton droit sur le projet dans l'Explorateur de solutions et en sélectionnant **Débogage**, puis **Démarrer une nouvelle instance** dans le menu contextuel.