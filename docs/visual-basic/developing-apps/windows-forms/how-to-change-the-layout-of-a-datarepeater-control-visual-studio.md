---
title: "How to: Change the Layout of a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, changing layout style"
  - "DataRepeater, changing orientation"
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Change the Layout of a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> peut être affiché selon une orientation verticale \(défilement vertical des éléments\) ou horizontale \(défilement horizontal des éléments\).  Vous pouvez modifier l'orientation au moment du design ou de l'exécution en modifiant la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>.  Si vous modifiez la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> au moment de l'exécution, peut\-être souhaiterez\-vous également redimensionner <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> et repositionner les contrôles enfants.  
  
> [!NOTE]
>  Si vous repositionnez des contrôles sur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> au moment de l'exécution, vous devrez appeler les méthodes <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> au début et à la fin du bloc de code chargé de repositionner les contrôles.  
  
### Pour modifier la disposition au moment du design  
  
1.  Dans le Concepteur Windows Forms, sélectionnez le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Vous devez sélectionner la bordure externe du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> en cliquant dans la région inférieure du contrôle, et pas dans la région <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> supérieure.  
  
2.  Dans la fenêtre Propriétés, affectez à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> soit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>, soit <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles>.  
  
### Pour modifier la disposition au moment de l'exécution  
  
1.  Ajoutez le code suivant à un gestionnaire d'événements `Click` de bouton ou de menu :  
  
     [!code-cs[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  Dans la plupart des cas, vous souhaiterez ajouter des lignes de code semblables à celles indiquées dans la section Exemple pour redimensionner <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> et réorganiser les contrôles en vue de les adapter à la nouvelle orientation.  
  
## Exemple  
 L'exemple suivant montre comment répondre à l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> dans un gestionnaire d'événements.  Cet exemple nécessite la présence d'un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nommé `DataRepeater1` sur le formulaire et que ses <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contiennent deux contrôles <xref:System.Windows.Forms.TextBox> nommés `TextBox1` et `TextBox2`.  
  
 [!code-cs[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)