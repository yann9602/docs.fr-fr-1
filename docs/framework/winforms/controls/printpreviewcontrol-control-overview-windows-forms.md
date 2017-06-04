---
title: "Vue d&#39;ensemble du contr&#244;le PrintPreviewControl (Windows Forms) | Microsoft Docs"
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
  - "PrintPreviewControl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "aperçu avant impression"
  - "PrintPreviewControl (contrôle)"
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble du contr&#244;le PrintPreviewControl (Windows Forms)
Le contrôle <xref:System.Windows.Forms.PrintPreviewControl> Windows Forms permet d'afficher un [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) tel qu'il apparaîtra à l'impression.  Ce contrôle ne présente pas de boutons, ni d'autres éléments d'interface utilisateur. En général, vous n'utiliserez donc le <xref:System.Windows.Forms.PrintPreviewControl> que pour écrire votre propre interface utilisateur d'aperçu avant impression.  Si vous souhaitez l'interface utilisateur standard, utilisez un contrôle <xref:System.Windows.Forms.PrintPreviewDialog> ; consultez [Vue d'ensemble du contrôle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) pour une vue d'ensemble.  
  
## Propriétés de clé  
 La principale propriété de ce contrôle est <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, qui définit le document à afficher.  Le document doit être un objet <xref:System.Drawing.Printing.PrintDocument>.  Pour une vue d'ensemble de la création de documents à imprimer, consultez [Vue d'ensemble du composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) et [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).  Les propriétés <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> déterminent le nombre de pages affichées horizontalement et verticalement dans le contrôle.  L'anticrénelage peut donner au texte un aspect plus lisse, mais aussi ralentir l'affichage ; pour l'utiliser, attribuez à la propriété <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> la valeur `true`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.PrintPreviewControl>   
 [Vue d'ensemble du contrôle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)   
 [PrintPreviewControl, contrôle](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)   
 [Contrôles et composants de boîte de dialogue](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)