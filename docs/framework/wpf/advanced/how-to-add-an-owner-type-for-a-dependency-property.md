---
title: "Comment : ajouter un type propriétaire d'une propriété de dépendance"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93934c8f84a7257445b530e27896342bdd73aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Comment : ajouter un type propriétaire d'une propriété de dépendance
Cet exemple montre comment ajouter une classe en tant que propriétaire d’une propriété de dépendance inscrite pour un type différent. Ainsi, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] du lecteur et système de propriétés sont en mesure de reconnaître la classe en tant que propriétaire de la propriété supplémentaire. Ajout en tant que propriétaire éventuellement permet de la classe d’ajout fournir les métadonnées spécifiques au type.  
  
 Dans l’exemple suivant, `StateProperty` est une propriété inscrite par la `MyStateControl` classe. La classe `UnrelatedStateControl` ajoute lui-même en tant que propriétaire de la `StateProperty` à l’aide de la <xref:System.Windows.DependencyProperty.AddOwner%2A> méthode, en particulier à l’aide de la signature qui permet de nouvelles métadonnées de la propriété de dépendance telle qu’elle existe sur le type d’ajout. Notez que vous devez fournir [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accesseurs de la propriété semblable à l’exemple illustré dans la [implémenter une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) exemple, ainsi que de nouveau exposer l’identificateur de propriété de dépendance dans la classe ajoutée en tant que propriétaire.  
  
 Sans wrappers, la propriété de dépendance continuerait de fonctionner du point de vue de l’accès par programme à l’aide <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>. Mais vous souhaiterez généralement parallèlement ce comportement de système de propriétés avec le [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wrappers de propriété. Les wrappers rendre plus facile de définir la propriété de dépendance par programme et permettent de définir les propriétés comme [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributs.  
  
 Pour savoir comment remplacer les métadonnées par défaut, consultez [remplacer les métadonnées pour une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
