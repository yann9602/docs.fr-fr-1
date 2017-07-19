---
title: "Vue d&#39;ensemble du composant PageSetupDialog (Windows Forms) | Microsoft Docs"
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
  - "PageSetupDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Mise en page (boîte de dialogue), afficher"
  - "PageSetupDialog (composant)"
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du composant PageSetupDialog (Windows Forms)
Le composant <xref:System.Windows.Forms.PageSetupDialog> Windows Forms est une boîte de dialogue préconfigurée utilisée pour définir la configuration d'impression d'une page dans des applications Windows.  En employant ce contrôle dans votre application Windows plutôt que de configurer votre propre boîte de dialogue, vous offrirez aux utilisateurs un moyen simple de définir les préférences de page.  De cette façon, vous permettez aux utilisateurs de définir la taille des bordures et des marges, les en\-têtes et pieds de page, ainsi que l'orientation portrait ou paysage.  En ayant recours aux boîtes de dialogue Windows standard, vous créez des applications dont les fonctionnalités de base sont d'emblée familières aux utilisateurs.  
  
## Propriétés et méthodes principales  
 Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue au moment de l'exécution.  Ce composant possède des propriétés que vous pouvez définir pour une page unique \(classe <xref:System.Drawing.Printing.PrintDocument>\) ou pour tout document \(classe <xref:System.Drawing.Printing.PageSettings>\).  En outre, le composant <xref:System.Windows.Forms.PageSetupDialog> peut être utilisé pour déterminer des paramètres d'impression spécifiques stockés dans la classe <xref:System.Drawing.Printing.PrinterSettings>.  
  
 Lorsque le composant <xref:System.Windows.Forms.PageSetupDialog> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.PageSetupDialog>   
 [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)