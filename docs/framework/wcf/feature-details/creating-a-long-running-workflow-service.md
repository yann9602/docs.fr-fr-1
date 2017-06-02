---
title: "Cr&#233;ation d&#39;un service de workflow de longue dur&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Cr&#233;ation d&#39;un service de workflow de longue dur&#233;e
Cette rubrique décrit comment créer un service de workflow de longue durée.  Les services de workflow de longue durée peuvent s'exécuter sur de longues périodes.  À un certain stade, le workflow peut devenir inactif en attendant des informations supplémentaires.  Lorsque cela se produit, le workflow est rendu persistant dans une base de données SQL et supprimé de la mémoire.  Une fois que les informations supplémentaires sont disponibles, l'instance de workflow est à nouveau chargée dans la mémoire et continue de s'exécuter.  Dans ce scénario, vous implémentez un système de commande très simplifié.  Le client envoie un message initial au service de workflow pour commencer la commande.  Un ID de commande est retourné au client.  À ce stade, le service de workflow attend un autre message du client, passe à l'état inactif et est rendu persistant dans une base de données SQL Server.  Lorsque le client envoie le message suivant pour commander un article, le service de workflow est à nouveau chargé dans la mémoire et termine le traitement de la commande.  Dans l'exemple de code, il retourne une chaîne indiquant que l'article a été ajouté à la commande.  L'exemple de code n'est pas censé refléter une application réelle de la technologie mais plutôt un exemple simple illustrant des services de workflow de longue durée. Cette rubrique suppose que vous savez déjà créer des projets et des solutions [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
## Composants requis  
 Les logiciels suivants doivent être installés pour suivre cette procédure pas à pas :  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  Vous êtes familiarisé avec WCF et [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] et vous savez déjà créer des projets et des solutions.  
  
### Pour configurer la base de données SQL  
  
1.  Pour que les instances du service de workflow soient persistantes, Microsoft SQL Server doit être installé et vous devez configurer une base de données pour stocker les instances de workflow persistantes.  Exécutez Microsoft SQL Management Studio en cliquant sur le bouton **Démarrer**, puis en sélectionnant **Tous les programmes**, **Microsoft SQL Server 2008** et **Microsoft SQL Management Studio**.  
  
2.  Cliquez sur le bouton **Connecter** pour vous connecter à l'instance SQL Server.  
  
3.  Cliquez avec le bouton droit sur **Bases de données** dans l'arborescence et sélectionnez **Nouvelle base de données...** pour créer une base de données nommée `SQLPersistenceStore`.  
  
4.  Exécutez le fichier de script SqlWorkflowInstanceStoreSchema.sql situé dans le répertoire C:\\Windows\\Microsoft.NET\\Framework\\v4.0\\SQL\\en dans la base de données SQLPersistenceStore pour configurer les schémas de base de données requis.  
  
5.  Exécutez le fichier de script SqlWorkflowInstanceStoreLogic.sql situé dans le répertoire C:\\Windows\\Microsoft.NET\\Framework\\v4.0\\SQL\\en dans la base de données SQLPersistenceStore pour configurer la logique de base de données requise.  
  
### Pour créer le service de workflow hébergé sur le Web  
  
1.  Créez une solution [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] vide et nommez\-la `OrderProcessing`.  
  
2.  Ajoutez à la solution un nouveau projet d'application de service de workflow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nommé `OrderService`.  
  
3.  Dans la boîte de dialogue des propriétés du projet, sélectionnez l'onglet **Web**.  
  
    1.  Sous **Action de démarrage**, sélectionnez **Page spécifique** et spécifiez `Service1.xamlx`.  
  
         ![Propriétés du projet web du service de flux de travail](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  Sous **Serveurs**, sélectionnez **Utiliser le serveur Web IIS local**.  
  
         ![Paramètres du serveur web local](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  Vous devez exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] en mode Administrateur pour effectuer ce paramétrage.  
  
         Ces deux étapes configurent le projet du service de workflow pour qu'il soit hébergé par IIS.  
  
4.  Ouvrez `Service1.xamlx` s'il n'est pas déjà ouvert et supprimez les activités **ReceiveRequest** et **SendResponse**.  
  
5.  Sélectionnez l'activité **Sequential Service** et cliquez sur le lien **Variables**, puis ajoutez les variables affichées dans l'illustration suivante.  Cette action permet d'ajouter des variables qui seront utilisées ultérieurement dans le service de workflow.  
  
    > [!NOTE]
    >  Si CorrelationHandle ne figure pas dans la liste déroulante Type de variable, sélectionnez **Rechercher des types** dans la liste.  Tapez CorrelationHandle dans la zone **Nom de type**, sélectionnez CorrelationHandle dans la zone de liste et cliquez sur **OK**.  
  
     ![Ajouter des variables](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  Faites glisser un modèle d'activité **ReceiveAndSendReply** dans l'activité **Sequential Service**.  Cet ensemble d'activités recevra un message d'un client et enverra une réponse en retour.  
  
    1.  Sélectionnez l'activité **Receive** et définissez les propriétés mises en surbrillance dans l'illustration suivante.  
  
         ![Définir les propriétés de l'activité Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         La propriété DisplayName définit le nom affiché pour l'activité Receive dans le concepteur.  Les propriétés ServiceContractName et OperationName spécifient le nom du contrat de service et de l'opération implémentés par l'activité Receive.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation des contrats dans les services de flux de travail, consultez [Utilisation de contrats dans le workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  
  
    2.  Cliquez sur le lien **Définir...** dans l'activité **ReceiveStartOrder** et définissez les propriétés affichées dans l'illustration suivante.  Notez que la case d'option **Paramètres** est sélectionnée et qu'un paramètre `p_customerName` est lié à la variable `customerName`.  L'activité **Receive** est alors configurée pour recevoir des données et lier ces données aux variables locales.  
  
         ![Définition des données reçues par l'activité Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  Sélectionnez l'activité **SendReplyToReceive** et définissez la propriété mise en surbrillance affichée dans l'illustration suivante.  
  
         ![Définition des propriétés de l'activité SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  Cliquez sur le lien **Définir...** dans l'activité **SendReplyToStartOrder** et définissez les propriétés affichées dans l'illustration suivante.  Notez que la case d'option **Paramètres** est sélectionnée ; un paramètre `p_orderId` est lié à la variable `orderId`.  Ce paramètre spécifie que l'activité SendReplyToStartOrder retournera une valeur de type String à l'appelant.  
  
         ![Configuration des données de contenu de l'activité SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
        > [!NOTE]
    5.  Faites glisser une activité Assign entre les activités **Receive** et **SendReply**, et définissez les propriétés comme dans l'illustration suivante :  
  
         ![Ajout d'une activité Assign](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         Cette action permet de créer un nouvel ID de commande et de placer la valeur dans la variable orderId.  
  
    6.  Sélectionnez l'activité **ReplyToStartOrder**.  Dans la fenêtre de propriétés, cliquez sur le bouton de sélection de **CorrelationInitializers**.  Sélectionnez le lien **Ajouter un initialiseur**, entrez `orderIdHandle` dans la zone de texte Initialiseur, sélectionnez l'initialiseur de corrélation de requête comme type de corrélation et sélectionnez p\_orderId sous la zone de texte déroulante Requêtes XPath.  Ces paramètres sont indiqués dans l'illustration suivante.  Cliquez sur **OK**.  Cette action permet d'initialiser une corrélation entre le client et cette instance du service de workflow.  Lorsqu'un message contenant cet ID de commande est reçu, il est routé vers cette instance du service de workflow.  
  
         ![Ajout d'un initialiseur de corrélation](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  Faites glisser une autre activité **ReceiveAndSendReply** vers la fin du workflow \(en dehors de la **séquence** contenant les premières activités **Receive** et **SendReply**\).  Le second message envoyé par le client sera alors reçu et une réponse sera renvoyée.  
  
    1.  Sélectionnez la **séquence** contenant les activités **Receive** et **SendReply** récemment ajoutées et cliquez sur le bouton **Variables**.  Ajoutez la variable mise en surbrillance dans l'illustration suivante :  
  
         ![Ajout de nouvelles variables](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  Sélectionnez l'activité **Receive** et définissez les propriétés indiquées dans l'illustration suivante :  
  
         ![Définir les propriétés de l'activité Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  Cliquez sur le lien **Définir...** dans l'activité **ReceiveAddItem** et ajoutez les paramètres indiqués dans l'illustration suivante. Cette action permet de configurer l'activité Receive de façon à accepter deux paramètres, l'ID de commande et l'ID de l'article commandé.  
  
         ![Spécification de paramètres pour la seconde réception](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  Cliquez sur le bouton de sélection **CorrelateOn** et entrez `orderIdHandle`.  Sous **Requêtes XPath**, cliquez sur la flèche de déroulement et sélectionnez `p_orderId`.  Cela permet de configurer la corrélation sur la deuxième activité Receive.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la corrélation, consultez [Corrélation](../../../../docs/framework/wcf/feature-details/correlation.md).  
  
         ![Définition de la propriété CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  Faites glisser une activité **If** immédiatement après l'activité **ReceiveAddItem**.  Cette activité agit de la même façon qu'une instruction if.  
  
        1.  Attribuez à la propriété **Condition** la valeur `itemId==”Zune HD” (itemId=”Zune HD” for Visual Basic)`.  
  
        2.  Faites glisser une activité **Assign** dans la section **Then** et une autre dans la section **Else**, puis définissez les propriétés des activités **Assign** comme indiqué dans l'illustration suivante.  
  
             ![Assignation du résultat de l'appel de service](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             Si la condition est `true`, la section **Then** est exécutée.  Si la condition est `false`, la section **Else** est exécutée.  
  
        3.  Sélectionnez l'activité **SendReplyToReceive** et définissez la propriété **DisplayName** indiquée dans l'illustration suivante.  
  
             ![Définition des propriétés de l'activité SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  Cliquez sur le lien **Définir...** dans l'activité **SetReplyToAddItem** et configurez\-la comme indiqué dans l'illustration suivante.  Cette action permet de configurer l'activité **SendReplyToAddItem** de façon à retourner la valeur dans la variable `orderResult`.  
  
             ![Définition de la liaison de données pour l'activité SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  Ouvrez le fichier web.config et ajoutez les éléments suivants dans la section \<behavior\> pour activer la persistance du workflow.  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
  
    ```  
  
    > [!WARNING]
    >  Assurez\-vous de remplacer le nom de l'hôte et de l'instance SQL Server dans l'extrait de code précédent.  
  
9. Générez la solution.  
  
### Pour créer une application cliente pour appeler le service de workflow  
  
1.  Ajoutez à la solution un nouveau projet d'application console nommé `OrderClient`.  
  
2.  Ajoutez les références aux assemblys suivantes au projet `OrderClient` :  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  Ajoutez une référence de service au service de workflow et spécifiez `OrderService` comme espace de noms.  
  
4.  Dans la méthode `Main()` du projet client, ajoutez le code suivant :  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
  
    ```  
  
5.  Générez la solution et exécutez l'application `OrderClient`.  Le client affiche le texte suivant :  
  
    ```Output  
  
                  Envoi d'un message de début  
    Le service de workflow est inactif.  Appuyez sur [Entrée] pour envoyer un message d'ajout d'élément de façon à réactiver le service de workflow.    
    ```  
  
6.  Pour vérifier que le service de workflow a été rendue persistante, démarrez SQL Server Management Studio en sélectionnant le menu **Démarrer**, **Tous les programmes**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.  
  
    1.  Dans le volet gauche, développez **Bases de données**, **SQLPersistenceStore**, **Vues** et cliquez avec le bouton droit sur **System.Activities.DurableInstancing.Instances**, puis choisissez **Sélectionner les 1000 lignes du haut**.  Dans le volet **Résultats**, vérifiez qu'au moins une instance est listée.  D'autres instances d'exécutions précédentes peuvent également être présentes si une exception s'est produite pendant l'exécution.  Vous pouvez supprimer les lignes existantes en cliquant avec le bouton droit sur **System.Activities.DurableInstancing.Instances** et en sélectionnant **Modifier les 200 lignes du haut**, en cliquant sur le bouton **Exécuter**, en sélectionnant toutes les lignes du volet de résultats puis **Supprimer**.  Pour vous assurer que l'instance affichée dans la base de données est bien l'instance créée par votre application, vérifiez que la vue Instances est vide avant d'exécuter le client.  Une fois que le client est en cours d'exécution, réexécutez la requête \(Sélectionner les 1000 lignes du haut\) et assurez\-vous qu'une nouvelle instance a été ajoutée.  
  
7.  Appuyez sur Entrée pour envoyer le message d'ajout d'élément au service de workflow.  Le client affiche le texte suivant :  
  
    ```Output  
  
                  Envoi d'un message d'ajout d'élément  
    Retour du service : Élément ajouté à la commande  
    Appuyez sur une touche pour continuer.  .  .    
    ```  
  
## Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)