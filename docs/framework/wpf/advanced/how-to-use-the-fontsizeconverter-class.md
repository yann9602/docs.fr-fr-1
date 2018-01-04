---
title: Guide pratique pour utiliser la classe FontSizeConverter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe6988f21c2e40c65a7e8acd48727ab48bd58e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Guide pratique pour utiliser la classe FontSizeConverter
## <a name="example"></a>Exemple  
 Cet exemple montre comment créer une instance de <xref:System.Windows.FontSizeConverter> et l’utiliser pour modifier la taille de police.  
  
 L’exemple définit une méthode personnalisée appelée `changeSize` qui convertit le contenu d’un <xref:System.Windows.Controls.ListBoxItem>, tel que défini dans une fonction [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier, à une instance de <xref:System.Double>et versions ultérieures dans un <xref:System.String>. Cette méthode passe le <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.FontSizeConverter> objet, qui convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> d’un <xref:System.Windows.Controls.ListBoxItem> à une instance de <xref:System.Double>. Cette valeur est ensuite retournée comme la valeur de la <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriété de la <xref:System.Windows.Controls.TextBlock> élément.  
  
 Cet exemple définit également une deuxième méthode personnalisée qui est appelée `changeFamily`. Cette méthode convertit le <xref:System.Windows.Controls.ContentControl.Content%2A> de la <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.String>, puis passe cette valeur à la <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriété de la <xref:System.Windows.Controls.TextBlock> élément.  
  
 Cet exemple ne s’exécute pas.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.FontSizeConverter>
