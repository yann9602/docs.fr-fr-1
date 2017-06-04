---
title: "Comment&#160;: modifier l&#39;apparence du composant ColorDialog Windows Forms | Microsoft Docs"
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
  - "boîte de dialogue des couleurs, configurer l'apparence"
  - "ColorDialog (composant), exemples"
  - "ColorDialog (composant), mettre en forme l'apparence"
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: modifier l&#39;apparence du composant ColorDialog Windows Forms
Vous pouvez configurer l'apparence du composant <xref:System.Windows.Forms.ColorDialog> Windows Forms en utilisant plusieurs de ses propriétés.  La boîte de dialogue se compose de deux parties : une qui montre les couleurs de base et une autre qui permet à l'utilisateur de définir des couleurs personnalisées.  
  
 La plupart des propriétés limitent le nombre de couleurs que l'utilisateur peut sélectionner dans la boîte de dialogue.  Si la propriété <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> a la valeur `true`, l'utilisateur est autorisé à définir des couleurs personnalisées.  La propriété <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> a la valeur `true` si la boîte de dialogue est développée pour permettre de définir des couleurs personnalisées ; sinon l'utilisateur doit cliquer sur un bouton "Définir des couleurs personnalisées".  Lorsque la propriété <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> a la valeur `true`, la boîte de dialogue affiche toutes les couleurs de base disponibles.  Si la propriété <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> a la valeur `true`, l'utilisateur ne peut pas sélectionner de couleurs tramées ; seules les couleurs unies sont mises à sa disposition.  
  
 Si la propriété <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> a la valeur `true`, un bouton Aide apparaît dans la boîte de dialogue.  Lorsque l'utilisateur clique sur le bouton Aide, l'événement <xref:System.Windows.Forms.CommonDialog.HelpRequest> du composant <xref:System.Windows.Forms.ColorDialog> est déclenché.  
  
### Pour configurer l'apparence de la boîte de dialogue des couleurs  
  
1.  Affectez aux propriétés <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> et <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> les valeurs souhaitées.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ColorDialog>   
 [ColorDialog, composant](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)   
 [Vue d'ensemble du composant ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)