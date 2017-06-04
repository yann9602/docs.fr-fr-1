---
title: "Comment&#160;: ajouter des &#233;l&#233;ments de menu &#224; un ContextMenuStrip | Microsoft Docs"
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
  - "menus contextuels, ajouter des éléments de menu"
  - "ContextMenuStrips, ajouter des éléments de menu"
  - "menus contextuels, ajouter des éléments"
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: ajouter des &#233;l&#233;ments de menu &#224; un ContextMenuStrip
Vous pouvez ajouter un seul ou plusieurs éléments de menu à la fois à un <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### Pour ajouter un seul élément de menu à ContextMenuStrip  
  
-   Utilisez la méthode <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> pour ajouter un élément de menu à un <xref:System.Windows.Forms.ContextMenuStrip>.  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### Pour ajouter plusieurs éléments de menu à ContextMenuStrip  
  
-   Utilisez la méthode <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> pour ajouter plusieurs éléments de menu à un <xref:System.Windows.Forms.ContextMenuStrip>.  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## Voir aussi  
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)