---
title: "Mode virtuel dans le contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 85f7e250c57a507e891eb30756c0550098cce9e0
ms.lasthandoff: 03/13/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>Mode virtuel dans le contrôle DataRepeater (Visual Studio)
Lorsque vous souhaitez afficher de grandes quantités de données tabulaires dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>(contrôle), vous pouvez améliorer les performances en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriété `True` et en gérant explicitement l’interaction du contrôle avec sa source de données.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle fournit plusieurs événements que vous pouvez gérer pour interagir avec votre source de données et afficher les données nécessaires au moment de l’exécution.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="how-virtual-mode-works"></a>Fonctionnement du Mode virtuel  
 Le scénario le plus courant pour les <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle consiste à lier les contrôles enfants du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>à des données source au moment du design et autoriser la <xref:System.Windows.Forms.BindingSource>pour passer des données selon les besoins.</xref:System.Windows.Forms.BindingSource> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Lorsque vous utilisez le mode virtuel, les contrôles ne sont pas liés à une source de données et les données sont transmises dans les deux sens à la source de données sous-jacente au moment de l’exécution.  
  
 Lorsque la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>est définie sur `True`, vous créez l’interface utilisateur en ajoutant des contrôles à partir de la **boîte à outils** au lieu d’ajouter des contrôles liés à partir de la **des Sources de données** fenêtre.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
 Événements sont déclenchés sur une base de contrôle en contrôle, et vous devez ajouter du code pour gérer l’affichage des données. Lorsqu’un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>est affiché le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>événement est déclenché une fois pour chaque contrôle et vous devez fournir les valeurs pour chaque contrôle dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>Gestionnaire d’événements.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>  
  
 Si les données dans un des contrôles sont modifiées par l’utilisateur, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>événement est déclenché et vous devez valider les données et les enregistrer dans votre source de données.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
  
 Si l’utilisateur ajoute un nouvel élément, le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>événement est déclenché.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> Utilisez le Gestionnaire de cet événement pour créer un nouvel enregistrement dans la source de données. Pour empêcher toute modification involontaire, vous devez également surveiller la <xref:System.Windows.Forms.Control.KeyDown>événement pour chaque contrôle et appeler <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>Si l’utilisateur appuie sur la touche ÉCHAP.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> </xref:System.Windows.Forms.Control.KeyDown>  
  
 Si vos données source change, vous pouvez actualiser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle en appelant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>méthodes.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Les deux méthodes doivent être appelées dans l’ordre.  
  
 Enfin, vous devez implémenter des gestionnaires d’événements pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>événement qui se produit lorsqu’un élément est supprimé et éventuellement pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>les événements qui se produisent chaque fois qu’un utilisateur supprime un élément en appuyant sur la touche SUPPR.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>  
  
## <a name="implementing-virtual-mode"></a>Implémentation du Mode virtuel  
 Voici les étapes requises pour implémenter le mode virtuel.  
  
#### <a name="to-implement-virtual-mode"></a>Pour implémenter le mode virtuel  
  
1.  Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler à partir de la **Visual Basic PowerPacks** onglet le **boîte à outils** à un formulaire ou un contrôle conteneur.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Définir le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriété `True`.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
2.  Faire glisser des contrôles à partir de la **boîte à outils** sur la région de modèle d’élément (région supérieure) de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Effectuez un contrôle pour chaque champ dans votre source de données que vous souhaitez afficher.  
  
3.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>événement afin de fournir des valeurs pour chaque contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> Cet événement est déclenché lorsqu’un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>est affiché.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Le code ressemblera à l’exemple suivant, qui est d’une source de données nommée `Employees`.  
  
     [!code-vb[N °&1; de VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n °&1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>pour stocker les données d’événement.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> Cet événement est déclenché lorsque l’utilisateur valide les modifications apportées à un contrôle enfant du <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Le code ressemblera à l’exemple suivant, qui est d’une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n °&2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implémentez un gestionnaire pour de chaque contrôle enfant <xref:System.Windows.Forms.Control.KeyDown>événements et surveillez la touche ÉCHAP.</xref:System.Windows.Forms.Control.KeyDown> Appelez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>pour empêcher le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>événement d’être déclenchés.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> Le code ressemblera à l’exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode n °&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n°&3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>événements.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> Cet événement est déclenché lorsque l’utilisateur ajoute un nouvel élément à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Le code ressemblera à l’exemple suivant, qui est d’une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n °&4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implémentez un gestionnaire pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>événements.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> Cet événement se produit lorsqu’un utilisateur supprime un élément existant. Le code ressemblera à l’exemple suivant, qui est d’une source de données nommée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n °&5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Pour la validation au niveau du contrôle, vous pouvez également implémenter des gestionnaires pour les <xref:System.Windows.Forms.Control.Validating>événements des contrôles enfants.</xref:System.Windows.Forms.Control.Validating> Le code ressemblera à l’exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode n °&6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode n °&6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
