---
title: "Vue d&#39;ensemble du composant SaveFileDialog (Windows Forms) | Microsoft Docs"
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
  - "SaveFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Enregistrer le fichier (boîte de dialogue), afficher"
  - "SaveFileDialog (composant), à propos de SaveFileDialog"
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du composant SaveFileDialog (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.SaveFileDialog> est une boîte de dialogue préconfigurée.  Il est identique à la boîte de dialogue **Enregistrer** le fichier standard de Windows.  Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.  
  
## Utilisation du composant SaveFileDialog  
 En employant ce contrôle dans votre application plutôt que de configurer votre propre boîte de dialogue, vous offrirez aux utilisateurs un moyen simple d'enregistrer leurs fichiers.  En ayant recours aux boîtes de dialogue Windows standard, vous créez des applications dont les fonctionnalités de base sont immédiatement familières aux utilisateurs.  Sachez toutefois que lorsque l'utilisation du composant <xref:System.Windows.Forms.SaveFileDialog> exige l'écriture de votre propre logique d'enregistrement de fichier.  
  
 Vous pouvez utiliser la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l'exécution.  Vous pouvez ouvrir un fichier en mode lecture\/écriture à l'aide de la méthode <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.  
  
 Lorsque le composant <xref:System.Windows.Forms.SaveFileDialog> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog, composant](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)