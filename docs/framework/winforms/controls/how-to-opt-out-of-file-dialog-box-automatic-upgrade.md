---
title: "Comment&#160;: choisir de ne pas opter pour une mise &#224; niveau automatique des styles dans une bo&#238;te de dialogue Fichier | Microsoft Docs"
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
  - "OpenFileDialog (Windows Forms), désactiver la mise à niveau automatique"
  - "boîte de dialogue (Windows Forms), de refuser la mise à niveau automatique"
  - "Boîte de dialogue de fichier Windows Vista boîte, refuser la mise à niveau automatique"
  - "SaveFileDialog (Windows Forms), désactiver la mise à niveau automatique"
  - "AutoUpgradeEnabled (propriété)"
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: choisir de ne pas opter pour une mise &#224; niveau automatique des styles dans une bo&#238;te de dialogue Fichier
Lors de la <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> classes sont utilisées dans une application, leur apparence et leur comportement dépendent de la version de Windows, l’application est en cours d’exécution. Lorsqu’une application qui a été créée sur le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] ou antérieure est affichée sur [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> sont affichés automatiquement avec le [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] apparence et le comportement. À compter de la [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], vous pouvez désactiver la mise à niveau automatique pour afficher les <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog> avec un [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-apparence et le comportement.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Pour désactiver la mise à niveau automatique de fichier boîte de dialogue boîte  
  
1.  Définir le <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> propriété du <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog> à `false` avant d’afficher la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FileDialog>