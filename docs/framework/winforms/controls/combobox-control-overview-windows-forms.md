---
title: "Vue d'ensemble du contrôle ComboBox (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 979a410020ab6e3a1f2c15dcee52b062eb00c1ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="combobox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle ComboBox (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ComboBox> contrôle est utilisé pour afficher des données dans une zone de liste déroulante modifiable. Par défaut, le <xref:System.Windows.Forms.ComboBox> contrôle s’affiche en deux parties : la partie supérieure est une zone de texte qui permet à l’utilisateur à taper un élément de liste. La deuxième partie est une zone de liste qui affiche une liste d’éléments à partir de laquelle l’utilisateur peut sélectionner un. Pour plus d’informations sur d’autres styles de zone de liste déroulante, consultez [quand utiliser un contrôle ComboBox Instead of un contrôle ListBox Windows Forms](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 Le <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> propriété retourne une valeur entière qui correspond à l’élément sélectionné. Vous pouvez modifier par programme l’élément sélectionné en modifiant le <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> de valeur dans le code ; l’élément correspondant dans la liste s’affiche dans la zone de texte de la zone de liste déroulante. Si aucun élément n’est sélectionné, le <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valeur est -1. Si le premier élément dans la liste est sélectionné, puis le <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> valeur est 0. Le <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> propriété est similaire à <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , mais retourne l’élément lui-même, en général une valeur de chaîne. Le <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> propriété reflète le nombre d’éléments dans la liste et la valeur de la <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> la propriété a toujours une plus de la plus élevée possible <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> , car la valeur <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est de base zéro.  
  
 Pour ajouter ou supprimer des éléments dans un <xref:System.Windows.Forms.ComboBox> contrôler, utilisez le <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> (méthode). Vous pouvez également ajouter des éléments à la liste à l’aide de la <xref:System.Windows.Forms.ComboBox.Items%2A> propriété dans le concepteur.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ComboBox>  
 [Vue d'ensemble du contrôle ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Guide pratique pour accéder à des éléments spécifiques d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)  
 [Guide pratique pour lier un contrôle ComboBox ou ListBox Windows Forms aux données](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)  
 [Guide pratique pour créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)
