---
title: "Comment&#160;: supprimer des &#233;l&#233;ments des contr&#244;les DomainUpDown Windows Forms | Microsoft Docs"
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
  - "DomainUpDown (contrôle Windows Forms), supprimer des éléments de"
  - "contrôle toupie, supprimer des éléments"
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: supprimer des &#233;l&#233;ments des contr&#244;les DomainUpDown Windows Forms
Vous pouvez supprimer des éléments du contrôle <xref:System.Windows.Forms.DomainUpDown> Windows Forms en appelant la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>.  La méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> supprime un élément précis, alors que la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> supprime un élément selon sa position.  
  
### Pour supprimer un élément  
  
-   Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> pour supprimer un élément selon son nom.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     ou  
  
-   Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> pour supprimer un élément d'après sa position.  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.DomainUpDown>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=fullName>   
 [DomainUpDown, contrôle](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)   
 [Vue d'ensemble du contrôle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)