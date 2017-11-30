---
title: "Extraire des données WF à l'aide du suivi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bbc9d72a55bd0affdccae9b735355c7e30c5d933
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="extract-wf-data-using-tracking"></a>Extraire des données WF à l'aide du suivi
Cet exemple montre comment utiliser le suivi de workflow pour extraire des variables de workflow et des arguments d’activités. Il montre également l'ajout d'annotations à des enregistrements de suivi et l'extraction de la charge utile de données dans des enregistrements de suivi personnalisés. L'exemple utilise le participant de suivi Suivi d'événements pour Windows (ETW, Event Tracing for Windows) pour extraire des données du workflow.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] fournit le suivi pour avoir plus de visibilité dans l'exécution d'une instance de workflow. Le runtime de suivi émet des enregistrements de suivi de workflow lors de l'exécution du workflow. Avec les enregistrements de suivi de workflow, les données dans l'instance de workflow peuvent être extraites du workflow. La liste suivante détaille les types des données qui peuvent être extraites des enregistrements de suivi :  
  
1.  Variables de workflow dans une activité et enregistrements de suivi pendant l'exécution de l'activité.  
  
     Pour extraire des variables de workflow, les variables à extraire sont spécifiées dans un profil. Les variables à extraire peuvent uniquement être spécifiées avec `ActivityStateQueries`. L'exemple de code suivant illustre un modèle de suivi utilisé pour extraire la variable de workflow d'une activité.  
  
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
  
     Les arguments définissent le flux de données à l'intérieur ou à l'extérieur d'une activité. Les arguments à extraire sont spécifiés à l'aide d'un <xref:System.Activities.Tracking.ActivityStateQuery>. L'exemple de code suivant est un modèle de suivi qui extrait l'argument `Value`.  
  
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
  
3.  Les annotations sont des paires clé/valeur qui peuvent être ajoutées à tout enregistrement de suivi émis.  
  
     Les annotations servent de mécanisme de balises pour les enregistrements de suivi. Les annotations sont ajoutées aux enregistrements de suivi via un modèle de suivi. Les annotations peuvent être ajoutées à tout type de requête de suivi de workflow. L'exemple de code suivant est un modèle de suivi qui montre comment une annotation peut être ajoutée à un enregistrement de suivi.  
  
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
  
     Les enregistrements de suivi personnalisés peuvent contenir des données de charge utile définies dans cette activité. L'abonnement aux enregistrements de suivi personnalisés dans un modèle de suivi permet l'extraction de la charge utile dans l'enregistrement de suivi. Les enregistrements de suivi personnalisés peuvent être extraits avec un <xref:System.Activities.Tracking.TrackingQuery> personnalisé. L'exemple de code suivant est un modèle de suivi qui extrait un enregistrement de suivi personnalisé avec sa charge utile.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 L'exemple illustre l'extraction de variables, d'arguments et d'enregistrements personnalisés ainsi que l'ajout d'annotations à l'aide d'un profil spécifié dans un fichier Web.config. Le suivi est activé sur l'exemple de service de workflow en ajoutant un élément de comportement `<etwTracking>`. L'exemple de code suivant active le suivi pour le modèle de suivi `ExtractWorkflowVariables`.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
     La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.  
  
4.  Dans le navigateur, cliquez sur StockPriceService.xamlx.  
  
5.  Le navigateur affiche la page StockPriceService, laquelle contient l'adresse WSDL du service local. Copiez cette adresse.  
  
     L'exemple suivant affiche une adresse WSDL du service local. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Avant d'appeler le service, démarrez l'observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service de workflow.  
  
7.  À partir de la **Démarrer** menu, sélectionnez **outils d’administration** , puis **Observateur d’événements**.  
  
8.  Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, et **Microsoft**. Avec le bouton droit **Microsoft** et sélectionnez **vue** , puis **afficher les journaux d’analyse et de débogage**.  
  
     Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée.  
  
9. Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **activer le journal**.  
  
10. À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], ouvrez le client de test WCF.  
  
     Le client de test WCF (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] dossier d’installation > \Common7\IDE\ dossier.  
  
     Le dossier d'installation [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] par défaut est C:\Program Files\Microsoft Visual Studio 10.0.  
  
11. Dans le client test WCF, sélectionnez **ajouter un Service** à partir de la **fichier** menu.  
  
     Ajoutez l'adresse WSDL du service local que vous avez copiée précédemment dans la zone d'entrée.  
  
12. Dans le client test WCF, double-cliquez sur `GetStockPrice`.  
  
     Vous ouvrez ainsi la méthode `GetStockPrice`. La demande accepte un paramètre. Utilisez la valeur **Contoso**.  
  
13. Cliquez sur **appeler**.  
  
14. Revenez à l’Observateur d’événements et naviguez jusqu'à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **Actualiser**. Les événements de workflow sont dans la plage d'ID d’événements comprise entre 100 et 199.  
  
     Les événements contiennent les annotations, variables, arguments et enregistrements de suivi personnalisés qui peuvent être affichés dans l'observateur d'événements.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Nettoyage dans l'observateur d'événements  
 Le canal analytique dans le journal des événements peut être nettoyé dans l'observateur d'événements en procédant comme suit.  
  
#### <a name="to-clean-up-optional"></a>Pour nettoyer (facultatif)  
  
1.  Ouvrez l'observateur d'événements.  
  
2.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**. Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.  
  
3.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**. Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.  
  
     Choisissez le **effacer** option pour effacer les événements.  
  
## <a name="known-issue"></a>Problème connu  
  
> [!NOTE]
>  Un problème connu de l'observateur d'événements est qu'il lui arrive de ne pas parvenir à décoder des événements ETW. Un message d'erreur semblable au suivant s'affiche éventuellement.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Si vous rencontrez cette erreur, cliquez sur **Actualiser** dans le volet actions. Le décodage de l'événement doit maintenant s'effectuer correctement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
