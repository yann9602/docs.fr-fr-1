---
title: "Comment&#160;: cr&#233;er une table de correspondance pour un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CheckedListBox (contrôle Windows Forms), créer des tables de correspondance"
  - "zones de liste déroulante, tables de correspondance"
  - "ComboBox (contrôle Windows Forms), table de correspondance"
  - "zones de liste, tables de correspondance"
  - "ListBox (contrôle Windows Forms), créer des tables de correspondance"
  - "ListBox (contrôle Windows Forms), tables de correspondance"
  - "tables de correspondance"
  - "tables de correspondance, créer des touches pour les contrôles"
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er une table de correspondance pour un contr&#244;le ComboBox, ListBox ou CheckedListBox Windows Forms
Il est parfois utile d'afficher les données dans un format convivial dans un Windows Form, mais de les stocker dans un format plus pertinent pour votre programme.  Par exemple, un formulaire de commande de produits alimentaires peut présenter les éléments de menu par leur nom dans une zone de liste.  Toutefois, la table de données dans laquelle la commande est enregistrée contient alors les numéros d'ID uniques représentant les produits alimentaires.  Les tableaux ci\-dessous montrent un exemple de stockage et d’affichage des données du formulaire de commande des produits alimentaires.  
  
### OrderDetailsTable  
  
|OrderID|ItemID|Quantité|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### ItemTable  
  
|ID|Nom|  
|--------|---------|  
|12|Pomme de terre|  
|13|Poulet|  
  
 Dans ce scénario, une seule table, OrderDetailsTable, stocke les informations qu'il est réellement nécessaire d'afficher et d'enregistrer.  Cependant, pour économiser de l'espace, elle procède d’une façon plutôt insolite.  L'autre table, ItemTable, contient uniquement des informations d’apparence sur les équivalences entre les numéros d'ID et les noms des produits alimentaires, mais rien en revanche sur les véritables commandes de produits alimentaires.  
  
 ItemTable est connecté au contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> ou <xref:System.Windows.Forms.CheckedListBox> par l’intermédiaire de trois propriétés.  La propriété `DataSource` contient le nom de la table.  La propriété `DisplayMember` contient la colonne de données de la table à afficher dans le contrôle \(nom du produit alimentaire\).  La propriété `ValueMember` contient la colonne de données de la table contenant les informations stockées \(numéro d'ID\).  
  
 OrderDetailsTable est connecté au contrôle par sa collection de liaisons, accessible via la propriété <xref:System.Windows.Forms.Control.DataBindings%2A>.  Quand vous ajoutez un objet de liaison à la collection, vous connectez une propriété du contrôle à une donnée membre spécifique \(la colonne des numéros d'ID\) dans une source de données \(OrderDetailsTable\).  Quand une sélection est effectuée dans le contrôle, c’est dans cette table que l'entrée du formulaire est enregistrée.  
  
### Pour créer une table de choix  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> ou <xref:System.Windows.Forms.CheckedListBox> au formulaire.  
  
2.  Connectez\-vous à la source de données.  
  
3.  Établissez une relation de données entre les deux tables.  Voir [Introduction aux objets DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md).  
  
4.  Définissez les propriétés ci\-dessous.  Elles peuvent être définies dans le code ou dans le concepteur.  
  
    |Propriété|Paramètre|  
    |---------------|---------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Table qui contient des informations sur les équivalences entre les numéros d’ID et les articles.  Dans le scénario précédent, il s’agit de la table `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Colonne de la table de source de données que vous souhaitez afficher dans le contrôle.  Dans le scénario précédent, il s'agit de la colonne `"Name"` \(pour la définir dans le code, utilisez des guillemets\).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Colonne de la table de source de données qui contient les informations stockées.  Dans le scénario précédent, il s'agit de la colonne `"ID"` \(pour la définir dans le code, utilisez des guillemets\).|  
  
5.  Dans une procédure, appelez la méthode <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la classe <xref:System.Windows.Forms.ControlBindingsCollection> pour lier la ppropriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> du contrôle à la table d'enregistrement de l'entrée du formulaire.  Vous pouvez également effectuer cette opération dans le Concepteur plutôt que dans le code, en accédant à la propriété <xref:System.Windows.Forms.Control.DataBindings%2A> du contrôle dans la fenêtre **Propriétés**.  Dans le scénario précédent, il s'agit de `OrderDetailsTable` et la colonne est `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
  
    ```  
  
## Voir aussi  
 [Liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Vue d'ensemble du contrôle ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)