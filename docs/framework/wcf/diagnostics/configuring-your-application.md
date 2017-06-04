---
title: "Configuration de votre application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2f995b0-669d-4721-b00f-4561ec7eb6a4
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Configuration de votre application
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise le système de configuration .NET et vous permet de configurer des services à la fois au niveau de l'ordinateur et au niveau de l'application.  
  
 Les paramètres de configuration définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se trouvent dans le groupe de sections `<system.serviceModel>` .[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la configuration d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez les rubriques suivantes :  
  
-   [Configuration des services](../../../../docs/framework/wcf/configuring-services.md)  
  
-   [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
 Les paramètres de configuration définis par l'application sont définis dans le groupe de sections `<appSettings>`.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les paramètres d'application dans les fichiers de configuration .NET, consultez [\<appSettings\>](http://go.microsoft.com/fwlink/?LinkId=95159).  
  
## Utilisation de l'Éditeur de configuration  
 L'[Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permet aux administrateurs et aux développeurs de créer et de modifier des paramètres de configuration pour les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'une interface utilisateur graphique.Cet outil vous permet de gérer les paramètres de liaison, comportement, service et diagnostic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sans modifier directement les fichiers de configuration XML.  
  
## Modification des fichiers de configuration dans Visual Studio  
 Pour modifier le fichier de configuration d'un projet de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], cliquez dessus avec le bouton droit dans l'**Explorateur de solutions** et choisissez l'élément de menu contextuel **Modifier la configuration WCF**.[Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) démarre.  
  
> [!NOTE]
>  Si vous modifiez le fichier de configuration d'un projet de service Web [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] en cliquant avec le bouton droit sur l'**Explorateur de solutions**, remarquez que l'élément de menu contextuel **Modifier la configuration WCF** est manquant.Pour résoudre ce problème, cliquez sur le menu **Outils** et sélectionnez **Éditeur de configuration de service WCF**.Ensuite, vous pouvez cliquer avec le bouton droit sur un fichier de configuration et utiliser l'élément de menu contextuel **Modifier la configuration WCF**.  
  
## Voir aussi  
 [Outil Éditeur de configuration \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)   
 [Configuration des services](../../../../docs/framework/wcf/configuring-services.md)   
 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)