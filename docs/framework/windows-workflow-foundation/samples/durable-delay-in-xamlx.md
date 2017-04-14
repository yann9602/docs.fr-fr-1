---
title: "D&#233;lai durable en XAMLX | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# D&#233;lai durable en XAMLX
Cet exemple montre comment utiliser un délai durable, qui est un délai rendant le workflow persistant sur un périphérique durable pendant le délai.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## Discussion  
 L'exemple de workflow contient deux messages sur un fichier local qui sont séparés par un délai.Lorsque le délai est déclenché, le workflow est déchargé, et attend 5 secondes dans le magasin d'instances de workflow avant d'être rechargé en mémoire.  
  
 Le fichier .xamlx est un service de workflow hébergé dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] utilise Cassini qui utilise un hôte de service de workflow pour héberger le workflow.  
  
 En plus d'héberger le workflow, l'hôte de service de workflow gère les instances de workflow en les chargeant et en les déchargeant.Pour démarrer une instance de la définition [!INCLUDE[wf](../../../../includes/wf-md.md)] \(sur l'hôte de service de workflow\), définissez un client qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.Ce <xref:System.ServiceModel.Activities.Receive> a sa propriété <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> qui a la valeur `true`, ce qui lui permet de créer une instance du workflow une fois qu'il reçoit un message.  
  
 Pendant l'initialisation, un comportement de déchargement d'instance est ajouté au fichier de configuration qui spécifie l'hôte de service de workflow sous lequel il doit décharger une instance dans le magasin de persistance \(base de données\).Pour cet exemple, il décharge l'instance immédiatement après le passage du workflow à l'état inactif \(lorsque le délai est déclenché\).  
  
#### Pour utiliser cet exemple  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naviguez jusqu'au dossier DurableDelayXamlx\\CS.  
  
3.  Exécutez Setup.cmd.  
  
4.  Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en tant qu'administrateur.  
  
5.  Ouvrez le fichier solution DurableDelayXamlx.sln.  
  
6.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la solution et sélectionnez **Propriétés**.  
  
7.  Sélectionnez **Plusieurs projets de démarrage** et affectez aux deux projets la valeur **Démarrer**.  
  
8.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
9. Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
#### Pour désinstaller cet exemple  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Naviguez jusqu'au dossier DurableDelayXamlx\\CS.  
  
3.  Exécutez Cleanup.cmd.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`