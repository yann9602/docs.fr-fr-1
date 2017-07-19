---
title: "Comment&#160;: impl&#233;menter l&#39;interface ITypedList | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingList(Of T) (classe)"
  - "liaison de données, implémenter"
  - "IBindingList (interface)"
  - "ITypedList (interface)"
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: impl&#233;menter l&#39;interface ITypedList
Implémentez l'interface <xref:System.ComponentModel.ITypedList> pour activer la découverte du schéma pour une liste pouvant être liée.  
  
## Exemple  
 L'exemple de code suivant illustre l'implémentation de l'interface <xref:System.ComponentModel.ITypedList>.  Un type générique nommé `SortableBindingList` dérive de la classe <xref:System.ComponentModel.BindingList%601> et implémente l'interface <xref:System.ComponentModel.ITypedList>.  Une classe simple nommée `Customer` fournit des données, qui sont liées à l'en\-tête d'un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System.Drawing et System.Windows.Forms.  
  
## Voir aussi  
 <xref:System.ComponentModel.ITypedList>   
 <xref:System.ComponentModel.BindingList%601>   
 <xref:System.ComponentModel.IBindingList>   
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)