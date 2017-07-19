---
title: "Comment&#160;: afficher une marque d&#39;insertion dans un contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "glisser-déplacer, marques d'insertion"
  - "graphiques, marques d'insertion"
  - "marques d'insertion"
  - "ListView (contrôle Windows Forms), opérations glisser"
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: afficher une marque d&#39;insertion dans un contr&#244;le ListView Windows Forms
La marque d'insertion dans le contrôle <xref:System.Windows.Forms.ListView> indique aux utilisateurs l'emplacement où les éléments déplacés seront insérés.  Quand un utilisateur fait glisser un élément vers un point entre deux autres éléments, la marque d'insertion indique le nouvel emplacement prévu de l'élément.  
  
> [!NOTE]
>  La fonctionnalité de marque d'insertion est disponible uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quand votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>.  Sur les systèmes d'exploitation antérieurs, tout code relatif à la marque d'insertion n'a aucun effet et la marque d'insertion n'apparaît pas.  Pour plus d'informations, consultez <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 L'illustration suivante montre une marque d'insertion :  
  
 ![Marque d'insertion ListView](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")  
  
 L'exemple de code suivant montre comment utiliser cette fonctionnalité.  
  
## Exemple  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ListViewInsertionMark>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/fr-fr/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [Procédure pas à pas : exécution d'opérations de glisser\-déplacer dans Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)