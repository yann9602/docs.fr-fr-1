---
title: "Vue d&#39;ensemble du composant PrintDocument (Windows Forms) | Microsoft Docs"
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
  - "PrintDocument"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintDocument (composant Windows Forms), à propos du composant PrintDocument"
  - "imprimer (Windows Forms), PrintDocument (composant)"
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Vue d&#39;ensemble du composant PrintDocument (Windows Forms)
Le composant Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) permet de définir les propriétés spécifiant ce qui doit être imprimé, puis la possibilité d'imprimer le document dans des applications Windows.  Il peut être utilisé avec le composant [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) afin de contrôler tous les aspects de l'impression d'un document.  
  
## Utilisation du composant PrintDocument  
 Le composant <xref:System.Drawing.Printing.PrintDocument> est principalement utilisé dans les deux contextes suivants :  
  
-   Travaux d'impression simples, tels que l'impression d'un fichier texte unique.  Dans ce cas, vous devez ajouter le composant <xref:System.Drawing.Printing.PrintDocument> à un Windows Form, puis ajouter la logique de programmation qui imprime un fichier dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  La logique de programmation doit déboucher sur la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour imprimer le document.  Cette méthode envoie à l'imprimante un objet <xref:System.Drawing.Graphics> contenu dans la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs>.  Pour obtenir un exemple qui illustre comment imprimer un document texte à l'aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).  
  
-   Travaux d'impression plus complexes ; par exemple si vous souhaitez réutiliser la logique d'impression que vous avez écrite.  Dans ce cas, vous devez dériver un nouveau composant du composant <xref:System.Drawing.Printing.PrintDocument> et substituer \(voir [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md) pour Visual Basic ou [override](../Topic/override%20\(C%23%20Reference\).md) pour C\#\) l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
 Lorsque le composant <xref:System.Drawing.Printing.PrintDocument> est ajouté à un formulaire, il apparaît dans la barre d'état située au bas du Concepteur Windows Forms.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Printing.PrintDocument>   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [PrintDocument, composant](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)