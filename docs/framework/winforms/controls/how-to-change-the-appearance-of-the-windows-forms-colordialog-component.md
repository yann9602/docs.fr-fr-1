---
title: "Comment : modifier l'apparence du composant ColorDialog Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11edb1019b8fedde368d712ab27dd0954a2de50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Comment : modifier l'apparence du composant ColorDialog Windows Forms
Vous pouvez configurer l’apparence des Windows Forms <xref:System.Windows.Forms.ColorDialog> composant avec un nombre de ses propriétés. La boîte de dialogue comporte deux sections : une qui affiche les couleurs de base et un type qui autorise l’utilisateur à définir des couleurs personnalisées.  
  
 La plupart des propriétés de restreindre les couleurs de l’utilisateur peut sélectionner à partir de la boîte de dialogue. Si le <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `true`, l’utilisateur est autorisé à définir des couleurs personnalisées. Le <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> propriété `true` si la boîte de dialogue est développée pour définir des couleurs personnalisées ; sinon, l’utilisateur doit cliquer un bouton « Définir les couleurs personnalisées ». Lorsque le <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> est définie sur `true`, la boîte de dialogue affiche toutes les couleurs disponibles dans le jeu de couleurs de base. Si le <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner de couleurs tramées ; uniquement des couleurs unies peuvent être sélectionnées.  
  
 Si le <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> est définie sur `true`, un bouton d’aide s’affiche dans la boîte de dialogue. Lorsque l’utilisateur clique sur le bouton aide, le <xref:System.Windows.Forms.ColorDialog> du composant <xref:System.Windows.Forms.CommonDialog.HelpRequest> événement est déclenché.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Pour configurer l’apparence de la boîte de dialogue couleur  
  
1.  Définir le <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, et <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> propriétés aux valeurs souhaitées.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog, composant](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Vue d’ensemble du composant ColorDialog](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
