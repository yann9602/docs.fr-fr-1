---
title: "Suivi &#224; l&#39;aide d&#39;un fichier texte | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Suivi &#224; l&#39;aide d&#39;un fichier texte
Cet exemple montre comment étendre le suivi dans [!INCLUDE[wf](../../../../includes/wf-md.md)] en créant un participant de suivi personnalisé.Les participants de suivi sont des classes .NET Framework qui reçoivent des enregistrements de suivi du runtime lorsqu'ils sont émis.Vous pouvez créer un participant de suivi pour transporter les événements de suivi vers toute destination qui est requise pour votre scénario.Par exemple, le participant de suivi ETW \(Event Tracing for Windows, suivi d'événements pour Windows\) est fourni dans le cadre du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].Dans cet exemple, le participant de suivi écrit les enregistrements au format XML dans un fichier texte.  
  
## Détails de l'exemple  
 Pour optimiser l'utilité et la fiabilité de votre participant de suivi, certaines étapes supplémentaires doivent être effectuées pour connecter correctement le participant de suivi au runtime.Le tableau suivant décrit les classes utilisées dans cet exemple pour créer un participant de suivi qui soit conforme aux meilleures pratiques.  
  
|Classe|Description|  
|------------|-----------------|  
|`TextFileTrackingExtensionElement`|Un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> est utilisé pour définir la section de configuration utilisée pour configurer le participant de suivi de fichier texte.Cela permet aux utilisateurs de spécifier la destination du fichier journal à l'aide de fichiers de configuration .NET Framework standard.|  
|`TextFileTrackingBehavior`|Les comportements dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettent aux utilisateurs d'injecter des extensions dans le runtime.Ce comportement ajoute le participant de suivi au service lors du démarrage de ce dernier.|  
|`TextFileTrackingParticipant`|Participant de suivi qui reçoit des participants de suivi au moment de l'exécution et les stocke à un fichier journal au format XML.|  
  
## Configuration des éléments d'extension de comportement  
 Une étape supplémentaire est requise pour utiliser l'élément d'extension de comportement décrite précédemment à l'aide de fichiers de configuration .NET Framework.La configuration suivante doit être placée dans les fichiers de configuration où l'extension doit être utilisée.  
  
```  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
  
```  
  
> [!NOTE]
>  Pour obtenir un exemple d'utilisation complet de configuration d'éléments d'extension de comportement, consultez le fichier Web.config disponible dans l'exemple.  
  
## Enregistrements de suivi personnalisé  
 Le fichier GetStockPrices.cs montre comment créer des enregistrements de suivi personnalisé à partir d'un <xref:System.Activities.CodeActivity>.Recherchez cet enregistrement lorsque l'exemple est exécuté.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
     La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.  
  
4.  Dans le navigateur, cliquez sur StockPriceService.xamlx.  
  
5.  Le navigateur affiche la page **StockPriceService**, laquelle contient l'adresse WSDL du service local.Copiez cette adresse.  
  
     L'adresse WSDL du service local est, par exemple, http:\/\/localhost:53797\/StockPriceService.xamlx?wsdl.  
  
6.  À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], accédez à votre dossier [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] \(le dossier d'installation par défaut est %SystemDrive%\\Program Files\\Microsoft Visual Studio 10.0\).Recherchez le sous\-dossier Common7\\IDE.  
  
7.  Double\-cliquez sur le fichier WcfTestClient.exe pour lancer le client test WCF.  
  
8.  Dans le client test WCF, sélectionnez **Ajouter un service** dans le menu **Fichier**.  
  
9. Collez l'URL que vous venez de copier dans la zone de texte.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
11. Testez le service à l'aide du client test WCF.  
  
    1.  Dans le client test WCF, double\-cliquez sur **GetStockPrice\(\)** sous le nœud **IStockPriceService**.  
  
         La méthode **GetStockPrice\(\)** s'affiche dans le volet droit, avec un paramètre.  
  
    2.  Tapez Contoso comme valeur pour le paramètre.  
  
    3.  Cliquez sur **Appeler**.  
  
12. Consultez les événements suivis dans le fichier journal situé dans votre répertoire de données d'application dans %APPDATA%\\trackingRecords.log.  
  
    > [!NOTE]
    >  %APPDATA% est une variable d'environnement qui correspond à %SystemDrive%\\Users\\\<NomUtilisateur\>\\AppData\\Roaming dans [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] ou Windows Server 2008.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## Voir aussi  
 [Exemples d'analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)