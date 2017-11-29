---
title: "Comment : modifier l'apparence d'un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>Comment : modifier l'apparence d'un contrôle DataRepeater (Visual Studio)
Vous pouvez modifier l’apparence d’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle au moment du design en définissant des propriétés ou en cours d’exécution en gérant la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> événement.  
  
 Les propriétés que vous définissez au moment du design lorsque la section de modèle d’élément du contrôle est sélectionnée sont répétées pour chaque <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> au moment de l’exécution. Relatives à l’apparence des propriétés de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle proprement dit est visible au moment de l’exécution uniquement si une partie du conteneur est laissée à découvert (par exemple, si la <xref:System.Windows.Forms.Control.Padding%2A> est définie sur une valeur élevée).  
  
 Au moment de l’exécution, relatives à l’apparence des propriétés peuvent être définies selon des conditions. Par exemple, dans une application de planification, vous pouvez modifier la couleur d’arrière-plan d’un élément pour avertir les utilisateurs lorsqu’un élément est en retard. Dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Gestionnaire d’événements, si vous définissez une propriété dans une instruction conditionnelle, telles que `If…Then`, vous devez également utiliser un `Else` clause pour spécifier l’apparence lorsque la condition n’est pas remplie.  
  
### <a name="to-change-the-appearance-at-design-time"></a>Pour modifier l’apparence au moment du design  
  
1.  Dans le Concepteur Windows Forms, sélectionnez la région de modèle (en haut) d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
2.  Dans la fenêtre Propriétés, sélectionnez une propriété et modifier la valeur. Les propriétés communes qui affectent l’apparence incluent <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, et <xref:System.Windows.Forms.Control.ForeColor%2A>.  
  
### <a name="to-change-the-appearance-at-run-time"></a>Pour modifier l’apparence au moment de l’exécution  
  
1.  Dans l’éditeur de code, dans la liste déroulante d’événements, cliquez sur **DrawItem**.  
  
2.  Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Gestionnaire d’événements, ajoutez le code pour définir les propriétés :  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>Exemple  
 Certaines personnalisations courantes pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle comprennent l’affichage des lignes dans différentes couleurs et la modification de la couleur d’un champ selon une condition. L’exemple suivant montre comment effectuer ces personnalisations. Cet exemple suppose que vous avez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle qui est lié à la table Products dans la base de données Northwind.  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 Notez que pour les deux de ces personnalisations, vous devez fournir le code pour définir les propriétés des deux côtés de la condition. Si vous ne spécifiez pas le `Else` condition, vous verrez des résultats inattendus au moment de l’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher des données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Guide pratique : afficher des en-têtes d’élément dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
