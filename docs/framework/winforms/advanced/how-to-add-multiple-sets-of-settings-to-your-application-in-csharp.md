---
title: "Comment&#160;: ajouter plusieurs jeux de param&#232;tres &#224; votre application en C# | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "paramètres d'application (Windows Forms), C#"
  - "paramètres d'application (Windows Forms), jeux multiples"
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: ajouter plusieurs jeux de param&#232;tres &#224; votre application en C# #
Dans certains cas, vous pouvez souhaiter avoir plusieurs jeux de paramètres dans une application.  Par exemple, si vous développez une application où un groupe particulier de paramètres est supposé changer fréquemment, il est recommandé de les placer dans un fichier unique afin que ce dernier puisse être globalement remplacé, sans que d'autres paramètres ne soient affectés.  Visual Studio vous permet d'ajouter plusieurs jeux de paramètres à votre projet.  Il est possible d'accéder aux jeux de paramètres supplémentaires via l'objet Properties.Settings.  
  
### Pour ajouter un jeu supplémentaire de paramètres à votre application  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  La boîte de dialogue **Ajouter un nouvel élément** s'ouvre.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Fichier de paramètres**, tapez un nom pour le fichier et cliquez sur **Ajouter** pour ajouter un nouveau fichier de paramètres à votre solution.  
  
3.  Dans l'**Explorateur de solutions**, faites glisser le nouveau fichier de paramètres dans le dossier **Propriétés**.  Vos nouveaux paramètres sont ainsi disponibles dans le code.  
  
4.  Ajoutez et utilisez des paramètres dans ce fichier comme vous le feriez dans n'importe quel autre fichier de paramètres.  Vous pouvez accéder à ce groupe de paramètres via l'objet Properties.Settings.  
  
## Voir aussi  
 [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)