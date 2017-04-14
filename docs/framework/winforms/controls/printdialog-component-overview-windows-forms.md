---
title: "Vue d&#39;ensemble du composant PrintDialog (Windows Forms) | Microsoft Docs"
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
  - "PrintDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Imprimer (boîte de dialogue), afficher"
  - "PrintDialog (composant Windows Forms), à propos du composant PrintDialog"
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble du composant PrintDialog (Windows Forms)
Le composant [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) Windows Forms est une boîte de dialogue préconfigurée qui permet de sélectionner une imprimante, de choisir les pages à imprimer et de déterminer d'autres paramètres d'impression dans des applications Windows.  En employant ce composant dans votre application plutôt que de configurer votre propre boîte de dialogue, vous offrirez aux utilisateurs un moyen simple de sélectionner des paramètres d'impression et d'imprimante.  Ainsi, vous permettez aux utilisateurs de choisir les parties de leurs documents à imprimer : totalité du document, plusieurs pages ou partie sélectionnée.  En ayant recours aux boîtes de dialogue Windows standard, vous créez des applications dont les fonctionnalités de base sont d'emblée familières aux utilisateurs.  Le composant <xref:System.Windows.Forms.PrintDialog> hérite de la classe <xref:System.Windows.Forms.CommonDialog>.  
  
## Utilisation du composant  
 Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l'exécution.  Ce composant possède des propriétés relatives à un travail d'impression unique \(classe <xref:System.Drawing.Printing.PrintDocument>\) ou aux paramètres d'une imprimante spécifique \(classe <xref:System.Drawing.Printing.PrinterSettings>\).  L'une ou l'autre option peut, à son tour, être partagée par plusieurs imprimantes.  
  
 Lorsque le composant <xref:System.Windows.Forms.PrintDialog> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.PrintDialog>   
 [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)