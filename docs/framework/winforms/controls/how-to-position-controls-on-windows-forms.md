---
title: "Comment&#160;: positionner des contr&#244;les dans des Windows Forms | Microsoft Docs"
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
  - "Location"
  - "Location.Y"
  - "Location.X"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms)"
  - "contrôles (Windows Forms), déplacer"
  - "contrôles (Windows Forms), positionner"
  - "lignes d'alignement"
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: positionner des contr&#244;les dans des Windows Forms
Pour positionner les contrôles, utilisez le Concepteur Windows Forms, ou spécifiez la propriété <xref:System.Windows.Forms.Control.Location%2A>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour positionner un contrôle dans l'aire de conception du Concepteur Windows Forms  
  
-   En vous servant de la souris, faites glisser le contrôle jusqu'à l'emplacement souhaité.  
  
    > [!NOTE]
    >  Sélectionnez le contrôle et déplacez\-le à l'aide des touches de direction pour le positionner plus précisément.  Également, les *lignes d'alignement \(SnapLines\)* vous aident à placer les contrôles avec précision sur votre formulaire.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### Pour positionner un contrôle à l'aide de la fenêtre Propriétés  
  
1.  Cliquez sur le contrôle que vous souhaitez positionner.  
  
2.  Dans la fenêtre **Propriétés**, tapez des valeurs pour la propriété <xref:System.Windows.Forms.Control.Location%2A> en les séparant d'une virgule afin de positionner le contrôle dans son conteneur.  
  
     Le premier nombre \(X\) correspond à sa distance par rapport au bord gauche du conteneur et le deuxième nombre \(Y\) à sa distance, en pixels, par rapport au bord supérieur de la zone du conteneur.  
  
    > [!NOTE]
    >  Vous pouvez développer la propriété <xref:System.Windows.Forms.Control.Location%2A> pour taper individuellement les valeurs **X** et **Y**.  
  
### Pour positionner un contrôle par programmation  
  
1.  Affectez un <xref:System.Drawing.Point> à la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Modifiez la coordonnée X du contrôle en utilisant la sous\-propriété <xref:System.Windows.Forms.Control.Left%2A>.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### Pour incrémenter par programmation la position d'un contrôle  
  
1.  Définissez la sous\-propriété <xref:System.Windows.Forms.Control.Left%2A> pour incrémenter la coordonnée X du contrôle.  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  Utilisez la propriété <xref:System.Windows.Forms.Control.Location%2A> pour définir simultanément les coordonnées X et Y d'un contrôle.  Pour définir les coordonnées séparément, utilisez les sous\-propriétés <xref:System.Windows.Forms.Control.Left%2A> \(**X**\) ou <xref:System.Windows.Forms.Control.Top%2A> \(**Y**\) du contrôle.  N'essayez pas de définir implicitement les coordonnées X et Y de la structure <xref:System.Drawing.Point> qui représente la position du bouton, car cette structure contient une copie des coordonnées du bouton.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [How to: Set the Screen Location of Windows Forms](http://msdn.microsoft.com/fr-fr/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)