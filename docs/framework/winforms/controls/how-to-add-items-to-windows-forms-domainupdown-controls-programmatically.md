---
title: "Comment&#160;: ajouter par programme des &#233;l&#233;ments aux contr&#244;les DomainUpDown Windows Forms | Microsoft Docs"
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
  - "DomainUpDown (contrôle Windows Forms), ajouter des éléments à"
  - "contrôle toupie, ajouter des éléments"
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ajouter par programme des &#233;l&#233;ments aux contr&#244;les DomainUpDown Windows Forms
Vous pouvez ajouter des éléments au contrôle <xref:System.Windows.Forms.DomainUpDown> Windows Forms dans le code.  Appelez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> pour ajouter des éléments à la propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> du contrôle.  La méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ajoute un élément à la fin d'une collection, tandis que la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> l'ajoute à la position spécifiée.  
  
### Pour ajouter un nouvel élément  
  
1.  À l'aide de la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>, ajoutez un élément à la fin de la liste des éléments.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     ou  
  
2.  À l'aide de la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>, insérez un élément dans la liste à la position que vous spécifiez.  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.DomainUpDown>   
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=fullName>   
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=fullName>   
 [DomainUpDown, contrôle](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)   
 [Vue d'ensemble du contrôle DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)