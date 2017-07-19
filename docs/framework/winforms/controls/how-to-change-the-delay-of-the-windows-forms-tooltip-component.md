---
title: "Comment&#160;: modifier la dur&#233;e avant affichage du composant ToolTip Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), info-bulles"
  - "ToolTip (composant Windows Forms), valeurs de délai"
  - "info-bulles (Windows Forms), valeurs de délai"
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: modifier la dur&#233;e avant affichage du composant ToolTip Windows Forms
Vous avez le choix entre plusieurs valeurs pour la durée avant affichage du composant <xref:System.Windows.Forms.ToolTip> Windows Forms.  L'unité de mesure de toutes ces propriétés est la milliseconde.  La propriété <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> détermine pendant combien de temps l'utilisateur doit pointer sur le contrôle associé avant que la chaîne d'info\-bulles ne s'affiche.  La propriété <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> définit le nombre de millisecondes que mettent les chaînes d'info\-bulles successives à s'afficher lorsque le pointeur de la souris se déplace d'un contrôle associé à une info\-bulle à un autre.  La propriété <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> détermine la durée pendant laquelle la chaîne d'info\-bulles reste affichée.  Vous pouvez définir ces valeurs individuellement ou attribuer une valeur à la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> ; les autres propriétés de durée sont définies en fonction de la valeur affectée à la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>.  Par exemple, lorsque la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> a la valeur de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divisée par cinq \(ou N\/5\) et <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> a une valeur égale à cinq fois la valeur de la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> \(ou 5N\).  
  
### Pour définir la durée avant affichage  
  
1.  Définissez les propriétés comme indiqué dans l'exemple suivant.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [Comment : définir des info\-bulles pour les contrôles d'un Windows Form au moment du design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [ToolTip, composant](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)