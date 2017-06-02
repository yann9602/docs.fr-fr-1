---
title: "Vue d&#39;ensemble du contr&#244;le ComboBox (Windows Forms) | Microsoft Docs"
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
  - "ComboBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "zones de liste déroulante, à propos des zones de liste déroulante"
  - "ComboBox (contrôle Windows Forms), à propos du contrôle ComboBox"
  - "listes déroulantes, ComboBox (contrôle)"
  - "listes déroulantes, Windows Forms"
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du contr&#244;le ComboBox (Windows Forms)
Le contrôle <xref:System.Windows.Forms.ComboBox> Windows Forms permet d'afficher des données dans une zone de liste déroulante fixe.  Par défaut, le contrôle <xref:System.Windows.Forms.ComboBox> comporte deux parties. Dans la partie supérieure figure une zone de texte dans laquelle l'utilisateur peut taper le nom d'un élément de la liste.  La seconde partie comprend une zone de liste dans laquelle l'utilisateur peut sélectionner un élément.  Pour plus d'informations sur d'autres styles de zone de liste déroulante, consultez [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md).  
  
 La propriété <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> retourne un entier correspondant à l'élément de liste sélectionné.  Vous pouvez modifier par programme l'élément sélectionné en changeant la valeur de la propriété <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> dans le code ; l'élément de liste correspondant apparaîtra dans la zone de texte de la zone de liste déroulante.  Si aucun élément n'est sélectionné, la valeur de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est \-1.  Si le premier élément de la liste est sélectionné, la valeur de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est 0.  La propriété <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> est similaire à la propriété <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, à cela près qu'elle retourne l'élément lui\-même, en général une valeur de chaîne.  La propriété <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> indique le nombre d'éléments contenus dans la liste et la valeur de la propriété <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> est toujours supérieure d'une unité à celle de la plus haute valeur de <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>, car la propriété <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> est numérotée à partir de zéro.  
  
 Pour ajouter ou supprimer des éléments dans un contrôle <xref:System.Windows.Forms.ComboBox>, utilisez la méthode <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> ou <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>.  Vous pouvez également ajouter des éléments à la liste en utilisant la propriété <xref:System.Windows.Forms.ComboBox.Items%2A> dans le concepteur.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 [Vue d'ensemble du contrôle ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [Comment : ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [Comment : trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [Comment : accéder à des éléments spécifiques d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)   
 [Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)