---
title: "Vue d&#39;ensemble du contr&#244;le PrintPreviewDialog (Windows Forms) | Microsoft Docs"
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
  - "PrintPreviewDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintPreviewDialog (contrôle du concepteur), à propos de PrintPreviewDialog"
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Vue d&#39;ensemble du contr&#244;le PrintPreviewDialog (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> est une boîte de dialogue préconfigurée utilisée pour afficher un [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) tel qu'il apparaîtra à l'impression.  L'utilisation de ce contrôle dans votre application Windows est plus simple que de configurer votre propre boîte de dialogue.  Ce contrôle contient des boutons destinés à l'impression, au zoom avant, à l'affichage d'une ou de plusieurs pages et à la fermeture de la boîte de dialogue.  
  
## Propriétés et méthodes principales  
 La principale propriété de ce contrôle est <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, qui définit le document à afficher.  Le document doit être un objet <xref:System.Drawing.Printing.PrintDocument>.  Pour afficher la boîte de dialogue, vous devez appeler sa méthode <xref:System.Windows.Forms.Form.ShowDialog%2A>.  L'anticrénelage peut donner au texte un aspect plus lisse, mais aussi ralentir l'affichage ; pour l'utiliser, attribuez à la propriété <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> la valeur `true`.  
  
 Certaines propriétés sont disponibles par le biais du contrôle <xref:System.Windows.Forms.PrintPreviewControl> contenu dans le contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  \(vous n'avez pas besoin d'ajouter le contrôle <xref:System.Windows.Forms.PrintPreviewControl> au formulaire ; il est automatiquement contenu dans le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> lorsque vous ajoutez la boîte de dialogue au formulaire\). Les propriétés disponibles par le biais du <xref:System.Windows.Forms.PrintPreviewControl> sont par exemple <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> et <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> qui déterminent le nombre de pages affichées horizontalement et verticalement dans le contrôle.  Vous pouvez accéder à la propriété <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> comme `PrintPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou `printPreviewDialog1->PrintPreviewControl->Columns` en [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## Voir aussi  
 <xref:System.Windows.Forms.PrintPreviewDialog>   
 [Vue d'ensemble du contrôle PrintPreviewControl](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)   
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [Contrôles et composants de boîte de dialogue](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)