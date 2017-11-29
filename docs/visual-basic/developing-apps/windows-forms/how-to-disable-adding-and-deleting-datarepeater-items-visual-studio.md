---
title: "Comment : désactiver l'ajout et la suppression d'éléments dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b15fe6fb5190855126ffa60ac488aaa74ad9b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a>Comment : désactiver l'ajout et la suppression d'éléments dans un contrôle DataRepeater (Visual Studio)
Par défaut, les utilisateurs peuvent ajouter et supprimer des éléments dans un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle. Les utilisateurs peuvent ajouter un nouvel élément en appuyant sur CTRL + N lorsqu’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> a le focus ou en cliquant sur le **AddNewItem** bouton sur le <xref:System.Windows.Forms.BindingNavigator> contrôle. Les utilisateurs peuvent supprimer un élément en appuyant sur SUPPR lorsqu’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> a le focus ou en cliquant sur le **DeleteItem** bouton sur le <xref:System.Windows.Forms.BindingNavigator> contrôle.  
  
 Vous pouvez désactiver Ajout et/ou la suppression au moment du design ou au moment de l’exécution.  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a>Pour désactiver l’ajout et la suppression au moment du design  
  
1.  Dans le Concepteur Windows Forms, sélectionnez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.  
  
    > [!NOTE]
    >  Vous devez sélectionner la section inférieure du contrôle. Si vous sélectionnez la section de modèle d’élément, un ensemble différent de propriétés s’affichera.  
  
2.  Dans la fenêtre Propriétés, définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> propriété **False**.  
  
3.  Définir le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> propriété **False**.  
  
4.  Dans le Concepteur Windows Forms, sélectionnez le <xref:System.Windows.Forms.BindingNavigator> contrôler, puis cliquez sur le **AddNewItem** bouton (le bouton avec un signe plus).  
  
5.  Dans la fenêtre Propriétés, définissez la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété **False**.  
  
6.  Dans le Concepteur Windows Forms, sélectionnez le <xref:System.Windows.Forms.BindingNavigator> contrôler, puis cliquez sur le **DeleteItem** bouton (le bouton avec un X rouge).  
  
7.  Dans la fenêtre Propriétés, définissez la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété **False**.  
  
8.  Dans la barre d’état du composant, sélectionnez le <xref:System.Windows.Forms.BindingSource> auquel le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> est lié.  
  
9. Dans la fenêtre Propriétés, définissez la <xref:System.Windows.Forms.BindingSource.AllowNew%2A> propriété **False**.  
  
10. Dans le Concepteur Windows Forms, double-cliquez sur le **DeleteItem** bouton pour ouvrir l’éditeur de Code.  
  
11. Dans la liste déroulante d’événements, sélectionnez le `BindingNavigatorDeleteItem_EnabledChanged` événement.  
  
12. Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire car <xref:System.Windows.Forms.BindingSource> active le bouton **DeleteItem** chaque fois que l’enregistrement actif est modifié.  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a>Pour désactiver l’ajout et la suppression en cours d’exécution  
  
1.  Dans le Concepteur Windows Forms, double-cliquez sur le formulaire pour ouvrir l’éditeur de code.  
  
2.  Ajoutez le code suivant à l’événement `Form_Load` .  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  Ajoutez le code suivant au gestionnaire d'événements `BindingNavigatorDeleteItem_EnabledChanged` :  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  Cette étape est nécessaire car <xref:System.Windows.Forms.BindingSource> active le bouton **DeleteItem** chaque fois que l’enregistrement actif est modifié.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
