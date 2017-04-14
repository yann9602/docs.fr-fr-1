---
title: "Vue d&#39;ensemble du contr&#244;le ListBox (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "zones de liste, à propos des zones de liste"
  - "ListBox (contrôle Windows Forms), à propos du contrôle ListBox"
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble du contr&#244;le ListBox (Windows Forms)
Un contrôle <xref:System.Windows.Forms.ListBox> Windows Forms affiche une liste d'éléments dans laquelle l'utilisateur peut effectuer un ou plusieurs choix.  Si le nombre total d'éléments excède la capacité d'affichage, une barre de défilement est automatiquement ajoutée au contrôle <xref:System.Windows.Forms.ListBox>.  Lorsque la propriété <xref:System.Windows.Forms.ListBox.MultiColumn%2A> a la valeur `true`, la zone de liste affiche des éléments dans plusieurs colonnes et une barre de défilement horizontale s'affiche.  Lorsque la propriété <xref:System.Windows.Forms.ListBox.MultiColumn%2A> a la valeur `false`, la zone de liste affiche des éléments dans une seule colonne et une barre de défilement verticale s'affiche.  Lorsque la propriété <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> a la valeur `true`, la barre de défilement s'affiche, quel que soit le nombre d'éléments.  La propriété <xref:System.Windows.Forms.ListBox.SelectionMode%2A> détermine le nombre d'éléments pouvant être sélectionnés en même temps.  
  
## Modes de modification du contrôle ListBox  
 La propriété <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> retourne une valeur entière correspondant au premier élément sélectionné dans la zone de liste.  Vous pouvez modifier par programme l'élément sélectionné en changeant la valeur de la propriété <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> dans le code ; l'élément de liste correspondant est affiché en surbrillance dans le Windows Form.  Si aucun élément n'est sélectionné, la valeur de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est \-1.  Si le premier élément dans la liste est sélectionné, la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est 0.  Lorsque plusieurs éléments sont sélectionnées, la valeur <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> reflète l'élément sélectionné qui s'affiche en premier dans la liste.  La propriété <xref:System.Windows.Forms.ListBox.SelectedItem%2A> est similaire à la propriété <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, à cela près qu'elle retourne l'élément lui\-même, en général une valeur de chaîne.  La propriété <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> indique le nombre d'éléments contenus dans la liste et la valeur de la propriété <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> est toujours supérieure d'une unité à celle de la plus haute valeur de <xref:System.Windows.Forms.ListBox.SelectedIndex%2A>, car la propriété <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> est numérotée à partir de zéro.  
  
 Pour ajouter ou supprimer des éléments dans un contrôle <xref:System.Windows.Forms.ListBox>, utilisez la méthode <xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A>.  Au moment du design, vous pouvez également ajouter des éléments à la liste en utilisant la propriété <xref:System.Windows.Forms.ListBox.Items%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListBox>   
 [Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [Vue d'ensemble du contrôle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)