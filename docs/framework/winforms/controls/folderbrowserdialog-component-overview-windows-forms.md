---
title: "Vue d&#39;ensemble du composant FolderBrowserDialog (Windows Forms) | Microsoft Docs"
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
  - "FolderBrowserDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "répertoires (Windows Forms), activer l'exploration dans des applications"
  - "FolderBrowserDialog (composant Windows Forms), à propos de FolderBrowserDialog"
  - "dossiers (Windows Forms), activer l'exploration dans des applications"
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du composant FolderBrowserDialog (Windows Forms)
Le composant <xref:System.Windows.Forms.FolderBrowserDialog> Windows Forms est une boîte de dialogue modale utilisée pour la navigation et la sélection de dossiers.  De nouveaux dossiers peuvent également être créés dans le composant <xref:System.Windows.Forms.FolderBrowserDialog>.  
  
> [!NOTE]
>  Pour sélectionner des fichiers plutôt que des dossiers, utilisez le composant [OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md).  
  
 Le composant <xref:System.Windows.Forms.FolderBrowserDialog> s'affiche lors de l'exécution à l'aide de la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  Définissez la propriété <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> afin de déterminer le dossier de niveau le plus élevé ainsi que les sous\-dossiers qui s'affichent dans l'arborescence de la boîte de dialogue.  Une fois la boîte de dialogue affichée, vous pouvez utiliser la propriété <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> pour obtenir le chemin d'accès du dossier sélectionné.  
  
 Lorsque le composant <xref:System.Windows.Forms.FolderBrowserDialog> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [Comment : sélectionner des dossiers avec le composant FolderBrowserDialog Windows Forms](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)   
 [FolderBrowserDialog, composant](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)