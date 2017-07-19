---
title: "Using Performance Counters | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: 31
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 31
---
# Using Performance Counters
Cet exemple montre comment accéder aux compteurs de performance [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et comment créer des compteurs de performance définis par l'utilisateur.Il est basé sur l'[Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Dans cet exemple, le client appelle les quatre méthodes du service `ICalculator`.Le client continue jusqu'à ce qu'il soit interrompu par l'utilisateur.Le service reste inchangé.  
  
 Les compteurs de performance sont activés dans la section de diagnostic du fichier Web.config pour le service, comme le montre l'exemple de configuration suivant.  
  
```  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Cette tâche peut également être effectuée à l'aide de l'[Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Lorsque les compteurs de performance sont activés, la suite entière de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est activée pour le service.Le .NET Framework assure automatiquement la maintenance des données de performance à trois niveaux : `ServiceModelService`, `ServiceModelEndpoint` et `ServiceModelOperation`.Chacun de ces niveaux comporte des compteurs de performance tels que « Appels », « Appels par seconde », et « Appels de sécurité non autorisés ».  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### Pour afficher les données de performance  
  
1.  Démarrez l'outil Analyseur de performances en cliquant sur **Démarrer**, **Exécuter**, entrez `perfmon` et cliquez sur **OK** ou, dans le Panneau de configuration, sélectionnez **Outils d'administration** et double\-cliquez sur **Performances**.  
  
    > [!NOTE]
    >  Vous ne pouvez pas ajouter de compteurs tant que l'exemple de code est en cours d'exécution.  
  
2.  Supprimez les compteurs de performance répertoriés en les sélectionnant et en appuyant sur la touche Suppr.  
  
3.  Ajoutez des compteurs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en cliquant avec le bouton droit sur le volet du graphique et en sélectionnant **Ajouter des compteurs**.Dans la boîte de dialogue **Ajouter des compteurs**, sélectionnez **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** dans la liste déroulante Objet de performance.Sélectionnez les compteurs que vous souhaitez afficher dans la liste.  
  
    > [!NOTE]
    >  Il n'y a pas de compteurs de performance [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour un service s'il n'y a pas de services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en cours d'exécution sur l'ordinateur.  
  
### Pour utiliser l'Éditeur de configuration afin d'activer des compteurs  
  
1.  Ouvrez une instance de SvcConfigEditor.exe.  
  
2.  Dans le menu File, cliquez sur **Open**, puis sur **Config file**.  
  
3.  Naviguez jusqu'au dossier de service de l'exemple d'application et ouvrez le fichier Web.config.  
  
4.  Cliquez sur **Diagnostics** dans l'arborescence Configuration.  
  
5.  Basculez l'affichage de **Performance counter** dans la fenêtre **Diagnostics** sur « All ».  
  
6.  Enregistrez le fichier de configuration et quittez l'éditeur.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)