---
title: "Extraire des donn&#233;es WF &#224; l&#39;aide du suivi | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Extraire des donn&#233;es WF &#224; l&#39;aide du suivi
Cet exemple montre comment utiliser le suivi de workflow pour extraire des variables de workflow et des arguments d'activités.Il montre également l'ajout d'annotations à des enregistrements de suivi et l'extraction de la charge utile de données dans des enregistrements de suivi personnalisés.L'exemple utilise le participant de suivi Suivi d'événements pour Windows \(ETW, Event Tracing for Windows\) pour extraire des données du workflow.  
  
## Détails de l'exemple  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] fournit le suivi pour avoir plus de visibilité dans l'exécution d'une instance de workflow.Le runtime de suivi émet des enregistrements de suivi de workflow lors de l'exécution du workflow.Avec les enregistrements de suivi de workflow, les données dans l'instance de workflow peuvent être extraites du workflow.La liste suivante détaille les types des données qui peuvent être extraites des enregistrements de suivi :  
  
1.  Variables de workflow dans une activité et enregistrements de suivi pendant l'exécution de l'activité.  
  
     Pour extraire des variables de workflow, les variables à extraire sont spécifiées dans un profil.Les variables à extraire peuvent uniquement être spécifiées avec `ActivityStateQueries`.L'exemple de code suivant illustre un modèle de suivi utilisé pour extraire la variable de workflow d'une activité.  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  Arguments d'activité et enregistrements de suivi d'état d'activité.  
  
     Les arguments définissent le flux de données à l'intérieur ou à l'extérieur d'une activité.Les arguments à extraire sont spécifiés à l'aide d'un <xref:System.Activities.Tracking.ActivityStateQuery>. L'exemple de code suivant est un modèle de suivi qui extrait l'argument `Value`.  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  Les annotations sont des paires clé\/valeur qui peuvent être ajoutées à tout enregistrement de suivi émis.  
  
     Les annotations servent de mécanisme de balises pour les enregistrements de suivi.Les annotations sont ajoutées aux enregistrements de suivi via un modèle de suivi.Les annotations peuvent être ajoutées à tout type de requête de suivi de workflow.L'exemple de code suivant est un modèle de suivi qui montre comment une annotation peut être ajoutée à un enregistrement de suivi.  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  Les enregistrements de suivi personnalisés sont émis à partir d'activités définies par l'utilisateur.  
  
     Les enregistrements de suivi personnalisés peuvent contenir des données de charge utile définies dans cette activité.L'abonnement aux enregistrements de suivi personnalisés dans un modèle de suivi permet l'extraction de la charge utile dans l'enregistrement de suivi.Les enregistrements de suivi personnalisés peuvent être extraits avec un <xref:System.Activities.Tracking.TrackingQuery> personnalisé.L'exemple de code suivant est un modèle de suivi qui extrait un enregistrement de suivi personnalisé avec sa charge utile.  
  
    ```  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 L'exemple illustre l'extraction de variables, d'arguments et d'enregistrements personnalisés ainsi que l'ajout d'annotations à l'aide d'un profil spécifié dans un fichier Web.config.Le suivi est activé sur l'exemple de service de workflow en ajoutant un élément de comportement `<etwTracking>`.L'exemple de code suivant active le suivi pour le modèle de suivi `ExtractWorkflowVariables`.  
  
```  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
     La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.  
  
4.  Dans le navigateur, cliquez sur StockPriceService.xamlx.  
  
5.  Le navigateur affiche la page StockPriceService, laquelle contient l'adresse WSDL du service local.Copiez cette adresse.  
  
     L'exemple suivant affiche une adresse WSDL du service local.`http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Avant d'appeler le service, démarrez l'observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service de workflow.  
  
7.  Dans le menu **Démarrer**, sélectionnez **Outils d'administration**, puis **Observateur d'événements**.  
  
8.  Dans l'arborescence de l'observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services** et **Microsoft**.Cliquez avec le bouton droit sur **Microsoft** et sélectionnez **Afficher**, puis **Afficher les journaux d'analyse et de débogage**.  
  
     Vérifiez que l'option **Afficher les journaux d'analyse et de débogage** est activée.  
  
9. Dans l'arborescence de l'observateur d'événements, naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.  
  
10. Ouvrez le client test WCF à l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)].  
  
     Le client test WCF \(WcfTestClient.exe\) se trouve dans le dossier \<dossier d'installation [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]\>\\Common7\\IDE\\.  
  
     Le dossier d'installation [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] par défaut est C:\\Program Files\\Microsoft Visual Studio 10.0.  
  
11. Dans le client test WCF, sélectionnez **Ajouter un service** dans le menu **Fichier**.  
  
     Ajoutez l'adresse WSDL du service local que vous avez copiée précédemment dans la zone d'entrée.  
  
12. Dans le client test WCF, double\-cliquez sur `GetStockPrice`.  
  
     Vous ouvrez ainsi la méthode `GetStockPrice`.La demande accepte un paramètre.Utilisez la valeur **Contoso**.  
  
13. Cliquez sur **Appeler**.  
  
14. Revenez à l'observateur d'événements et naviguez jusqu'à **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows**, **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Actualiser**.Les événements de workflow sont dans la plage d'ID d’événements comprise entre 100 et 199.  
  
     Les événements contiennent les annotations, variables, arguments et enregistrements de suivi personnalisés qui peuvent être affichés dans l'observateur d'événements.  
  
## Nettoyage dans l'observateur d'événements  
 Le canal analytique dans le journal des événements peut être nettoyé dans l'observateur d'événements en procédant comme suit.  
  
#### Pour nettoyer \(facultatif\)  
  
1.  Ouvrez l'observateur d'événements.  
  
2.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Désactiver le journal**.  
  
3.  Naviguez vers **Observateur d'événements**, **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Effacer le journal**.  
  
     Choisissez l'option **Effacer** pour effacer les événements.  
  
## Problème connu  
  
> [!NOTE]
>  Un problème connu de l'observateur d'événements est qu'il lui arrive de ne pas parvenir à décoder des événements ETW.Un message d'erreur semblable au suivant s'affiche éventuellement.  
>   
>  `La description de l'ID d'événement <id> dans la source Microsoft-Windows-Serveur d'applications-Applications est introuvable.Le composant qui a déclenché cet événement n'est pas installé sur l'ordinateur local ou l'installation est endommagée.Vous pouvez installer ou réparer le composant sur l'ordinateur local.`  
>   
>  Si vous rencontrez cette erreur, cliquez sur **Actualiser** dans le volet Actions.Le décodage de l'événement doit maintenant s'effectuer correctement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)