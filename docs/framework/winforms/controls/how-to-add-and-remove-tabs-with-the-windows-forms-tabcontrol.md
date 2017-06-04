---
title: "Comment&#160;: ajouter et supprimer des onglets avec le contr&#244;le TabControl Windows Forms | Microsoft Docs"
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
  - "pages d'onglets"
  - "TabControl (contrôle Windows Forms), ajouter et supprimer des onglets"
  - "TabPage (contrôle)"
  - "onglets, ajouter aux pages"
  - "onglets, supprimer des pages"
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter et supprimer des onglets avec le contr&#244;le TabControl Windows Forms
Par défaut, un contrôle <xref:System.Windows.Forms.TabControl> contient deux contrôles <xref:System.Windows.Forms.TabPage>.  Vous pouvez accéder à ces onglets par l'intermédiaire de la propriété <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
### Pour ajouter un onglet par programme  
  
-   Utilisez la méthode <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> de la propriété <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### Pour supprimer un onglet par programme  
  
-   Pour supprimer les onglets sélectionnés, utilisez la méthode <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> de la propriété <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
     ou  
  
-   Pour supprimer tous les onglets, utilisez la méthode <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> de la propriété <xref:System.Windows.Forms.TabControl.TabPages%2A>.  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du contrôle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [Comment : ajouter un contrôle à une page d'onglet](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [Comment : désactiver les pages d'onglets](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [Comment : modifier l'apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)