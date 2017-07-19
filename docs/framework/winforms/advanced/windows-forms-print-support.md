---
title: "Prise en charge de l&#39;impression dans les Windows Forms | Microsoft Docs"
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
  - "formulaires, imprimer (à l'aide du concepteur)"
  - "imprimer (Windows Forms)"
  - "imprimer (Windows Forms), prise en charge de l'impression"
  - "imprimer, Windows Forms, prise en charge"
  - "Windows Forms, imprimer"
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Prise en charge de l&#39;impression dans les Windows Forms
L'impression dans les Windows Forms revient essentiellement à utiliser le composant [PrintDocument, composant](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) pour permettre à l'utilisateur d'imprimer, et le contrôle [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) et les composants [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) et [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) pour fournir une interface graphique familière aux utilisateurs habitués au système d'exploitation Windows.  
  
 En règle générale, vous créez une nouvelle instance du composant <xref:System.Drawing.Printing.PrintDocument>, vous définissez les propriétés qui décrivent les éléments à imprimer à l'aide des classes <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings>, puis vous appelez la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour procéder à l'impression du document.  
  
 Au cours d'une impression initialisée dans une application Windows, le composant <xref:System.Drawing.Printing.PrintDocument> affiche une boîte de dialogue d'annulation d'impression afin d'avertir les utilisateurs de l'impression en cours et de leur permettre d'annuler le travail d'impression.  
  
## Dans cette section  
 [Comment : créer des travaux d'impression Windows Forms standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Explique comment utiliser le composant <xref:System.Drawing.Printing.PrintDocument> pour imprimer à partir d'un Windows Form.  
  
 [Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Explique comment utiliser le composant <xref:System.Windows.Forms.PrintDialog> pour modifier par programme les options d'impression sélectionnées.  
  
 [Comment : choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans Windows Forms](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Décrit la modification de l'imprimante chargée de l'impression à l'aide du composant <xref:System.Windows.Forms.PrintDialog> au moment de l'exécution.  
  
 [Comment : imprimer des graphiques dans Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Décrit l'envoi de graphismes à l'imprimante.  
  
 [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Décrit l'envoi de texte à l'imprimante.  
  
 [Comment : terminer des travaux d'impression Windows Forms](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Explique comment prévenir les utilisateurs qu'un travail d'impression est terminé.  
  
 [Comment : imprimer un Windows Form](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Montre comment imprimer une copie du formulaire actuel.  
  
 [Comment : imprimer dans les Windows Forms en utilisant l'aperçu avant impression](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Montre comment utiliser une <xref:System.Windows.Forms.PrintPreviewDialog> pour l'impression d'un document.  
  
## Rubriques connexes  
 [PrintDocument, composant](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Explique comment utiliser le composant <xref:System.Drawing.Printing.PrintDocument>.  
  
 [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Explique comment utiliser le composant <xref:System.Windows.Forms.PrintDialog>.  
  
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Explique comment utiliser le contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
 [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Explique comment utiliser le composant <xref:System.Windows.Forms.PageSetupDialog>.  
  
 <xref:System.Drawing.Printing>  
 Décrit les classes dans l'espace de noms <xref:System.Drawing.Printing>.