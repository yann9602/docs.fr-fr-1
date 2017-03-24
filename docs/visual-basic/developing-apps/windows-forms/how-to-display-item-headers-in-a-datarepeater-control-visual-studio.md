---
title: "How to: Display Item Headers in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, item headers"
  - "DataRepeater, selection indicators"
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Display Item Headers in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'en\-tête d'élément d'un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> fournit un indicateur visuel lorsqu'un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> est sélectionné.  Lorsque la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> \(valeur par défaut\), l'en\-tête d'élément apparaît à gauche de chaque élément.  Lorsque la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, l'en\-tête d'élément apparaît en haut de chaque élément.  
  
 Lorsqu'il est sélectionné en premier, l'en\-tête d'élément apparaît dans la couleur spécifiée par la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> et une icône représentant une flèche blanche s'affiche.  
  
> [!NOTE]
>  Si vous affectez à <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> la valeur <xref:System.Drawing.Color.White%2A>, le symbole de sélection n'apparaît pas lorsque l'élément est sélectionné en premier.  
  
 Lorsqu'un champ de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> a le focus, la couleur de l'en\-tête d'élément devient celle de l'arrière\-plan <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> et l'icône de la flèche devient noire.  Si vous modifiez des données, un symbole de crayon apparaît dans l'en\-tête d'élément.  
  
 La largeur par défaut \(ou hauteur lorsque la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> a la valeur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>\) de l'en\-tête d'élément est de 15 pixels.  Vous pouvez changer la largeur en définissant la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>.  
  
> [!NOTE]
>  Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> a une valeur inférieure à 11, les symboles d'indicateur n'apparaissent pas dans l'en\-tête d'élément.  
  
 Vous pouvez masquer les en\-têtes d'élément en attribuant la valeur **False** au paramètre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>.  Lorsque <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> a la valeur **False**, la seule indication qu'un élément est sélectionné est un trait pointillé autour du périmètre du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
> [!NOTE]
>  Vous pouvez également fournir votre propre indicateur de sélection en surveillant la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> dans l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
### Pour modifier l'apparence des en\-têtes d'élément  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région inférieure du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Vous devez sélectionner la région inférieure du contrôle.  Si vous sélectionnez la section modèle d'élément, un jeu différent de propriétés apparaîtra dans la fenêtre Propriétés.  
  
2.  Dans la fenêtre Propriétés, vous pouvez utiliser la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> pour changer la couleur des en\-têtes d'élément.  
  
    > [!NOTE]
    >  Si vous affectez à <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> la valeur <xref:System.Drawing.Color.White%2A>, le symbole de sélection n'apparaît pas lorsque l'élément est sélectionné en premier.  
  
3.  Utilisez la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> pour modifier la largeur \(ou la hauteur\) des en\-têtes d'élément.  
  
    > [!NOTE]
    >  Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> a une valeur inférieure à 11, les symboles d'indicateur n'apparaissent pas dans l'en\-tête d'élément.  
  
### Pour masquer des en\-têtes d'élément  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région inférieure du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Vous devez sélectionner la région inférieure du contrôle.  Si vous sélectionnez la section modèle d'élément, un jeu différent de propriétés apparaîtra dans la fenêtre Propriétés.  
  
2.  Dans la fenêtre Propriétés, attribuez la valeur **False** à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>.  
  
     Lorsqu'un élément de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est sélectionné, la seule indication est un trait pointillé autour du périmètre du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)