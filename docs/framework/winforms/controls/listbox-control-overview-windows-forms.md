---
title: "Vue d'ensemble du contrôle ListBox (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ListBox
helpviewer_keywords:
- list boxes [Windows Forms], about list boxes
- ListBox control [Windows Forms], about ListBox control
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6e73d76a2d9b31a87bf5a693b5ffa387d7ab5cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ListBox (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ListBox> contrôle affiche une liste à partir de laquelle l’utilisateur peut sélectionner un ou plusieurs éléments. Si le nombre total d’éléments dépasse le nombre qui peut être affiché, une barre de défilement est automatiquement ajoutée à la <xref:System.Windows.Forms.ListBox> contrôle. Lorsque le <xref:System.Windows.Forms.ListBox.MultiColumn%2A> est définie sur `true`, la zone de liste affiche des éléments dans plusieurs colonnes et une barre de défilement horizontale s’affiche. Lorsque le <xref:System.Windows.Forms.ListBox.MultiColumn%2A> est définie sur `false`, la zone de liste affiche les éléments dans une seule colonne et une barre de défilement verticale apparaît. Lorsque <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> a la valeur `true`, la barre de défilement s’affiche quel que soit le nombre d’éléments. Le <xref:System.Windows.Forms.ListBox.SelectionMode%2A> propriété détermine le nombre d’éléments pouvant être sélectionné à la fois.  
  
## <a name="ways-to-change-the-listbox-control"></a>Méthodes pour modifier le contrôle de zone de liste  
 Le <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> propriété retourne une valeur entière qui correspond au premier élément sélectionné dans la zone de liste. Vous pouvez modifier par programme l’élément sélectionné en modifiant le <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> de valeur dans le code ; l’élément correspondant dans la liste apparaissent en surbrillance dans le formulaire Windows. Si aucun élément n’est sélectionné, le <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valeur est -1. Si le premier élément dans la liste est sélectionné, le <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valeur est 0. Lorsque plusieurs éléments sont sélectionnés, la <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> valeur reflète l’élément sélectionné apparaît en premier dans la liste. Le <xref:System.Windows.Forms.ListBox.SelectedItem%2A> propriété est similaire à <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, mais retourne l’élément lui-même, en général une valeur de chaîne. Le <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> propriété reflète le nombre d’éléments dans la liste et la valeur de la <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> la propriété a toujours une plus de la plus élevée possible <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> , car la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est de base zéro.  
  
 Pour ajouter ou supprimer des éléments dans un <xref:System.Windows.Forms.ListBox> contrôler, utilisez le <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> (méthode). Vous pouvez également ajouter des éléments à la liste à l’aide de la <xref:System.Windows.Forms.ListBox.Items%2A> propriété au moment du design.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ListBox>  
 [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Guide pratique pour lier un contrôle ComboBox ou ListBox Windows Forms aux données](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Vue d'ensemble du contrôle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Vue d'ensemble du contrôle CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Guide pratique pour créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
