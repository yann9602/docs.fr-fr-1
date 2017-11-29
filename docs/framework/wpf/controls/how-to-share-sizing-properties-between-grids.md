---
title: "Comment : partager des propriétés de dimensionnement entre grilles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f0e3be0a0b550f6fbbc9876709094d4a23abe1a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-sizing-properties-between-grids"></a>Comment : partager des propriétés de dimensionnement entre grilles
Cet exemple montre comment partager les données de dimensionnement des colonnes et des lignes entre <xref:System.Windows.Controls.Grid> éléments afin de conserver une taille cohérente.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente deux <xref:System.Windows.Controls.Grid> éléments en tant qu’éléments enfants d’un parent <xref:System.Windows.Controls.DockPanel>. Le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> propriété de jointe <xref:System.Windows.Controls.Grid> est défini sur le parent <xref:System.Windows.Controls.DockPanel>.  
  
 L’exemple manipule la valeur de propriété à l’aide de deux <xref:System.Windows.Controls.Button> éléments ; chaque élément représente une des valeurs de propriété booléenne. Lorsque le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> propriété a la valeur `true`, chaque membre de colonne ou ligne d’un <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> partage des informations sur le dimensionnement, quel que soit le contenu d’une ligne ou colonne.  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 L’exemple de code-behind suivant gère les méthodes que le bouton <xref:System.Windows.Controls.Primitives.ButtonBase.Click> déclenche des événements. L’exemple écrit les résultats de ces appels de méthode <xref:System.Windows.Controls.TextBlock> éléments liée de l’utilisation des méthodes get pour sortir les nouvelles valeurs de propriété sous forme de chaînes.  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md)
