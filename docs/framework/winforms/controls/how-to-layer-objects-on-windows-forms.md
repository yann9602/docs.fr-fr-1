---
title: "Comment&#160;: superposer des objets dans les Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), superposer"
  - "contrôles (Windows Forms), positionner"
  - "contrôles Windows Forms, superposer"
  - "ordre de plan"
  - "ordre z"
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: superposer des objets dans les Windows Forms
Lorsque vous créez une interface utilisateur complexe ou que vous travaillez dans un formulaire d'interface multidocument \(MDI\), il est souvent utile de superposer les contrôles et les formulaires enfants en vue de constituer des interfaces utilisateur plus élaborées.  Pour déplacer et suivre les contrôles et les fenêtres dans le contexte d'un groupe, vous intervenez sur leur ordre de plan.  L'*ordre de plan* détermine la superposition visuelle des contrôles d'un formulaire sur l'axe z \(profondeur\).  La fenêtre occupant le premier rang de l'ordre de plan se superpose à toutes les autres.  Inversement, toutes les fenêtres se superposent à celle qui occupe le dernier rang dans l'ordre de plan.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour superposer des contrôles au moment du design  
  
1.  Sélectionnez le contrôle à superposer.  
  
2.  Dans le menu **Format**, pointez sur **Ordre**, puis cliquez sur **Mettre au premier plan** ou **Mettre en arrière\-plan**.  
  
### Pour superposer les contrôles par programme  
  
-   Utilisez les méthodes <xref:System.Windows.Forms.Control.BringToFront%2A> et <xref:System.Windows.Forms.Control.SendToBack%2A> pour manipuler l'ordre de plan des contrôles.  
  
     Par exemple, si un contrôle <xref:System.Windows.Forms.TextBox>, `txtFirstName`, est placé sous un autre contrôle et que vous voulez qu'il se trouve au premier plan, utilisez le code suivant :  
  
    ```vb  
    txtFirstName.BringToFront()  
  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Forms prend en charge la *contenance de contrôles*.  Cette fonction consiste à placer un certain nombre de contrôles à l'intérieur d'un contrôle conteneur ; par exemple, des contrôles <xref:System.Windows.Forms.RadioButton> dans un contrôle <xref:System.Windows.Forms.GroupBox>.  Vous pouvez ensuite superposer les contrôles à l'intérieur de leur conteneur.  Le fait de déplacer la zone de groupe a pour conséquence de déplacer également les contrôles qu'elle contient.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)