---
title: "S&#233;rialisation de g&#233;n&#233;riques de services Web, exemple de technologie | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# S&#233;rialisation de g&#233;n&#233;riques de services Web, exemple de technologie
[Télécharger l'exemple](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Cet exemple montre comment utiliser et contrôler la sérialisation de génériques dans les services Web ASP.NET.  
  
### Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Ouvrez Visual Studio et sélectionnez **Nouveau site Web** dans le menu **Fichier**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Nouveau site Web**, sélectionnez le langage de programmation de votre choix, puis dans le volet droit, sélectionnez **Service Web ASP.NET**.  
  
3.  Cliquez sur **Parcourir** et accédez au sous\-répertoire \\CS\\GenericsService.  
  
4.  Sélectionnez Service.asmx pour ouvrir le fichier dans Visual Studio.  
  
5.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
> [!NOTE]
>  Les cinq premières étapes de cette liste sont facultatives.L'exécution .NET Framework générera automatiquement le service Web lors de la première demande du service.  
  
> [!NOTE]
>  Les étapes suivantes sont obligatoires pour générer l'exemple.  
  
1.  Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez au sous\-répertoire \\CS.  
  
2.  Cliquez avec le bouton droit sur l'icône du sous\-répertoire GenericsService et sélectionnez **Partage et sécurité**.  
  
3.  Sous l'onglet **Partage Web**, sélectionnez **Partager ce dossier**.  
  
> [!IMPORTANT]
>  Notez le nom du répertoire virtuel répertorié dans le volet **Alias**, car vous en aurez besoin pour exécuter l'exemple.  
  
### Pour générer l'exemple à l'aide des services IIS \(Internet Information Services\)  
  
1.  Ouvrez le composant logiciel enfichable de gestion **Internet Information Services** et développez **Sites Web**.  
  
2.  Cliquez sur **Site Web par défaut**, sélectionnez **Nouveau**, puis **Répertoire virtuel** pour créer l'**Assistant Création de répertoire virtuel**.  
  
3.  Cliquez sur **Suivant**, entrez l'alias public pour votre répertoire virtuel et cliquez sur **Suivant**.  
  
4.  Entrez le chemin d'accès au répertoire où vous avez enregistré l'exemple \(il s'agit, en principe, du sous\-répertoire \\CS\\GenericsService\) et cliquez sur **Suivant**.Cliquez sur **Suivant** pour quitter l'Assistant.  
  
> [!IMPORTANT]
>  Notez le nom du répertoire virtuel répertorié dans le volet **Alias**, car vous en aurez besoin pour exécuter l'exemple.  
  
### Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de navigateur et sélectionnez sa barre d'adresses.  
  
2.  Tapez **http:\/\/localhost\/**\[répertoire virtuel\]**\/Service.asmx**, où \[répertoire virtuel\] représente le répertoire virtuel que vous avez créé au moment de la construction de l'exemple.  
  
## Notes  
 L'exemple affiche une page ASP.NET par défaut qui contient des liens vers la définition du service Web.Vous pouvez modifier le code source pour le service Web, mais également personnaliser l'affichage.Pour plus d'informations, consultez [Building XML Web Service Clients](http://msdn.microsoft.com/fr-fr/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 <xref:System.Web.Services>   
 <xref:System.Xml.Serialization>   
 [Sérialisation](../../../docs/framework/serialization/index.md)   
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/fr-fr/1e64af78-d705-4384-b08d-591a45f4379c)