---
title: "Activation bas&#233;e sur la configuration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Activation bas&#233;e sur la configuration
Cet exemple montre comment activer des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sans avoir à utiliser un fichier .svc.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## Détails de l'exemple  
 Dans cet exemple, le client est le client de test [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et le service est hébergé dans IIS.  
  
> [!NOTE]
>  Les instructions d'installation et de génération correspondant à cet exemple figurent en fin de rubrique.  
  
### Activation de services sans avoir à utiliser de fichier .svc  
 Dans [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], un fichier .svc était requis pour activer un service.Cela générait une charge de gestion supplémentaire, en raison du déploiement et de la maintenance nécessaires d'un fichier supplémentaire avec l'application.Avec le lancement de [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], les composants d'activation peuvent être configurés à l'aide du fichier de configuration de l'application.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] introduit un nouvel élément de configuration \(<xref:System.ServiceModel.Configuration.ServiceActivationElement>\), dans le <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> du fichier de configuration de l'application.La collection <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> accepte une collection de services à activer, comme le montre l'exemple de code suivant.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
  
```  
  
 L'observation à formuler est que la configuration semble très similaire à celle de fichiers .svc.Un attribut supplémentaire, `relativeAddress`, qui fournit l'adresse du service, a été introduit.L'adresse relative constitue également le chemin d'accès virtuel du service.L'hôte récupère le fichier Web.config du fichier à partir de l'emplacement `virtualPath`, s'il existe ; sinon, l'hôte effectue une recherche récursive dans son dossier parent.  
  
> [!NOTE]
>  Pour fonctionner, cet exemple requiert un hébergement dans IIS.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier Service.csproj.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Testez le service en exécutant WCFTestClient.exe.  
  
4.  À l'aide de l'[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], naviguez jusqu'au dossier %SystemDrive%\\Program Files\\Microsoft Visual Studio 10.0\\Common7\\IDE.  
  
5.  Exécutez WcfTestClient.exe.  
  
6.  Définissez l'adresse MEX du service.  
  
7.  Appuyez sur CTRL\+MAJ\+A pour définir l'adresse du service.  
  
8.  Définissez l'adresse http:\/\/localhost\/ServiceModelSamples\/Calculator.svc.  
  
9. Effectuez l'opération `Add`.Affectez au paramètre `n1` la valeur 10 et au paramètre `n2` la valeur 15.  
  
10. Cliquez sur **Appeler**.  
  
     Le résultat attendu est 25.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Une fois la solution générée, exécutez Setup.bat pour installer l'application ServiceModelSamples dans IIS.Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application IIS.  
  
4.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## Voir aussi  
 [Hébergement AppFabric et exemples de persistance](http://go.microsoft.com/fwlink/?LinkId=193961)