---
title: "Comment&#160;: donner un style aux contr&#244;les d&#39;une barre d&#39;outils | Microsoft Docs"
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
  - "personnaliser les contrôles dans la barre d'outils"
  - "appliquer un style aux contrôles dans la barre d'outils"
  - "barres d'outils"
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: donner un style aux contr&#244;les d&#39;une barre d&#39;outils
<xref:System.Windows.Controls.ToolBar> définit des objets <xref:System.Windows.ResourceKey> pour spécifier le style des contrôles dans <xref:System.Windows.Controls.ToolBar>.  Pour affecter un style à un contrôle <xref:System.Windows.Controls.ToolBar>, définissez l'attribut `x:key` du style de <xref:System.Windows.ResourceKey> défini dans <xref:System.Windows.Controls.ToolBar>.  
  
 <xref:System.Windows.Controls.ToolBar> définit les objets de <xref:System.Windows.ResourceKey> suivants :  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## Exemple  
 L'exemple suivant définit les styles des contrôles dans <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)