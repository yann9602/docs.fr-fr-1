---
title: "Comment : afficher des en-têtes d'élément dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da02f9374471a581a58131e26d618f91d7cbb7af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>Comment : afficher des en-têtes d'élément dans un contrôle DataRepeater (Visual Studio)
L’en-tête de l’élément dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle fournit un indicateur visuel lorsqu’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> est sélectionnée. Lorsque le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> est définie sur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> (la valeur par défaut), l’en-tête de l’élément est affiché à gauche de chaque élément. Lorsque le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> est définie sur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>, l’en-tête de l’élément est affiché en haut de chaque élément.  
  
 Lorsqu’il est sélectionné en premier, l’en-tête de l’élément est affiché dans la couleur qui est spécifiée par le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriété et une icône de flèche blanche s’affiche.  
  
> [!NOTE]
>  Si vous définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> à <xref:System.Drawing.Color.White%2A>, le symbole de sélection ne sera pas visible lorsque l’élément est sélectionné en premier.  
  
 Lorsqu’un champ dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> a le focus, la couleur de l’élément d’en-tête devient à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> couleur d’arrière-plan et les modifications d’icône flèche noire. Si les données sont modifiées, un symbole de crayon est affiché dans l’en-tête de l’élément.  
  
 La largeur par défaut (ou de la hauteur lors de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> est définie sur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) de l’élément en-tête est de 15 pixels. Vous pouvez modifier la largeur en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriété.  
  
> [!NOTE]
>  Si la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> est définie sur une valeur inférieure à 11, les symboles d’indicateur dans l’en-tête de l’élément ne s’affichera pas.  
  
 Vous pouvez masquer les en-têtes d’élément en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriété **False**. Lorsque <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> a la valeur **False**, la seule indication qu’un élément est sélectionné est une ligne en pointillés autour du périmètre de le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Vous pouvez également fournir votre propre indicateur de sélection en surveillant la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> propriété de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> dans les <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> l’événement de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### <a name="to-change-the-appearance-of-item-headers"></a>Pour modifier l’apparence des en-têtes d’élément  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région inférieure de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
    > [!NOTE]
    >  Vous devez sélectionner la région inférieure du contrôle. Si vous sélectionnez la section de modèle d’élément, un ensemble différent de propriétés s’affiche dans la fenêtre Propriétés.  
  
2.  Dans la fenêtre Propriétés, utilisez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> propriété à modifier la couleur des en-têtes d’élément.  
  
    > [!NOTE]
    >  Si vous définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> à <xref:System.Drawing.Color.White%2A>, le symbole de sélection ne sera pas visible lorsque l’élément est sélectionné en premier.  
  
3.  Utilisez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> propriété à modifier la largeur (ou la hauteur) des en-têtes d’élément.  
  
    > [!NOTE]
    >  Si la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> est définie sur une valeur inférieure à 11, les symboles d’indicateur dans l’en-tête de l’élément ne s’affichera pas.  
  
### <a name="to-hide-item-headers"></a>Pour masquer les en-têtes d’élément  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région inférieure de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
    > [!NOTE]
    >  Vous devez sélectionner la région inférieure du contrôle. Si vous sélectionnez la section de modèle d’élément, un ensemble différent de propriétés s’affiche dans la fenêtre Propriétés.  
  
2.  Dans la fenêtre Propriétés, définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> propriété **False**.  
  
     Lorsqu’un élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est sélectionné, la seule indication est une ligne en pointillés autour du périmètre de le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Guide pratique : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : modifier la disposition d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
