---
title: "Suivi à l'aide d'un fichier texte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a2725c34b79b8c9dd05a9f9a071ef52e29527e02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="tracking-using-a-text-file"></a>Suivi à l'aide d'un fichier texte
Cet exemple montre comment étendre le suivi dans [!INCLUDE[wf](../../../../includes/wf-md.md)] en créant un participant de suivi personnalisé. Les participants de suivi sont des classes .NET Framework qui reçoivent des enregistrements de suivi du runtime lorsqu'ils sont émis. Vous pouvez créer un participant de suivi pour transporter les événements de suivi vers toute destination qui est requise pour votre scénario. Par exemple, le participant de suivi ETW (Event Tracing for Windows, suivi d'événements pour Windows) est fourni dans le cadre du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. Dans cet exemple, le participant de suivi écrit les enregistrements au format XML dans un fichier texte.  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Pour optimiser l'utilité et la fiabilité de votre participant de suivi, certaines étapes supplémentaires doivent être effectuées pour connecter correctement le participant de suivi au runtime. Le tableau suivant décrit les classes utilisées dans cet exemple pour créer un participant de suivi qui soit conforme aux meilleures pratiques.  
  
|Classe|Description|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|Un <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> est utilisé pour définir la section de configuration utilisée pour configurer le participant de suivi de fichier texte. Cela permet aux utilisateurs de spécifier la destination du fichier journal à l'aide de fichiers de configuration .NET Framework standard.|  
|`TextFileTrackingBehavior`|Les comportements dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettent aux utilisateurs d'injecter des extensions dans le runtime. Ce comportement ajoute le participant de suivi au service lors du démarrage de ce dernier.|  
|`TextFileTrackingParticipant`|Participant de suivi qui reçoit des participants de suivi au moment de l'exécution et les stocke à un fichier journal au format XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Configuration des éléments d'extension de comportement  
 Une étape supplémentaire est requise pour utiliser l'élément d'extension de comportement décrite précédemment à l'aide de fichiers de configuration .NET Framework. La configuration suivante doit être placée dans les fichiers de configuration où l'extension doit être utilisée.  
  
```xml  
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
  
## <a name="custom-tracking-records"></a>Enregistrements de suivi personnalisé  
 Le fichier GetStockPrices.cs montre comment créer des enregistrements de suivi personnalisé à partir d'un <xref:System.Activities.CodeActivity>. Recherchez cet enregistrement lorsque l'exemple est exécuté.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution WFStockPriceApplication.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
     La fenêtre du navigateur s'ouvre et affiche la liste des répertoires pour l'application.  
  
4.  Dans le navigateur, cliquez sur StockPriceService.xamlx.  
  
5.  Le navigateur affiche le **StockPriceService** page qui contient l’adresse wsdl du service local. Copiez cette adresse.  
  
     L'adresse WSDL du service local est, par exemple, http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], accédez à votre dossier [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (le dossier d'installation par défaut est %SystemDrive%\Program Files\Microsoft Visual Studio 10.0). Recherchez le sous-dossier Common7\IDE.  
  
7.  Double-cliquez sur le fichier WcfTestClient.exe pour lancer le client test WCF.  
  
8.  Dans le Client Test WCF, sélectionnez **ajouter un Service en cours...** à partir de la **fichier** menu.  
  
9. Collez l'URL que vous venez de copier dans la zone de texte.  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
11. Testez le service à l'aide du client test WCF.  
  
    1.  Dans le Client Test WCF, double-cliquez sur **GetStockPrice()** sous le **IStockPriceService** nœud.  
  
         Le **GetStockPrice()** méthode s’affiche dans le volet droit, avec un paramètre.  
  
    2.  Tapez Contoso comme valeur pour le paramètre.  
  
    3.  Cliquez sur **appeler**.  
  
12. Consultez les événements suivis dans le fichier journal situé dans votre répertoire de données d'application dans %APPDATA%\trackingRecords.log.  
  
    > [!NOTE]
    >  %AppData% est une variable d’environnement qui se résout en %SystemDrive%\Users\\< nom d’utilisateur\>\AppData\Roaming dans [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ou Windows Server 2008.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’analyse AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
