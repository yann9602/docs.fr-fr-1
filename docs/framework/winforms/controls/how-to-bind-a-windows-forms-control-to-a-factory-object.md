---
title: "Comment&#160;: lier un contr&#244;le Windows Forms &#224; un objet Factory | Microsoft Docs"
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
  - "BindingSource (composant Windows Forms), lier à un objet de fabrique"
  - "BindingSource (composant Windows Forms), exemples"
  - "contrôles (Windows Forms), liaison"
  - "objets de fabrique, lier à"
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: lier un contr&#244;le Windows Forms &#224; un objet Factory
Quand vous créez des contrôles qui interagissent avec des données, vous devez parfois lier un contrôle à un objet ou à une méthode qui génère d'autres objets.  Un tel objet ou une telle méthode porte le nom de fabrique.  Votre source de données peut par exemple être la valeur de retour d'un appel de méthode, plutôt qu'un objet en mémoire ou un type.  Vous pouvez lier un contrôle à ce genre de source de données tant que la source retourne une collection.  
  
 Vous pouvez facilement lier un contrôle à un objet de fabrique à l'aide du contrôle <xref:System.Windows.Forms.BindingSource>.  
  
## Exemple  
 L'exemple suivant montre comment lier un contrôle <xref:System.Windows.Forms.DataGridView> à une méthode de fabrique à l'aide d'un contrôle <xref:System.Windows.Forms.BindingSource>.  La méthode de fabrique se nomme `GetOrdersByCustomerId` et retourne toutes les commandes pour un client donné dans la base de données Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)