---
title: "Vue d&#39;ensemble du composant OpenFileDialog (Windows Forms) | Microsoft Docs"
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
  - "OpenFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Ouvrir un fichier (boîte de dialogue), afficher dans les Windows Forms"
  - "OpenFileDialog (composant), à propos d'OpenFileDialog"
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du composant OpenFileDialog (Windows Forms)
Le composant Windows Forms <xref:System.Windows.Forms.OpenFileDialog> est une boîte de dialogue préconfigurée.  Il est identique à la boîte de dialogue **Ouvrir un fichier** exposée par le système d'exploitation Windows.  Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.  
  
## Utilisation de ce Composant  
 L'utilisation de ce composant dans votre application Windows plutôt que de configurer votre propre boîte de dialogue vous offre un moyen simple de sélectionner des fichiers.  En ayant recours aux boîtes de dialogue Windows standard, vous créez des applications dont les fonctionnalités de base sont d'emblée familières aux utilisateurs.  Sachez toutefois que lorsque l'utilisation du composant <xref:System.Windows.Forms.OpenFileDialog> exige l'écriture de votre propre logique d'ouverture de fichier.  
  
 Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l'exécution.  Vous pouvez permettre aux utilisateurs de sélectionner plusieurs fichiers à ouvrir avec la propriété <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>.  En outre, vous pouvez utiliser la propriété <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> pour déterminer si une case à cocher en lecture seule apparaîtra dans la boîte de dialogue.  La propriété <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> indique si la case à cocher en lecture seule est sélectionnée.  Enfin, la propriété <xref:System.Windows.Forms.FileDialog.Filter%2A> définit la chaîne de filtre du nom de fichier en cours, laquelle détermine les choix proposés dans la zone « Types de fichiers » de la boîte de dialogue.  
  
 Lorsque le composant <xref:System.Windows.Forms.OpenFileDialog> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog, composant](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)