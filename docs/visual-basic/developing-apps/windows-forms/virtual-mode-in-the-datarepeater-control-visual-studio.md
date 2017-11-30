---
title: "Mode virtuel dans le contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- virtual data binding [Visual Basic]
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c85ce4541e32991bfa09b1436385281d27ad355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Mode virtuel dans le contrôle DataRepeater (Visual Studio)
Lorsque vous souhaitez afficher de grandes quantités de données tabulaires dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> (contrôle), vous pouvez améliorer les performances en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> propriété `True` et en gérant explicitement l’interaction du contrôle avec sa source de données. Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle fournit plusieurs événements que vous pouvez gérer pour interagir avec votre source de données et afficher les données nécessaires au moment de l’exécution.  
  
## <a name="how-virtual-mode-works"></a>Fonctionnement du Mode virtuel  
 Le scénario le plus courant pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle consiste à lier les contrôles enfants de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> à des données source au moment du design et autoriser la <xref:System.Windows.Forms.BindingSource> pour passer des données dans les deux sens en fonction des besoins. Lorsque vous utilisez le mode virtuel, les contrôles ne sont pas liés à une source de données et les données sont transmises dans les deux sens à la source de données sous-jacente au moment de l’exécution.  
  
 Lorsque le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> est définie sur `True`, vous créez l’interface utilisateur en ajoutant des contrôles à partir de la **boîte à outils** au lieu d’ajouter des contrôles liés à partir de la **des Sources de données** fenêtre.  
  
 Les événements sont déclenchés sur une base de contrôle en contrôle, et vous devez ajouter du code pour gérer l’affichage de données. Lorsqu’un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> devient visible, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> événement est déclenché une fois pour chaque contrôle, et vous devez fournir les valeurs pour chaque contrôle dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> Gestionnaire d’événements.  
  
 Si les données dans un des contrôles sont modifiées par l’utilisateur, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> événement est déclenché et vous devez valider les données et les enregistrer dans votre source de données.  
  
 Si l’utilisateur ajoute un nouvel élément, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> événement est déclenché. Utilisez le Gestionnaire de cet événement pour créer un nouvel enregistrement dans votre source de données. Pour empêcher des modifications non souhaitées, vous devez également surveiller la <xref:System.Windows.Forms.Control.KeyDown> événement pour chaque contrôle et l’appeler <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> si l’utilisateur appuie sur la touche ÉCHAP.  
  
 Si les modifications de source de données, vous pouvez actualiser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle en appelant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> méthodes. Les deux méthodes doivent être appelées dans l’ordre.  
  
 Enfin, vous devez implémenter des gestionnaires d’événements pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> événement qui se produit lorsqu’un élément est supprimé et éventuellement pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> les événements qui se produisent chaque fois qu’un utilisateur supprime un élément en appuyant sur la touche SUPPR.  
  
## <a name="implementing-virtual-mode"></a>Implémentation du Mode virtuel  
 Voici les étapes requises pour implémenter le mode virtuel.  
  
#### <a name="to-implement-virtual-mode"></a>Pour implémenter le mode virtuel  
  
1.  Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur. Affectez à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> la valeur `True`.  
  
2.  Faites glisser les contrôles à partir de la **boîte à outils** sur la région de modèle d’élément (région supérieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Vous devez un contrôle pour chaque champ dans votre source de données que vous souhaitez afficher.  
  
3.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> événement afin de fournir des valeurs pour chaque contrôle. Cet événement est déclenché lorsqu’un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> devient visible. Le code ressemblera à l’exemple suivant, qui est pour une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> pour stocker les données d’événement. Cet événement est déclenché lorsque l’utilisateur valide les modifications apportées à un contrôle enfant de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>. Le code ressemblera à l’exemple suivant, qui est pour une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implémentez un gestionnaire pour de chaque contrôle enfant <xref:System.Windows.Forms.Control.KeyDown> événement et surveillez la touche ÉCHAP. Appelez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> pour empêcher le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> événement déclenché. Le code ressemblera à l’exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> événement. Cet événement est déclenché lorsque l’utilisateur ajoute un nouvel élément à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Le code ressemblera à l’exemple suivant, qui est pour une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> événement. Cet événement se produit lorsqu’un utilisateur supprime un élément existant. Le code ressemblera à l’exemple suivant, qui est pour une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Pour la validation au niveau du contrôle, vous pouvez également implémenter des gestionnaires pour les <xref:System.Windows.Forms.Control.Validating> événements des contrôles enfants. Le code ressemblera à l’exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
