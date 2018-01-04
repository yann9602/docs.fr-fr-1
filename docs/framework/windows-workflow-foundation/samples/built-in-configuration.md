---
title: "Configuration intégrée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ddf9b316074a69a88f08a0d7f519533f2db0002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="built-in-configuration"></a>Configuration intégrée
Cet exemple illustre l'utilisation et la configuration du magasin d'instances de workflow SQL. Le magasin d'instances de workflow SQL est une implémentation basée sur SQL d'un magasin d'instances. Il permet à une instance d'enregistrer et de charger son état vers et à partir d'une base de données SQL Server ou SQL Server Express.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Cet exemple est composé d'un workflow qui implémente un service de comptage. Une fois que la méthode de démarrage du service est appelée, le service compte de 0 à 59. Le compteur est incrémenté une fois toutes les 2 secondes. Après chaque compte, le workflow rend son état persistant.  
  
 Le workflow de comptage est auto-hébergé par un hôte de service de workflow. La méthode `Main` du programme crée une instance de l'hôte de service de workflow qui héberge le workflow de comptage. Elle définit les points de terminaison sous lesquels le workflow de comptage peut être atteint. Après cela, il définit un comportement de magasin d'instances de workflow SQL, lequel est utilisé pour configurer le magasin d'instances de workflow SQL. Ensuite, le programme crée un client qui appelle la méthode de démarrage du workflow de comptage.  
  
 Une fois le programme démarré, le compteur commence automatiquement le comptage. Notez que le chargement de l'instance et la configuration du magasin d'instances de workflow SQL peut prendre quelques secondes. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]le magasin d’instances de flux de travail, consultez [magasin d’instances de flux de travail de SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Cet exemple est composé de deux parties :  
  
1.  InstanceStore1 montre comment <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> est configuré à l'aide du code C# (voir Program.cs).  
  
2.  InstanceStore2 montre comment <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> est configuré à l'aide de XML (voir App.config).  
  
 Les paramètres suivants sont disponibles pour configurer le comportement du magasin d'instances de workflow SQL :  
  
-   Définissez `HostLockRenewalPeriod`. Ce temps définit l'intervalle dans lequel l'hôte renouvelle le verrou de propriété des instances qu'il s'exécute. Les informations de verrou sont stockées dans le magasin d'instances. Si la propriété n'est pas renouvelée pendant deux des intervalles définis dans `HostLockRenewalPeriod`, l'instance est considérée comme étant abandonnée. Si un autre <xref:System.ServiceModel.Activities.WorkflowServiceHost> exécute le même workflow et est connecté au même magasin d'instances (sur le même ordinateur ou sur un ordinateur différent), il récupère cette instance. (La récupération d'instance est hors de portée pour cet exemple.)  
  
-   Définissez `RunnableInstancesDetectionPeriod`. Cette période définit l'intervalle dans lequel l'hôte recherche les instances qui sont devenues exécutables. Des instances peuvent devenir exécutables si l'un des événements suivants se produit :  
  
    -   Un minuteur durable (<xref:System.Activities.Statements.Delay>) expire.  
  
    -   Un autre hôte manque sa pulsation `HostLockRenewal` (par exemple, en raison d'un incident d'ordinateur) et l'instance est récupérée.  
  
-   Définissez `InstanceCompletionAction`. Cette propriété, si elle a la valeur `DeleteNothing`, conserve les instances terminées dans le magasin d'instances ; si elle a la valeur `DeleteAll`, les instances sont supprimées du magasin une fois leur exécution terminée. Prenez note de ce qui suit :  
  
    > [!NOTE]
    >  Le fait d'arrêter l'hôte en appuyant sur ENTRÉE avant la fin du comptage ne termine pas l'instance de workflow.  
  
-   Définissez `InstanceLockedExceptionAction`. Ce paramètre définit ce qu'un hôte doit faire s'il veut charger une instance qui est verrouillée par un autre hôte. Les options suivantes sont disponibles :  
  
    -   Si la valeur définie est `NoRetry` : permet de ne pas faire une nouvelle tentative de charge et de retourner un `InstanceLockedException` à l'hôte.  
  
    -   Si la valeur définie est `BasicRetry` : permet de poursuivre la tentative de chargement de l'instance. Les nouvelles tentatives sont planifiées selon un algorithme linéaire simple (par exemple, réessayer toutes les 5 secondes).  
  
    -   Si la valeur définie est `AggressiveRetry` : permet de poursuivre la tentative de chargement de l'instance. Les tentatives sont planifiées selon un algorithme de réduction de puissance exponentiel agressif.  
  
-   Définissez l'option Encodage. Ce paramètre définit la façon dont l'état de l'instance est stocké dans le magasin d'instances de workflow SQL. Les options suivantes sont disponibles :  
  
    -   L'état de l'instance est compressé à l'aide de l'algorithme de compression Gzip.  
  
    -   L'état de l'instance n'est pas compressé.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en tant qu'Administrateur si ces autorisations sont disponibles.  
  
2.  Accédez au répertoire de l'exemple (\WF\Basic\Persistence\BuiltInConfiguration\CS) et exécutez CreateInstanceStore.cmd.  
  
3.  Si les privilèges d'administrateur ne sont pas disponibles, créez un compte de connexion SQL Server. Accédez à `Security`, **connexions**. Avec le bouton droit **connexions** et créez une nouvelle connexion.  
  
4.  Ajoutez votre utilisateur ACL au rôle SQL. Ouvrez **bases de données**, **InstanceStore**, **sécurité**. Avec le bouton droit **utilisateurs** et sélectionnez **nouveaux utilisateurs**. Définir le **nom de connexion** pour l’utilisateur créé à l’étape précédente. Ajoutez l’utilisateur à l’appartenance au rôle de base de données **System.Activities.DurableInstancing.InstanceStoreUsers** (et autres). Notez qu'il est possible que l'utilisateur existe déjà (par exemple, l'utilisateur dbo).  
  
5.  Ouvrez le fichier InstanceStore.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez la solution en appuyant sur Ctrl+Maj+B.  
  
6.  Dans [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], accédez au répertoire \bin\debug approprié de l’exemple (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), cliquez avec le bouton droit sur InstanceStore.exe, puis sélectionnez **exécuter en tant qu’administrateur**. Cet exemple doit être exécuté avec des privilèges d'administrateur car il ouvre un écouteur de canal.  
  
7.  Si vous avez créé le magasin d'instances dans une base de données autre qu'une installation locale de SQL Server Express, vous devez mettre à jour, dans l'exemple, la chaîne de connexion à la base de données (`const string ConnectionString` dans le fichier Program.cs du projet InstanceStore1, et l'attribut `connectionString` dans le fichier App.config du projet InstanceStore2) et recompiler l'exemple.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Pour vérifier que l'exemple s'exécute correctement  
  
1.  Pendant que l'exemple est en cours d'exécution, démarrez SQL Server Management Studio.  
  
2.  Dans le **l’Explorateur d’objets**, sélectionnez **bases de données**, **InstanceStore**, **Tables**, puis  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Bouton droit sur **InstanceTable** et sélectionnez **sélectionnez 1000 lignes du haut**.  
  
4.  Observez qu’il existe une nouvelle entrée et que le **expiration du verrou** modifie toutes les 5 secondes (cliquez sur la barre des tâches **Execute** bouton pour actualiser la requête). Il s’agit d’une conséquence du paramètre de la **Host Lock Renewal Period** à 5.  
  
5.  Vous pouvez observer qu'une fois le comptage terminé, l'entrée est supprimée de la table d'instance. Il s’agit d’une conséquence de paramètre **Instance Completion Action** à **DeleteAll**.  
  
6.  Appuyez sur ENTRÉE pour mettre fin à l’application hôte du workflow et constatez que la **LockOwnersTable** est supprimé.  
  
#### <a name="to-uninstall-the-sample"></a>Pour désinstaller l'exemple  
  
1.  Exécutez RemoveInstanceStore.cmd dans le répertoire de l'exemple (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Voir aussi  
 [Hébergement de AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)
