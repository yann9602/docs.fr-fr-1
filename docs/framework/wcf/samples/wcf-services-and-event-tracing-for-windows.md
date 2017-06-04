---
title: "WCF Services et suivi d&#39;&#233;v&#233;nements Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# WCF Services et suivi d&#39;&#233;v&#233;nements Windows
Cet exemple montre comment utiliser le traçage analytique dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour émettre des événements dans le suivi d'événements pour Windows \(ETW, Event Tracing for Windows\).  Les traces analytiques sont des événements émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui permettent de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans un environnement de production.  
  
 La trace analytique des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est un suivi qui peut être activé dans un environnement de production avec un impact minime sur les performances.  Ces traces sont émises en tant qu'événements dans une session de suivi ETW.  
  
 Cet exemple inclut un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base dans lequel des événements sont émis du service au journal des événements, lequel peut être consulté à l'aide de l'Observateur d'événements.  Il est également possible de démarrer une session de suivi ETW dédiée qui écoute les événements du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution EtwAnalyticTraceSample.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator.svc**.  L'URI du document WSDL du service doit s'afficher dans le navigateur.  Copiez cet URI.  
  
     Par défaut, le service commence à écouter les requêtes sur le port 1378 \(http:\/\/localhost:1378\/Calculator.svc\).  
  
4.  Exécutez le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(WcfTestClient.exe\).  
  
     Le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) se trouve sous \<répertoire d'installation de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]\>\\Common7\\IDE\\ WcfTestClient.exe \(le répertoire d'installation de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] par défaut est C:\\Program Files\\Microsoft Visual Studio 10.0\).  
  
5.  Dans le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ajoutez le service en sélectionnant **Fichier**, puis **Ajouter un service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée.  La valeur par défaut est http:\/\/localhost:1378\/Calculator.svc.  
  
6.  Ouvrez l'application Observateur d'événements.  
  
     Avant d'appeler le service, démarrez l'Observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
7.  Dans le menu **Démarrer**, sélectionnez **Outils d'administration**, puis **Observateur d'événements**.  Activez les journaux d'**analyse** et de **débogage**.  
  
8.  Dans l'arborescence de l'Observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.  Cliquez avec le bouton droit sur **Serveur d'applications\-Applications**, sélectionnez **Afficher**, puis **Afficher les journaux d'analyse et de débogage**.  
  
     Vérifiez que l'option **Afficher les journaux d'analyse et de débogage** est activée.  
  
9. Activez le journal **Analyse**.  
  
     Dans l'arborescence de l'Observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.  Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.  
  
#### Pour tester le service  
  
1.  Revenez au client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], double\-cliquez sur `Divide` et conservez les valeurs par défaut, qui spécifient le dénominateur 0.  
  
     Si le dénominateur est 0, le service génère une erreur.  
  
2.  Observez les événements émis par le service.  
  
     Revenez à l'observateur d'événements et naviguez jusqu'à **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.  Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Actualiser**.  
  
     Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements.  Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.  
  
3.  Répétez les étapes 1 et 2, mais avec des entrées valides.  La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.  
  
     Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.  
  
 L'exemple montre les événements de trace analytique émis par un service WCF.  
  
#### Pour effectuer un nettoyage \(facultatif\)  
  
1.  Ouvrez l'observateur d'événements.  
  
2.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.  Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Désactiver le journal**.  
  
3.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.  Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Effacer le journal**.  
  
4.  Choisissez l'option **Effacer** pour effacer les événements.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)