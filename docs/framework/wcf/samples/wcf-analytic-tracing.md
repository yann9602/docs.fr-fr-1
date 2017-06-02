---
title: "tra&#231;age analytique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# tra&#231;age analytique
Cet exemple montre comment ajouter vos propres événements de suivi au flux de données des traces analytiques que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] écrit dans le suivi des événements pour Windows dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].Les traces analytiques permettent d'obtenir facilement une visibilité de vos services sans que cela se traduise par une lourde pénalité en termes de performances.Cet exemple montre comment utiliser les API <xref:System.Diagnostics.Eventing?displayProperty=fullName> pour écrire des événements qui s'intègrent aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les API <xref:System.Diagnostics.Eventing?displayProperty=fullName>, consultez <xref:System.Diagnostics.Eventing?displayProperty=fullName>.  
  
 Pour en savoir plus sur le suivi des événements dans Windows, consultez [Améliorez le débogage et l'optimisation des performances avec ETW](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## Suppression d'EventProvider  
 Cet exemple utilise la classe <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=fullName>, qui implémente <xref:System.IDisposable?displayProperty=fullName>.Lors de l'implémentation du suivi pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], il est probable que vous utilisiez les ressources de <xref:System.Diagnostics.Eventing.EventProvider> pour la durée de vie du service.Pour cette raison, et à des fins de lisibilité, cet exemple ne supprime jamais l'<xref:System.Diagnostics.Eventing.EventProvider> inclus dans un wrapper.Si pour une raison ou une autre, les spécifications de votre service diffèrent en matière de suivi et que vous devez supprimer cette ressource, modifiez cet exemple conformément aux meilleures pratiques de suppression de ressources non managées.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la suppression de ressources non managées, consultez [Implémentation d'une méthode Dispose](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## Auto\-hébergement etHébergement Web  
 Pour les services hébergés sur le Web, les traces analytiques de WCF fournissent un champ, nommé « HostReference », utilisé pour identifier le service qui émet les traces.Les traces utilisateur extensibles peuvent participer à ce modèle et cet exemple en illustre les meilleures pratiques.Une référence d'hôte Web lorsque le caractère « &#124; » apparaît réellement dans la chaîne obtenue peut se présenter sous l'une des formes suivantes :  
  
-   Si l'application ne se situe pas à la racine.  
  
     \<NomSite\>\<CheminVirtuelApplication\>&#124;\<CheminVirtuelService\>&#124;\<NomService\>  
  
-   Si l'application se situe à la racine.  
  
     \<NomSite\>&#124;\<CheminVirtuelService\>&#124;\<NomService\>  
  
 Pour les services auto\-hébergés, les traces analytiques de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne remplissent pas le champ « HostReference ».La classe `WCFUserEventProvider` de cet exemple se comporte de manière cohérente lorsqu'elle est utilisée par un service auto\-hébergé.  
  
## Informations sur l'événement personnalisé  
 Le manifeste du fournisseur d'événements ETW de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] définit trois événements conçus par les auteurs du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour être émis depuis le code du service.Le tableau suivant détaille ces trois événements.  
  
|Événement|Description|ID d'événement|  
|---------------|-----------------|--------------------|  
|UserDefinedInformationEventOccurred|Émettez cet événement lorsqu'un fait remarquable, qui n'est pas un problème, se produit dans votre service.Par exemple, vous pouvez émettre un événement après qu'un appel à une base de données a abouti.|301|  
|UserDefinedWarningOccurred|Émettez cet événement lorsqu'un problème susceptible d'aboutir à un échec se produit.Par exemple, vous pouvez émettre un événement d'avertissement lorsqu'un appel à une base de données a échoué, mais que vous avez pu recourir à une banque de données redondante.|302|  
|UserDefinedErrorOccurred|Émettez cet événement lorsque votre service ne se comporte pas comme prévu.Par exemple, vous pouvez émettre un événement si un appel à une base de données a échoué et que vous n'avez pas pu récupérer les données ailleurs.|303|  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution WCFAnalyticTracingExtensibility.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator.svc**.L'URI du document WSDL du service doit s'afficher dans le navigateur.Copiez cet URI.  
  
4.  Exécutez le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(WcfTestClient.exe\).  
  
     Le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] \(WcfTestClient.exe\) se trouve sous \<répertoire d'installation [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] \>\\Common7\\IDE\\ WcfTestClient.exe \(le répertoire d'installation [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] par défaut est C:\\Program Files\\Microsoft Visual Studio 10.0\).  
  
5.  Dans le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ajoutez le service en sélectionnant **Fichier**, puis **Ajouter un service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
     Le service ICalculator est ajouté dans le volet gauche sous **Mes projets de service**.  
  
7.  Ouvrez l'application Observateur d'événements.  
  
     Avant d'appeler le service, démarrez l'Observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
8.  Dans le menu **Démarrer**, sélectionnez **Outils d'administration**, puis **Observateur d'événements**.Activez les journaux d'**analyse** et de **débogage**.  
  
9. Dans l'arborescence de l'Observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Serveur d'applications\-Applications**, sélectionnez **Afficher**, puis **Afficher les journaux d'analyse et de débogage**.  
  
     Vérifiez que l'option **Afficher les journaux d'analyse et de débogage** est activée.Activez le journal **Analyse**.  
  
     Dans l'arborescence de l'Observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, **Serveur d'applications\-Applications**, puis **Analyse**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.  
  
10. Testez le service à l'aide du client test WCF.  
  
    1.  Dans le client test WCF, double\-cliquez sur **Add\(\)** sous le nœud du service ICalculator.  
  
         La méthode **Add\(\)** s'affiche dans le volet droit avec deux paramètres.  
  
    2.  Tapez 2 pour le premier paramètre et 3 pour le deuxième.  
  
    3.  Cliquez sur **Appeler** pour appeler la méthode.  
  
11. Accédez à la fenêtre **Observateurs d'événements** que vous avez déjà ouverte.Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.  
  
12. Cliquez avec le bouton droit sur le nœud **Analyse** et sélectionnez **Actualiser**.  
  
     Les événements s'affichent dans le volet droit.  
  
13. Trouvez l'événement avec l'ID 303 et double\-cliquez dessus pour l'ouvrir et en inspecter le contenu.  
  
     Cet événement a été émis par la méthode `Add()` du service ICalculator et a une charge utile égale à « 2\+3\=5 ».  
  
#### Pour nettoyer \(facultatif\)  
  
1.  Ouvrez **Observateur d'événements**.  
  
2.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, puis **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Désactiver le journal**.  
  
3.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, **Serveur d'applications\-Applications**, puis **Analyse**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Effacer le journal**.  
  
4.  Cliquez sur **Effacer** pour effacer les événements.  
  
## Problème connu  
 Un problème connu de l'**Observateur d'événements** est qu'il lui arrive de ne pas parvenir à décoder des événements ETW.Le message d'erreur suivant peut alors s'afficher : « La description de l'ID d'événement \<id\> dans la source Microsoft\-Windows\-Serveur d'applications\-Applications est introuvable.Le composant qui a déclenché cet événement n'est pas installé sur l'ordinateur local ou l'installation est endommagée.Vous pouvez installer ou réparer le composant sur l'ordinateur local ». Si vous rencontrez cette erreur, sélectionnez **Actualiser** dans le menu **Actions**.Le décodage de l'événement doit ensuite s'effectuer correctement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)