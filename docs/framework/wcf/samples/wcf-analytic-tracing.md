---
title: "traçage analytique [WCF]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c238d4c923b00a6c3387caa9bdafd69b126753c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-analytic-tracing"></a>traçage analytique [WCF]
Cet exemple montre comment ajouter vos propres événements de suivi au flux de données des traces analytiques que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] écrit dans le suivi des événements pour Windows dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Les traces analytiques permettent d'obtenir facilement une visibilité de vos services sans que cela se traduise par une lourde pénalité en termes de performances. Cet exemple montre comment utiliser les API <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> pour écrire des événements qui s'intègrent aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les API <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>, consultez <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Pour en savoir plus sur le suivi d’événements dans Windows, consultez [Améliorez le débogage et l’optimisation des performances avec ETW](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Suppression d'EventProvider  
 Cet exemple utilise la classe <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType>, qui implémente <xref:System.IDisposable?displayProperty=nameWithType>. Lors de l'implémentation du suivi pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], il est probable que vous utilisiez les ressources de <xref:System.Diagnostics.Eventing.EventProvider> pour la durée de vie du service. Pour cette raison, et à des fins de lisibilité, cet exemple ne supprime jamais l'<xref:System.Diagnostics.Eventing.EventProvider> inclus dans un wrapper. Si pour une raison ou une autre, les exigences de votre service diffèrent en matière de suivi et que vous devez supprimer cette ressource, modifiez cet exemple conformément aux meilleures pratiques de suppression de ressources non managées. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]suppression des ressources non managées, consultez [implémentant une méthode de suppression](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Auto-hébergement et Hébergement Web  
 Pour les services hébergés sur le Web, les traces analytiques de WCF fournissent un champ nommé « HostReference », qui est utilisé pour identifier le service qui émet les traces. Les traces utilisateur extensibles peuvent participer à ce modèle et cet exemple en illustre les meilleures pratiques. Le format d’un hôte Web référencer lorsque le canal ' &#124;' caractères apparaît réellement dans la boîte chaîne peut prendre l’une des opérations suivantes :  
  
-   Si l'application ne se situe pas à la racine.  
  
     \<SiteName >\<ApplicationVirtualPath > &#124;\< ServiceVirtualPath > &#124; \<ServiceName >  
  
-   Si l'application se situe à la racine.  
  
     \<SiteName > &#124; \<ServiceVirtualPath > &#124; \<ServiceName >  
  
 Pour les services auto-hébergés, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de traces analytiques ne remplissent pas le champ « HostReference ». La classe `WCFUserEventProvider` de cet exemple se comporte de manière cohérente lorsqu'elle est utilisée par un service auto-hébergé.  
  
## <a name="custom-event-details"></a>Informations sur l'événement personnalisé  
 Le manifeste du fournisseur d'événements ETW de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] définit trois événements conçus par les auteurs du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour être émis depuis le code du service. Le tableau suivant détaille ces trois événements.  
  
|Événement|Description|ID d'événement|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Émettez cet événement lorsqu'un fait remarquable, qui n'est pas un problème, se produit dans votre service. Par exemple, vous pouvez émettre un événement après qu'un appel à une base de données a abouti.|301|  
|UserDefinedWarningOccurred|Émettez cet événement lorsqu'un problème susceptible d'aboutir à un échec se produit. Par exemple, vous pouvez émettre un événement d'avertissement lorsqu'un appel à une base de données a échoué, mais que vous avez pu recourir à une banque de données redondante.|302|  
|UserDefinedErrorOccurred|Émettez cet événement lorsque votre service ne se comporte pas comme prévu. Par exemple, vous pouvez émettre un événement si un appel à une base de données a échoué et que vous n'avez pas pu récupérer les données ailleurs.|303|  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution WCFAnalyticTracingExtensibility.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
     Dans le navigateur Web, cliquez sur **Calculator.svc**. L'URI du document WSDL du service doit s'afficher dans le navigateur. Copiez cet URI.  
  
4.  Exécutez le client test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (WcfTestClient.exe).  
  
     Le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test (WcfTestClient.exe) se trouve dans le \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Répertoire_installation_ > \Common7\IDE\ WcfTestClient.exe (valeur par défaut [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] est C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  Dans le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client de test, ajoutez le service en sélectionnant **fichier**, puis **ajouter un Service**.  
  
     Ajoutez l'adresse du point de terminaison dans la zone d'entrée.  
  
6.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
     Le service ICalculator est ajouté dans le volet gauche sous **Mes projets de Service**.  
  
7.  Ouvrez l'application Observateur d'événements.  
  
     Avant d'appeler le service, démarrez l'Observateur d'événements et vérifiez que le journal des événements écoute les événements de suivi émis à partir du service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
8.  À partir de la **Démarrer** menu, sélectionnez **outils d’administration**, puis **Observateur d’événements**. Activer la **analyse** et **déboguer** journaux.  
  
9. Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis **Serveur d’applications-Applications**. Avec le bouton droit **serveur d’applications-Applications**, sélectionnez **vue**, puis **afficher les journaux d’analyse et de débogage**.  
  
     Vérifiez que le **afficher les journaux d’analyse et de débogage** option est activée. Activer la **analyse** journal.  
  
     Dans l’arborescence de commandes dans l’Observateur d’événements, accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**, puis **analytique**. Avec le bouton droit **analyse** et sélectionnez **activer le journal**.  
  
10. Testez le service à l'aide du client test WCF.  
  
    1.  Dans le Client Test WCF, double-cliquez sur **Add()** sous le nœud du service ICalculator.  
  
         Le **Add()** méthode s’affiche dans le volet droit avec deux paramètres.  
  
    2.  Tapez 2 pour le premier paramètre et 3 pour le deuxième.  
  
    3.  Cliquez sur **Invoke** pour appeler la méthode.  
  
11. Accédez à la **Observateur d’événements** fenêtre que vous avez déjà ouverte. Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, **Application Les Applications serveur**.  
  
12. Cliquez sur le **analyse** nœud et sélectionnez **Actualiser**.  
  
     Les événements s'affichent dans le volet droit.  
  
13. Trouvez l'événement avec l'ID 303 et double-cliquez dessus pour l'ouvrir et en inspecter le contenu.  
  
     Cet événement a été émis par le `Add()` méthode du service ICalculator et a une charge utile égale à « 2 + 3 = 5 ».  
  
#### <a name="to-clean-up-optional"></a>Pour nettoyer (facultatif)  
  
1.  Ouvrez **Observateur d’événements**.  
  
2.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**, puis  **Serveur d’applications-Applications**. Avec le bouton droit **analyse** et sélectionnez **désactiver le journal**.  
  
3.  Accédez à **Observateur d’événements**, **journaux des Applications et Services**, **Microsoft**, **Windows**,  **Serveur d’applications-Applications**, puis **analytique**. Avec le bouton droit **analyse** et sélectionnez **effacer le journal**.  
  
4.  Cliquez sur **effacer** pour effacer les événements.  
  
## <a name="known-issue"></a>Problème connu  
 Il existe un problème connu dans le **Observateur d’événements** où il peut échouer décoder des événements ETW. Vous pouvez voir un message d’erreur indiquant : « la description de l’ID d’événement \<id > à partir de la source Microsoft-Windows-Application Server-Applications est introuvable. Le composant qui a déclenché cet événement n'est pas installé sur l'ordinateur local ou l'installation est endommagée. Vous pouvez installer ou réparer le composant sur l’ordinateur local. » Si vous rencontrez cette erreur, sélectionnez **Actualiser** à partir de la **Actions** menu. Le décodage de l'événement doit ensuite s'effectuer correctement.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
