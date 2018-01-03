---
title: "Comment : dessiner des lignes avec le contrôle LineShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Comment : dessiner des lignes avec le contrôle LineShape (Visual Studio)
Vous pouvez utiliser la <xref:Microsoft.VisualBasic.PowerPacks.LineShape> contrôle pour dessiner une ligne horizontale, verticale ou diagonale sur un formulaire ou un conteneur, à la fois au moment du design et au moment de l’exécution.  
  
 **Remarque** votre ordinateur peut afficher des noms différents ou des emplacements de l’utilisateur de Visual Studio pour les éléments d’interface dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Pour dessiner une ligne au moment du design  
  
1.  Faites glisser le <xref:Microsoft.VisualBasic.PowerPacks.LineShape> contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** faire glisser vers un formulaire ou un contrôle conteneur.  
  
2.  Faites glisser la poignée et déplacez les poignées pour redimensionner et positionner la ligne.  
  
     Vous pouvez également redimensionner et repositionner la ligne en modifiant le `X1`, `X2`, `Y1`, et `Y2` propriétés dans le **propriétés** fenêtre.  
  
3.  Dans le **propriétés** fenêtre, vous pouvez également définir des propriétés supplémentaires telles que `BorderStyle` ou `BorderColor` pour modifier l’apparence de la ligne.  
  
### <a name="to-draw-a-line-at-run-time"></a>Pour dessiner une ligne en cours d’exécution  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
2.  Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Microsoft.VisualBasic.PowerPacks.VS**, puis cliquez sur **OK**.  
  
3.  Dans le **éditeur de Code**, ajoutez une `Imports` ou `using` instruction en haut du module :  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Ajoutez le code suivant dans une procédure `Event` :  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Introduction aux contrôles Line et Shape](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Guide pratique : dessiner des formes avec les contrôles OvalShape et RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)
