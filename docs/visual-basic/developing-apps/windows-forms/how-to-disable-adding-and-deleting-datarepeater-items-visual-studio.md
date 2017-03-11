---
title: "How to: Disable Adding and Deleting DataRepeater Items (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, disabling delete"
  - "DataRepeater, disabling add"
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Par défaut, les utilisateurs peuvent ajouter et supprimer des éléments dans un contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  Les utilisateurs peuvent ajouter un élément en appuyant sur CTRL\+N lorsqu'un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> a le focus ou en cliquant sur le bouton **AddNewItem** sur le contrôle <xref:System.Windows.Forms.BindingNavigator>.  Les utilisateurs peuvent supprimer un élément en appuyant sur Suppr lorsqu'un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> a le focus ou en cliquant sur le bouton **DeleteItem** sur le contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
 Vous pouvez désactiver l'ajout et\/ou la suppression au moment du design ou de l'exécution.  
  
### Pour désactiver l'ajout et la suppression au moment du design  
  
1.  Dans le Concepteur Windows Forms, sélectionnez le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
    > [!NOTE]
    >  Vous devez sélectionner la section inférieure du contrôle.  Si vous sélectionnez la section modèle d'élément, un jeu différent de propriétés sera affiché.  
  
2.  Dans la fenêtre Propriétés, attribuez la valeur **False** à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>.  
  
3.  Attribuez la valeur **False** à la propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>.  
  
4.  Dans le Concepteur Windows Forms, sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>, puis cliquez sur le bouton **AddNewItem** \(bouton avec un signe plus\).  
  
5.  Dans la fenêtre Propriétés, attribuez la valeur **False** à la propriété <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>.  
  
6.  Dans le Concepteur Windows Forms, sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>, puis cliquez sur le bouton **DeleteItem** \(bouton avec un X rouge\).  
  
7.  Dans la fenêtre Propriétés, attribuez la valeur **False** à la propriété <xref:System.Windows.Forms.ToolBarButton.Enabled%2A>.  
  
8.  Dans la barre d'état des composants, sélectionnez la <xref:System.Windows.Forms.BindingSource> à laquelle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est lié.  
  
9. Dans la fenêtre Propriétés, attribuez la valeur **False** à la propriété <xref:System.Windows.Forms.BindingSource.AllowNew%2A>.  
  
10. Dans le Concepteur Windows Forms, double\-cliquez sur le bouton **DeleteItem** pour ouvrir l'Éditeur de code.  
  
11. Sélectionnez l'événement `BindingNavigatorDeleteItem_EnabledChanged` dans la liste déroulante Événements.  
  
12. Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DisableAddDeleteCS/DisableAddDelete.cs#1)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/vbpowerpacksdatarepeaterdisableadddelete/form1.vb#1)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire dans la mesure où <xref:System.Windows.Forms.BindingSource> active le bouton **DeleteItem** chaque fois que l'enregistrement actuel est modifié.  
  
### Pour désactiver l'ajout et la suppression au moment de l'exécution  
  
1.  Dans le Concepteur Windows Forms, double\-cliquez sur le formulaire pour ouvrir l'Éditeur de code.  
  
2.  Ajoutez le code suivant à l'événement `Form_Load` :  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DisableAddDeleteCS/DisableAddDelete.cs#2)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/vbpowerpacksdatarepeaterdisableadddelete/form1.vb#2)]  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/DisableAddDeleteCS/DisableAddDelete.cs#1)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/vbpowerpacksdatarepeaterdisableadddelete/form1.vb#1)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire dans la mesure où <xref:System.Windows.Forms.BindingSource> active le bouton **DeleteItem** chaque fois que l'enregistrement actuel est modifié.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)