---
title: "Comment : rechercher un élément par son nom"
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 62e5cc9c65afe9da9c77d06c103e99d3ff8d995a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a>Comment : rechercher un élément par son nom
Cet exemple explique comment utiliser le <xref:System.Windows.FrameworkElement.FindName%2A> méthode pour rechercher un élément par son <xref:System.Windows.FrameworkElement.Name%2A> valeur.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la méthode à rechercher un élément particulier par son nom est écrit en tant que le Gestionnaire d’événements d’un bouton. `stackPanel`est la <xref:System.Windows.FrameworkElement.Name%2A> de la racine de <xref:System.Windows.FrameworkElement> recherché, et la méthode d’exemple indique ensuite visuellement l’élément trouvé en effectuant un cast en tant que <xref:System.Windows.Controls.TextBlock> et modifier l’un de le <xref:System.Windows.Controls.TextBlock> visible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriétés.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
