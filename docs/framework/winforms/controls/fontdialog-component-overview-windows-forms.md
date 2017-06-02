---
title: "Vue d&#39;ensemble du composant FontDialog (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FontDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Police (boîte de dialogue)"
  - "Police (boîte de dialogue), Windows Forms"
  - "FontDialog (composant Windows Forms), à propos du composant FontDialog"
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du composant FontDialog (Windows Forms)
Le composant <xref:System.Windows.Forms.FontDialog> Windows Forms est une boîte de dialogue préconfigurée correspondant à la boîte de dialogue  **Police** standard de Windows, qui permet d'exposer les polices actuellement installées dans le système.  En employant ce contrôle dans votre application Windows plutôt que de configurer votre propre boîte de dialogue, vous offrirez aux utilisateurs un moyen simple de sélectionner des polices.  
  
 Par défaut, la boîte de dialogue affiche des zones de liste pour la police, son style et sa taille ; des cases à cocher pour obtenir un effet de barré ou de souligné ; une liste déroulante pour la sélection de scripts ; et un exemple montrant à quoi ressemblera la police.  \(Le script fait référence aux différents jeux de caractères disponibles pour une police, hébreux ou japonais, par exemple.\) Pour afficher la boîte de dialogue Police, appelez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## Propriétés de clé  
 Le composant possède un certain nombre de propriétés qui définissent son apparence.  Les propriétés qui définissent les sélections de la boîte de dialogue sont <xref:System.Windows.Forms.FontDialog.Font%2A> et <xref:System.Windows.Forms.FontDialog.Color%2A>.  La propriété <xref:System.Windows.Forms.FontDialog.Font%2A> définit la police, le style, la taille, le script et les effets ; par exemple,  `Arial, 10pt, style=Italic, Strikeout`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog, composant](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)