---
title: "&#201;tendue du convoi des transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# &#201;tendue du convoi des transactions
Cet exemple montre comment créer un modèle d'activité de messagerie de convoi parallèle conjointement avec un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour modéliser un protocole où un certain nombre d'opérations peuvent se produire dans n'importe quel ordre dans le cadre de la même transaction.Cet exemple montre également comment un <xref:System.ServiceModel.Activities.TransactedReceiveScope> crée automatiquement une transaction lorsque aucune transaction n'est passée au serveur, de sorte que le client n'utilise aucune transaction.  
  
 Cet exemple est composé deux projets de workflow qui représentent le client et le serveur.Le projet client exécute un workflow qui commence en envoyant un message pour démarrer le workflow serveur, ce qui initialise une corrélation et démarre une étendue transactionnelle pour le reste des activités de messagerie.L'activité <xref:System.Activities.Statements.Sequence> cliente contient une paire <xref:System.ServiceModel.Activities.Send> et  <xref:System.ServiceModel.Activities.ReceiveReply> initiale, puis une activité <xref:System.Activities.Statements.Parallel> avec trois branches.Chaque branche envoie un message unidirectionnel au serveur.La propriété <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> de l'activité <xref:System.Activities.Statements.Parallel> a la valeur `false` afin que les trois branches se terminent.  
  
 Le workflow serveur est semblable au workflow client, excepté que les activités de messagerie sont orientées vers le côté serveur de la communication et qu'elles sont contenues dans une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> afin que tout le travail effectué s'exécute dans le cadre de la même transaction.Lorsque le premier message est reçu sur le serveur, une transaction est créée et est rendue ambiante pour l'étendue du corps <xref:System.ServiceModel.Activities.TransactedReceiveScope>, afin que toute activité de cette étendue puisse accéder à la transaction.Ensuite, toutes les réceptions s'exécutent en parallèle.Toutes les réceptions doivent s'exécuter une seule et unique fois, tel que décrit par la condition d'achèvement sur l'activité parallèle.Il existe un point de persistance implicite à la fin du corps <xref:System.ServiceModel.Activities.TransactedReceiveScope> et l'opération de persistance est également exécutée dans le cadre de la même transaction.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution ParallelConvoySample.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Vérifiez que les deux projets sont configurés pour démarrer.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la solution, puis sélectionnez **Définir les projets de démarrage**.  
  
    2.  Sélectionnez **Plusieurs projets de démarrage** et vérifiez que l'action pour les deux projets a la valeur **Démarrer**.  
  
4.  Pour exécuter la solution, appuyez sur CTRL\+F5.  
  
     Le serveur imprime `Server is running`, ce qui indique le serveur est prêt.  
  
     Appuyez sur n'importe quelle touche dans la fenêtre de console cliente pour démarrer l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`  
  
## Voir aussi