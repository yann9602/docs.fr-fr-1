---
title: "Configuration Channel Factory | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Configuration Channel Factory
Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.Le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet une gestion centralisée de la configuration du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Celle\-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.  
  
## Démonstrations  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## Discussion  
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.  
  
 Cet exemple est composé de deux projets.Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients.Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service.Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.  
  
 Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
  
```  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec les privilèges d'administrateur.  
  
2.  Cliquez avec le bouton droit sur la solution ConfigurationChannelFactory \(2 projets\) et sélectionnez **Propriétés**.  
  
3.  Dans **Propriétés communes**, sélectionnez **Projet de démarrage**, puis cliquez sur **Plusieurs projets de démarrage**.  
  
4.  Déplacez le projet **Service** vers le début de la liste, avec l'**action de démarrage**, puis déplacez le projet **Client** après le projet **Service**, toujours avec l'**action de démarrage**, de sorte que le projet **Client** soit exécuté après le projet **Service**.  
  
5.  Cliquez sur **OK**, puis appuyez sur F5 \(ou CTRL\+F5\) pour exécuter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`