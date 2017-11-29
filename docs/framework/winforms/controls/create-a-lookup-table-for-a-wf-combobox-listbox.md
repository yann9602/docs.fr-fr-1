---
title: "Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb7ffb8a7f20c1e53b24a1db8bda326d73743a93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Comment : créer une table de correspondance pour un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms
Il est parfois utile d'afficher les données dans un format convivial dans un Windows Form, mais de les stocker dans un format plus pertinent pour votre programme. Par exemple, un formulaire de commande de produits alimentaires peut présenter les éléments de menu par leur nom dans une zone de liste. Toutefois, la table de données dans laquelle la commande est enregistrée contient alors les numéros d'ID uniques représentant les produits alimentaires. Les tableaux ci-dessous montrent un exemple de stockage et d’affichage des données du formulaire de commande des produits alimentaires.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Quantité|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|Nom|  
|--------|----------|  
|12|Pomme de terre|  
|13|Poulet|  
  
 Dans ce scénario, une table, **OrderDetailsTable**, stocke les informations d’affichage et l’enregistrement. Cependant, pour économiser de l'espace, elle procède d’une façon plutôt insolite. L’autre table, **ItemTable**, contient uniquement des informations relatives à l’apparence sur le ID de nombre équivaut au nom de produit alimentaire et rien sur les commandes de produits alimentaires réel.  
  
 Le **ItemTable** est connecté à la <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, ou <xref:System.Windows.Forms.CheckedListBox> via trois propriétés. Le `DataSource` propriété contient le nom de la table. Le `DisplayMember` propriété contient la colonne de données de la table que vous souhaitez afficher dans le contrôle (nom de produit alimentaire). Le `ValueMember` propriété contient la colonne de données de la table contenant les informations stockées (le numéro d’ID).  
  
 Le **OrderDetailsTable** est connecté au contrôle par sa collection de liaisons, accédée via la <xref:System.Windows.Forms.Control.DataBindings%2A> propriété. Lorsque vous ajoutez un objet de liaison à la collection, vous connectez une propriété du contrôle à une donnée membre spécifique (la colonne des numéros d’ID) dans une source de données (la **OrderDetailsTable**). Quand une sélection est effectuée dans le contrôle, c’est dans cette table que l'entrée du formulaire est enregistrée.  
  
### <a name="to-create-a-lookup-table"></a>Pour créer une table de choix  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> ou <xref:System.Windows.Forms.CheckedListBox> au formulaire.  
  
2.  Connectez-vous à la source de données.  
  
3.  Établissez une relation de données entre les deux tables. Consultez [Introduction aux objets DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Définissez les propriétés ci-dessous. Elles peuvent être définies dans le code ou dans le concepteur.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Table qui contient des informations sur les équivalences entre les numéros d’ID et les articles. Dans le scénario précédent, il s’agit de `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Colonne de la table de source de données que vous souhaitez afficher dans le contrôle. Dans le scénario précédent, il s’agit `"Name"` (pour la définir dans le code, utilisez des guillemets doubles).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Colonne de la table de source de données qui contient les informations stockées. Dans le scénario précédent, il s’agit `"ID"` (pour la définir dans le code, utilisez des guillemets doubles).|  
  
5.  Dans une procédure, appelez la méthode <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> de la classe <xref:System.Windows.Forms.ControlBindingsCollection> pour lier la ppropriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> du contrôle à la table d'enregistrement de l'entrée du formulaire. Vous pouvez également le faire dans le concepteur plutôt que dans le code, en accédant à du contrôle <xref:System.Windows.Forms.Control.DataBindings%2A> propriété dans le **propriétés** fenêtre. Dans le scénario précédent, il s’agit de `OrderDetailsTable`, et la colonne est `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Vue d'ensemble du contrôle ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Vue d'ensemble du contrôle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Vue d'ensemble du contrôle CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
