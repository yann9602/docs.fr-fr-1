---
title: "Comment : activer la tabulation entre les formes (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a39957ffaa67d6abeb6d394ae9826d42ad2230de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="53a8c-102">Comment : activer la tabulation entre les formes (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="53a8c-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="53a8c-103">Les contrôles Line et shape n’ont pas `TabStop` ou `TabIndex` , mais vous pouvez quand même activer la tabulation entre eux.</span><span class="sxs-lookup"><span data-stu-id="53a8c-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="53a8c-104">Dans l’exemple suivant, en appuyant sur la touche CTRL et les touches de tabulation sera onglet entre les formes. uniquement la touche TAB sera onglet entre les boutons.</span><span class="sxs-lookup"><span data-stu-id="53a8c-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53a8c-105">Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="53a8c-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="53a8c-106">L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments.</span><span class="sxs-lookup"><span data-stu-id="53a8c-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="53a8c-107">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="53a8c-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="53a8c-108">Pour activer la tabulation entre les formes</span><span class="sxs-lookup"><span data-stu-id="53a8c-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="53a8c-109">Faites glisser trois <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> contrôles et deux <xref:System.Windows.Forms.Button> des contrôles de la **boîte à outils** à un formulaire.</span><span class="sxs-lookup"><span data-stu-id="53a8c-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="53a8c-110">Dans le **éditeur de Code**, ajoutez une `Imports` ou `using` instruction en haut du module :</span><span class="sxs-lookup"><span data-stu-id="53a8c-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="53a8c-111">Dans une procédure événementielle, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="53a8c-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="53a8c-112">Ajoutez le code suivant dans le `Button1_PreviewKeyDown` procédure événementielle :</span><span class="sxs-lookup"><span data-stu-id="53a8c-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="53a8c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53a8c-113">See Also</span></span>  
 [<span data-ttu-id="53a8c-114">Guide pratique : dessiner des formes avec les contrôles OvalShape et RectangleShape</span><span class="sxs-lookup"><span data-stu-id="53a8c-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="53a8c-115">Guide pratique : dessiner des lignes avec le contrôle LineShape</span><span class="sxs-lookup"><span data-stu-id="53a8c-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="53a8c-116">Introduction aux contrôles Line et Shape</span><span class="sxs-lookup"><span data-stu-id="53a8c-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
