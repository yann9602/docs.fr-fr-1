---
title: "Comment&#160;: afficher le composant PrintDialog | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Imprimer (boîte de dialogue), afficher"
  - "PrintDialog (composant Windows Forms), afficher"
  - "imprimer (Windows Forms), afficher la boîte de dialogue Imprimer"
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: afficher le composant PrintDialog
Le composant <xref:System.Windows.Forms.PrintDialog> est la boîte de dialogue d'impression Windows standard, familière à la plupart de vos utilisateurs.  Étant donné que vos utilisateurs sauront d'emblée utiliser cette boîte de dialogue, il serait judicieux d'utiliser le composant <xref:System.Windows.Forms.PrintDialog>.  
  
### Pour afficher le composant PrintDialog  
  
-   Appelez la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A> à partir du code de votre application.  
  
     Le composant une fois affiché, les utilisateurs pourront interagir avec lui pour définir les propriétés du travail d'impression.  Celles\-ci sont enregistrées dans la classe [PrinterSettings](frlrfSystemDrawingPrintingPrinterSettingsMembersTopic) \(et dans la classe [PageSettings](frlrfSystemDrawingPrintingPageSettingsMembersTopic), si l'utilisateur accède à [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) via le composant <xref:System.Windows.Forms.PrintDialog>\) associée à ce travail d'impression.  Vous pouvez créer des appels aux propriétés qu'elles définissent pour déterminer les caractéristiques du travail d'impression.  
  
## Voir aussi  
 [Comment : créer des travaux d'impression Windows Forms standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)   
 [Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)   
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [PrintDialog, composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)