---
title: "How to: Draw Lines with the LineShape Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LineShape control"
  - "lines, drawing"
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Draw Lines with the LineShape Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez utiliser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.LineShape> pour dessiner des lignes horizontales, verticales ou diagonales sur un formulaire ou un conteneur, que ce soit au moment du design ou de l'exécution.  
  
 **Remarque** Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les intructions suivantes.  Ces éléments dépendent de l'édition de Visual Studio dont vous disposez et des paramètres que vous utilisez.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour dessiner une ligne au moment du design  
  
1.  Faites glisser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.LineShape> depuis l'onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser les poignées de dimensionnement et de déplacement pour changer la taille et la position de la ligne.  
  
     Vous pouvez également redimensionner et repositionner la ligne en modifiant les propriétés `X1`, `X2`, `Y1` et `Y2` dans la fenêtre **Propriétés**.  
  
3.  Dans la fenêtre **Propriétés**, définissez facultativement des propriétés supplémentaires telles que `BorderStyle` ou `BorderColor` pour modifier l'apparence de la ligne.  
  
### Pour dessiner une ligne au moment de l'exécution  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, sélectionnez **Microsoft.VisualBasic.PowerPacks.VS**, puis cliquez sur **OK**.  
  
3.  Dans l'**Éditeur de code**, ajoutez une instruction `Imports` ou `using` en haut du module :  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  Ajoutez le code suivant à une procédure `Event` :  
  
     [!code-cs[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)