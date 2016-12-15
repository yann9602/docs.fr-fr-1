---
title: "Virtual Mode in the DataRepeater Control (Visual Studio) | Microsoft Docs"
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
  - "virtual data binding"
  - "DataRepeater"
  - "DataRepeater, virtual mode"
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Virtual Mode in the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque vous souhaitez afficher de très grandes quantités de données sous forme de tableau dans un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, vous pouvez améliorer les performances en donnant à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> la valeur `True` et en gérant explicitement l'interaction du contrôle avec sa source de données.  Le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> fournit plusieurs événements que vous pouvez gérer pour interagir avec votre source de données et afficher les données nécessaires au moment de l'exécution.  
  
## Fonctionnement du mode virtuel  
 Le scénario le plus courant pour le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> consiste à lier les contrôles enfants de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> à une source de données au moment du design et à permettre au <xref:System.Windows.Forms.BindingSource> de transférer des données selon les besoins.  Lorsque vous utilisez le mode virtuel, les contrôles ne sont pas liés à une source de données et les données sont transférées à la source de données sous\-jacente au moment de l'exécution.  
  
 Lorsque la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> a la valeur `True`, vous créez l'interface utilisateur en ajoutant des contrôles depuis la **Boîte à outils** au lieu d'ajouter des contrôles liés depuis la fenêtre **Sources de données**.  
  
 Les événements sont déclenchés contrôle par contrôle et vous devez ajouter du code pour gérer l'affichage des données.  Lorsqu'un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> fait l'objet d'un défilement dans l'affichage, l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> est déclenché une fois par contrôle et vous devez fournir les valeurs pour chaque contrôle dans le gestionnaire d'événements <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>.  
  
 Si l'utilisateur modifie les données d'un des contrôles, l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> est déclenché et vous devez valider les données et les enregistrer dans votre source de données.  
  
 Si l'utilisateur ajoute un nouvel élément, l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> est déclenché.  Utilisez le gestionnaire de cet événement pour créer un enregistrement dans votre source de données.  Pour empêcher toute modification involontaire, vous devez également surveiller l'événement <xref:System.Windows.Forms.Control.KeyDown> pour chaque contrôle et appeler <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> si l'utilisateur appuie sur la touche Échap.  
  
 Si votre source de données change, vous pouvez actualiser le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> en appelant les méthodes <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetTemplateItem%2A> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetTemplateItem%2A>.  Ces deux méthodes doivent être appelées dans l'ordre.  
  
 Enfin, vous devez implémenter des gestionnaires d'événements pour l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>, qui se produit lorsqu'un élément est supprimé, et, facultativement, pour les événements <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>, qui sont déclenchés chaque fois qu'un utilisateur supprime un élément en appuyant sur la touche SUPPR.  
  
## Implémentation du mode virtuel  
 Les étapes suivantes sont requises pour implémenter le mode virtuel.  
  
#### Pour implémenter le mode virtuel  
  
1.  Faites glisser un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> depuis l'onglet **Visual Basic PowerPacks** de la **Boîte à outils** vers un formulaire ou un contrôle conteneur.  Affectez à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> la valeur `True`.  
  
2.  Faites glisser des contrôles depuis la **Boîte à outils** sur la région de modèle d'élément \(région supérieure\) du contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Vous avez besoin d'un contrôle pour chacun des champs de la source de données que vous souhaitez afficher.  
  
3.  Implémentez un gestionnaire pour l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> afin de fournir des valeurs à chaque contrôle.  Cet événement est déclenché lorsqu'un nouveau <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> fait l'objet d'un défilement dans l'affichage.  Le code se présentera comme dans l'exemple suivant, lequel concerne une source de données appelée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  Implémentez un gestionnaire pour l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> afin de stocker les données.  Cet événement est déclenché lorsqu'un utilisateur valide des modifications apportées à un contrôle enfant de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.  Le code se présentera comme dans l'exemple suivant, lequel concerne une source de données appelée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  Implémentez un gestionnaire pour l'événement <xref:System.Windows.Forms.Control.KeyDown> de chaque contrôle enfant et surveillez la touche Échap.  Appelez la méthode <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> pour empêcher le déclenchement de l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>.  Le code ressemblera à l'exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  Implémentez un gestionnaire pour l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>.  Cet événement est déclenché lorsque l'utilisateur ajoute un nouvel élément au contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Le code se présentera comme dans l'exemple suivant, lequel concerne une source de données appelée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  Implémentez un gestionnaire pour l'événement <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>.  Cet événement se produit lorsqu'un utilisateur supprime un élément existant.  Le code se présentera comme dans l'exemple suivant, lequel concerne une source de données appelée `Employees`.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  Pour la validation au niveau du contrôle, vous pouvez implémenter des gestionnaires pour les événements <xref:System.Windows.Forms.Control.Validating> des contrôles enfants.  Le code ressemblera à l'exemple suivant.  
  
     [!code-vb[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb)]
     [!code-cs[VbPowerPacksDataRepeaterVirtualMode#6](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)