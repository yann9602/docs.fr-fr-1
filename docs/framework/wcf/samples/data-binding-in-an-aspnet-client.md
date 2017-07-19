---
title: "Data Binding in an ASP.NET Client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# Data Binding in an ASP.NET Client
Cet exemple indique comment lier des données retournées par un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] standard dans une application Web Forms.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 Cet exemple présente un service qui implémente un contrat définissant un modèle de communication demande\-réponse.Il se compose d'une application Web Forms cliente accessible à partir d'un navigateur, et d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergé par les services Internet \(IIS\).  
  
 Le service implémente un contrat qui définit un modèle de communication demande\-réponse.Le contrat est défini par l'interface `IWeatherService`, laquelle expose une opération appelée `GetWeatherData`.Cette opération accepte un tableau de villes et retourne un tableau d'objets `WeatherData` qui représente les prévisions de températures maximales et minimales d'une ville.  
  
 Sur la page .aspx du client [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], un contrôle Web DataGrid est défini et contient la représentation graphique des données retournées par le service.Le code sur la page .aspx appelle le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et retourne les données météorologiques dans un tableau d'objets `WeatherData`.DataGrid indique où obtenir ses données en affectant ce tableau à sa propriété `DataSource`.La liaison de données se produit avec un appel à la méthode `DataBind` de DataGrid.L'ensemble de ce code étant situé dans la méthode `Page_Load` de la page `aspx`, les données sont mises à jour dans DataGrid chaque fois que l'utilisateur actualise la page du navigateur.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Le client de cet exemple est un site Web qui s'exécute sous un serveur Web de développement.Pour lancer le serveur Web de développement, tapez la commande suivante à l'invite : "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.Puis accédez à http:\/\/localhost:8000\/client.Pour exécuter cet exemple sur plusieurs ordinateurs, remplacez toutes les références à `localhost` dans le fichier Web.config du client par le nom d'ordinateur du serveur.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## Voir aussi