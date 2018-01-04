---
title: "Comment : définir et référencer une ressource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 173be3048f7bf082db2eef2ea21eb1e0319f9a43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-and-reference-a-resource"></a>Comment : définir et référencer une ressource
Cet exemple montre comment définir une ressource et y fait référence à l’aide d’un attribut dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit deux types de ressources : un <xref:System.Windows.Media.SolidColorBrush> ressources et plusieurs <xref:System.Windows.Style> ressources. Le <xref:System.Windows.Media.SolidColorBrush> ressource `MyBrush` est utilisée pour fournir la valeur de plusieurs propriétés qui prennent chacune un <xref:System.Windows.Media.Brush> de type valeur. Le <xref:System.Windows.Style> ressources `PageBackground`, `TitleText` et `Label` chaque cible d’un type de contrôle particulier. Les styles de définissent diverses propriétés différentes sur les contrôles ciblés lorsque cette ressource de style est référencée par la clé de ressource et qu’il est utilisée pour définir le <xref:System.Windows.FrameworkElement.Style%2A> propriétés de plusieurs éléments de contrôle spécifiques définis dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Notez que l’une des propriétés des accesseurs Set de la `Label` style fait également référence à la `MyBrush` ressources définis précédemment. Il s’agit d’une technique courante, mais il est important de se rappeler que les ressources sont analysées et entrés dans un dictionnaire de ressources dans l’ordre où elles sont fournies. Ressources sont également demandées dans l’ordre qui se trouvent dans le dictionnaire si vous utilisez la [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) de les référencer à partir d’une autre ressource. Assurez-vous que toutes les ressources que vous référencez sont défini plus haut dans la collection de ressources où cette ressource est demandée. Si nécessaire, vous pouvez contourner l’ordre strict de création des références de ressources à l’aide un [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) fassent référence à la ressource lors de l’exécution à la place, mais vous devez être conscient que cette DynamicResource technique a des conséquences sur les performances. Pour plus d’informations, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)
