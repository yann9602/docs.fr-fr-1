---
title: "Comment&#160;: d&#233;finir des info-bulles pour les contr&#244;les d&#39;un Windows Form au moment du design | Microsoft Docs"
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
  - "info-bulles (Windows Forms), pour les contrôles"
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: d&#233;finir des info-bulles pour les contr&#244;les d&#39;un Windows Form au moment du design
Vous pouvez définir une chaîne <xref:System.Windows.Forms.ToolTip> dans le code ou dans le Concepteur Windows Forms.  Pour plus d'informations sur le composant <xref:System.Windows.Forms.ToolTip>, consultez [Vue d'ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir une info\-bulle par programme  
  
1.  Ajoutez le contrôle qui affichera l'info\-bulle.  
  
2.  Utilisez la méthode <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> du composant <xref:System.Windows.Forms.ToolTip>.  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### Pour définir une info\-bulle dans le concepteur  
  
1.  Ajoutez un composant <xref:System.Windows.Forms.ToolTip> au formulaire.  
  
2.  Sélectionnez le contrôle qui affichera l'info\-bulle ou ajoutez\-en un au formulaire.  
  
3.  Dans la fenêtre **Propriétés**, attribuez à la valeur **ToolTip de ToolTip1** une chaîne de texte appropriée.  
  
## Voir aussi  
 [Vue d'ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [Comment : modifier la durée avant affichage du composant ToolTip Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)   
 [ToolTip, composant](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)