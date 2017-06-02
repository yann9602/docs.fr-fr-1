---
title: "Comment&#160;: cr&#233;er un style pour un en-t&#234;te de colonne GridView d&#233;plac&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôles ListView, appliquer un style"
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er un style pour un en-t&#234;te de colonne GridView d&#233;plac&#233;
Cet exemple montre comment modifier l'apparence d'un <xref:System.Windows.Controls.GridViewColumnHeader> déplacé lorsque l'utilisateur change la position d'une colonne.  
  
## Exemple  
 Lorsque vous déplacez un en\-tête de colonne à un autre emplacement dans un <xref:System.Windows.Controls.ListView> qui utilise <xref:System.Windows.Controls.GridView> comme mode d'affichage, la colonne est déplacée à la nouvelle position.  Lorsque vous déplacez l'en\-tête de colonne, une copie flottante de l'en\-tête apparaît en plus de l'en\-tête d'origine.  Dans un <xref:System.Windows.Controls.GridView>, un en\-tête de colonne est représenté par un objet <xref:System.Windows.Controls.GridViewColumnHeader>.  
  
 Pour personnaliser l'apparence des en\-têtes flottant et d'origine, vous pouvez définir des <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> pour modifier le <xref:System.Windows.Style> <xref:System.Windows.Controls.GridViewColumnHeader>.  Ces <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> sont appliqués lorsque la valeur de la propriété <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> est `true` et que la valeur de la propriété <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> est <xref:System.Windows.Controls.GridViewColumnHeaderRole>.  
  
 Lorsque l'utilisateur appuie sur le bouton de la souris et le maintient enfoncé quand la souris passe sur le <xref:System.Windows.Controls.GridViewColumnHeader>, la valeur de la propriété <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> devient `true`.  De même, lorsque l'utilisateur commence l'opération de glissement, la propriété <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> devient <xref:System.Windows.Controls.GridViewColumnHeaderRole>.  
  
 L'exemple suivant montre comment définir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> pour modifier les couleurs de <xref:System.Windows.Controls.Control.Foreground%2A> et d'<xref:System.Windows.Controls.Control.Background%2A> des en\-têtes flottant et d'origine lorsque l'utilisateur déplace une colonne à une nouvelle position.  
  
 [!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [Vue d'ensemble de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [Vue d'ensemble de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)