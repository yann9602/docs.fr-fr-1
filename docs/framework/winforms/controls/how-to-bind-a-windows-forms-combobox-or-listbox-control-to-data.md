---
title: "Comment&#160;: lier un contr&#244;le ComboBox ou ListBox Windows Forms aux donn&#233;es | Microsoft Docs"
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
  - "contrôles dépendants, zones de liste déroulante"
  - "zones de liste déroulante, liaison de données"
  - "ComboBox (contrôle Windows Forms), liaison de données"
  - "données (Windows Forms), lier aux contrôles"
  - "liaison de données, zones de liste déroulante"
  - "contrôles liés aux données, Windows Forms"
  - "zones de liste, liaison de données"
  - "ListBox (contrôle Windows Forms), liaison de données"
  - "contrôles Windows Forms, liaison de données"
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: lier un contr&#244;le ComboBox ou ListBox Windows Forms aux donn&#233;es
Vous pouvez lier les <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que parcourir des données dans une base de données, entrer de nouvelles données ou modifier des données existantes.  
  
### Pour lier un contrôle ComboBox ou ListBox  
  
1.  Définissez la propriété `DataSource`  avec un objet de source de données.  Les sources de données possibles sont une <xref:System.Windows.Forms.BindingSource> liée aux données, une table de données, une vue de données, un groupe de données, un gestionnaire de vue de données, un tableau ou toute classe implémentant l'interface <xref:System.Collections.IList>.  Pour plus d'informations, consultez [Sources de données prises en charge par les Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Si vous créez une liaison avec une table, donnez à la propriété `DisplayMember`  le nom d'une colonne dans la source de données.  
  
     \- ou \-  
  
     Si vous créez une liaison avec un <xref:System.Collections.IList>, définissez le membre d'affichage à une propriété publique du type dans la liste.  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
  
    ```  
  
    > [!NOTE]
    >  En cas de liaison à une source de données qui n'implémente pas l'interface <xref:System.ComponentModel.IBindingList>, par exemple un <xref:System.Collections.ArrayList>, les données du contrôle lié ne sont pas mises à jour lorsque la source de données est mise à jour.  Par exemple, si une zone de liste déroulante est liée à une <xref:System.Collections.ArrayList> et que des données sont ajoutées à une <xref:System.Collections.ArrayList>, ces nouveaux éléments n'apparaissent pas dans la zone de liste déroulante.  Cependant, vous pouvez forcer la mise à jour de la zone de liste déroulante en appelant les méthodes <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> sur l'instance de la classe <xref:System.Windows.Forms.BindingContext> à laquelle le contrôle est lié.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Contrôles Windows Forms utilisés pour l'affichage de listes d'options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)