---
title: "How to: Search Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, implementing search"
  - "DataRepeater, searching data"
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Search Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Lorsque vous utilisez un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> qui contient de nombreux enregistrements, vous souhaiterez peut\-être permettre aux utilisateurs de rechercher un enregistrement spécifique.  Au lieu de rechercher les données dans le contrôle lui\-même, vous pouvez implémenter une recherche en interrogeant la <xref:System.Windows.Forms.BindingSource> sous\-jacente.  Si l'élément est trouvé, vous pouvez ensuite utiliser la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> pour le sélectionner et le faire défiler dans l'affichage.  
  
### Pour implémenter la recherche  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> depuis la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
2.  Dans la fenêtre Propriétés, remplacez la valeur de la propriété **Name** par SearchTextBox.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> depuis la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
4.  Dans la fenêtre Propriétés, remplacez la valeur de la propriété **Name** par SearchButton.  Affectez la valeur Search à la propriété **Text**.  
  
5.  Double\-cliquez sur le contrôle <xref:System.Windows.Forms.Button> pour ouvrir l'Éditeur de code et ajoutez le code suivant au gestionnaire d'événements `SearchButton_Click`.  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Remplacez *ProductsBindingSource* par le nom de la <xref:System.Windows.Forms.BindingSource> de votre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> et remplacez *IDProduit* par le nom du champ que vous souhaitez rechercher.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)