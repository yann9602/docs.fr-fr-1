---
title: "Comment&#160;: partager des propri&#233;t&#233;s de dimensionnement entre grilles | Microsoft Docs"
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
  - "Grid (contrôle), partager des données de dimensionnement de colonnes"
  - "Grid (contrôle), partager des données de dimensionnement de lignes"
  - "données de dimensionnement dans des contrôles Grid"
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: partager des propri&#233;t&#233;s de dimensionnement entre grilles
Cet exemple montre comment partager les données de dimensionnement des colonnes et des lignes entre des éléments <xref:System.Windows.Controls.Grid> afin de conserver une taille cohérente.  
  
## Exemple  
 L'exemple suivant présente deux éléments <xref:System.Windows.Controls.Grid> comme éléments enfants d'un <xref:System.Windows.Controls.DockPanel>parent.  La [propriété attachée](GTMT) <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> de <xref:System.Windows.Controls.Grid> est définie sur le <xref:System.Windows.Controls.DockPanel> parent.  
  
 L'exemple manipule la valeur de propriété en utilisant deux éléments <xref:System.Windows.Controls.Button>, représentant chacun une des valeurs de propriétés booléennes.  Lorsque la valeur de propriété <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> est `true`, chaque membre de colonne ou de ligne d'un <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> partage des informations sur la taille, quel que soit le contenu d'une ligne ou d'une colonne.  
  
 [!code-xml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 L'exemple de code\-behind suivant gère les méthodes que l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> de bouton déclenche.  L'exemple écrit les résultats de ces appels de méthode dans les éléments <xref:System.Windows.Controls.TextBlock> qui utilisent des méthodes get associées pour sortir les nouvelles valeurs de propriété comme chaînes.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>   
 [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)