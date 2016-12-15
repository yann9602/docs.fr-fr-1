---
title: "Troubleshooting the DataRepeater Control (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, troubleshooting"
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette rubrique répertorie les problèmes courants susceptibles de se produire lorsque vous utilisez le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
## Les événements de clavier et de souris DataRepeater ne sont pas déclenchés  
 Certains événements de contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, tels que événements de clavier et de souris, ne sont pas déclenchés.  Ce problème est dû au design.  Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est un conteneur pour des objets <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> et est inaccessible au moment de l'exécution.  Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> n'expose d'événements au moment du design.  Par conséquent, le fait de cliquer sur un élément ou d'appuyer sur une touche lorsque l'élément a le focus ne déclenche pas d'événement.  
  
 Il y a toutefois une exception à cette règle, à savoir lorsque la valeur affectée à la propriété <xref:System.Windows.Forms.Control.Padding%2A> est suffisamment grande pour exposer les bords du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Dans ce cas, des événements de souris sont déclenchés lorsque vous cliquez dans la marge exposée.  
  
 Pour résoudre ce problème, ajoutez un contrôle <xref:System.Windows.Forms.Panel> à la section <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, puis ajoutez le reste des contrôles au <xref:System.Windows.Forms.Panel>.  Vous pouvez ensuite ajouter le code aux gestionnaires d'événements du contrôle <xref:System.Windows.Forms.Panel> pour les événements de clavier et de souris.  
  
## Le DataRepeater est partiellement masqué derrière le navigateur de liaisons  
 Lorsque vous ajoutez pour la première fois un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> à un formulaire, puis ajoutez des contrôles liés aux données depuis la fenêtre **Sources de données**, le contrôle <xref:System.Windows.Forms.BindingNavigator> peut apparaître au\-dessus du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Il s'agit d'une limitation connue de la fenêtre **Sources de données**, qui est cohérente avec le comportement d'autres contrôles, tels que <xref:System.Windows.Forms.DataGridView>.  
  
 Vous pouvez déplacer le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> en dessous du contrôle <xref:System.Windows.Forms.BindingNavigator> au moment du design ou ajouter du code semblable à celui présenté ci\-après dans le gestionnaire d'événements `Load`.  
  
```vb#  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```c#  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## Les contrôles ne s'affichent pas correctement au moment de l'exécution  
 Certains contrôles d'un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> peuvent ne pas s'afficher comme prévu au moment de l'exécution.  Le processus utilisé pour cloner des contrôles depuis le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> vers le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ne parvient pas toujours à déterminer toutes les propriétés de tous les contrôles.  Par exemple, si vous ajoutez un contrôle <xref:System.Windows.Forms.ListBox> indépendant à un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> au moment du design et remplissez sa collection <xref:System.Windows.Forms.ListBox.Items%2A> avec une liste de chaînes, le <xref:System.Windows.Forms.ListBox> sera vide au moment de l'exécution.  Cela s'explique par le fait que le processus de clonage n'est pas en mesure de prendre en compte la propriété <xref:System.Windows.Forms.ListBox.Items%2A>.  
  
 Vous pouvez résoudre les problèmes de ce type en restaurant les propriétés manquantes dans l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>, qui se produit après que le clonage par défaut a été effectué.  L'exemple suivant montre comment réparer la collection <xref:System.Windows.Forms.ListBox.Items%2A> d'un contrôle <xref:System.Windows.Forms.ListBox> dans le gestionnaire d'événements <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>.  
  
 [!code-cs[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## Le symbole de sélection n'apparaît pas sur l'en\-tête d'élément  
 Lorsque vous modifiez la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> de l'en\-tête d'élément dans un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, certains choix de couleurs peuvent provoquer la disparition du symbole de sélection.  La modification de la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> peut également entraîner la disparition de ce symbole.  
  
 La couleur et taille du symbole de sélection ne peuvent pas être modifiées.  
  
-   Si vous affectez à <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> la valeur <xref:System.Drawing.Color.White%2A>, le symbole de sélection n'apparaît pas lorsqu'un élément est sélectionné pour la première fois.  
  
-   Si vous affectez au <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> la valeur <xref:System.Drawing.Color.Black%2A>, le symbole de sélection n'apparaît pas lorsqu'un contrôle est sélectionné. Par ailleurs, le symbole de crayon n'est pas visible lorsqu'un contrôle est en mode édition.  
  
-   Si la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> a une valeur inférieure à 11, les symboles d'indicateur n'apparaissent pas dans l'en\-tête d'élément.  
  
 Vous pouvez fournir votre propre en\-tête d'élément et symbole de sélection en utilisant un contrôle <xref:System.Windows.Forms.PictureBox> et en surveillant la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> dans l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>.  
  
## Voir aussi  
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)