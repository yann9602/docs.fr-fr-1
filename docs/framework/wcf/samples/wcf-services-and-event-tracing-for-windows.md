---
title: "WCF Services et suivi d'événements Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3b7b370ed6b1d9a900579ff0e6f1b0a22290c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>WCF Services et suivi d'événements Windows
Cet exemple montre comment utiliser le traçage analytique dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour émettre des événements dans le suivi d'événements pour Windows (ETW, Event Tracing for Windows). Les traces analytiques sont des événements émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui permettent de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans un environnement de production.  
  
 La trace analytique des services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est un suivi qui peut être activé dans un environnement de production avec un impact minime sur les performances. Ces traces sont émises en tant qu'événements dans une session de suivi ETW.  
  
 Cet exemple inclut un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base dans lequel des événements sont émis du service au journal des événements, lequel peut être consulté à l'aide de l'Observateur d'événements. Il est également possible de démarrer une session de suivi ETW dédiée qui écoute les événements du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. L'exemple comprend un script permettant de créer une session de suivi ETW dédiée qui stocke des événements dans un fichier binaire pouvant être lu à l'aide de l'Observateur d'événements.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution EtwAnalyticTraceSample.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator.svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.  
  
     Par défaut, le service commence à écouter les requêtes sur le port 1378 (http://localhost:1378/Calculator.svc).  
  
4.  Exécutez le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (WcfTestClient.exe).  
  
     Le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Répertoire_installation_ > \Common7\IDE\ WcfTestClient.exe (valeur par défaut [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] est C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  Dans le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test, ajoutez le service en sélectionnant **fichier**, puis **ajouter un Service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée. La valeur par défaut est http://localhost:1378/Calculator.svc.  
  
6.  Ouvrez l'application Observateur d'événements.  
  
     Avant d'appeler le service, démarrez l'Observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
7.  À partir de la **Démarrer** menu, sélectionnez **outils d’administration**, puis **Observateur d’événements**.  Activer la **analyse** et **déboguer** journaux.  
  
8.  Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**. Avec le bouton droit **serveur d’applications-Applications**, sélectionnez **vue**, puis **afficher les journaux d’analyse et de débogage**.  
  
     Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée.  
  
9. Activer la **analyse** journal.  
  
     Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **activer le journal**.  
  
#### <a name="to-test-the-service"></a>Pour tester le service  
  
1.  Revenez au client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], double-cliquez sur `Divide` et conservez les valeurs par défaut, qui spécifient le dénominateur 0.  
  
     Si le dénominateur est 0, le service génère une erreur.  
  
2.  Observez les événements émis par le service.  
  
     Revenez à l’Observateur d’événements et naviguez jusqu'à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **Actualiser**.  
  
     Les événements du traçage analytique de WCF s'affichent dans l'Observateur d'événements. Notez qu'en raison de l'erreur générée par le service, un événement de trace d'erreur est visible dans l'Observateur d'événements.  
  
3.  Répétez les étapes 1 et 2, mais avec des entrées valides. La valeur du paramètre `N2` peut être n'importe quel nombre différent de 0.  
  
     Actualisez le canal analytique pour constater que les événements WCF n'incluent aucun événement d'erreur.  
  
 L'exemple montre les événements de trace analytique émis par un service WCF.  
  
#### <a name="to-cleanup-optional"></a>Pour effectuer un nettoyage (facultatif)  
  
1.  Ouvrez l'observateur d'événements.  
  
2.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis  **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.  
  
3.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis  **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.  
  
4.  Choisissez le **effacer** option pour effacer les événements.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
