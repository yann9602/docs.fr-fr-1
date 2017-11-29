---
title: "Comment : rechercher des données dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a>Comment : rechercher des données dans un contrôle DataRepeater (Visual Studio)
Lorsque vous utilisez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle qui contient plusieurs enregistrements, vous pouvez souhaiter permettre aux utilisateurs, recherchez un enregistrement spécifique. Au lieu de rechercher les données dans le contrôle lui-même, vous pouvez implémenter une recherche en interrogeant sous-jacent <xref:System.Windows.Forms.BindingSource>. Si l’élément est trouvé, vous pouvez ensuite utiliser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> propriété pour sélectionner l’élément et de faire défiler dans l’affichage.  
  
### <a name="to-implement-search"></a>Pour implémenter la recherche  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> .  
  
2.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchTextBox**.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> .  
  
4.  Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchButton**. Affectez à la propriété **Text** la valeur **Search**.  
  
5.  Double-cliquez sur le contrôle <xref:System.Windows.Forms.Button> pour ouvrir l’éditeur de code et ajoutez le code suivant au gestionnaire d’événements `SearchButton_Click` .  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     Remplacez *ProductsBindingSource* avec le nom de la <xref:System.Windows.Forms.BindingSource> pour votre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>et remplacez *ProductID* avec le nom du champ que vous souhaitez rechercher.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Guide pratique : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
