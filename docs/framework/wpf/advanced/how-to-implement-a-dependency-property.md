---
title: "Guide pratique pour implémenter une propriété de dépendance"
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
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bc4dee8f0b2eef76e5769ae7da3a13edf7c3300
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-dependency-property"></a>Guide pratique pour implémenter une propriété de dépendance
Cet exemple montre comment sauvegarder un [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] propriété avec un <xref:System.Windows.DependencyProperty> champ, définissant ainsi une propriété de dépendance. Quand vous définissez vos propres propriétés et que vous souhaitez qu’elles prennent en charge de nombreux aspects des fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], notamment les styles, la liaison de données, l’héritage, l’animation et les valeurs par défaut, vous devez les implémenter en tant que propriétés de dépendance.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant enregistre tout d’abord une propriété de dépendance en appelant le <xref:System.Windows.DependencyProperty.Register%2A> (méthode). Le nom du champ d’identificateur que vous utilisez pour stocker le nom et de caractéristiques de la propriété de dépendance doivent être le <xref:System.Windows.DependencyProperty.Name%2A> vous avez choisi pour la propriété de dépendance dans le cadre de la <xref:System.Windows.DependencyProperty.Register%2A> appel, ajouté par la chaîne littérale `Property`. Par exemple, si vous inscrivez une propriété de dépendance avec un <xref:System.Windows.DependencyProperty.Name%2A> de `Location`, le champ d’identificateur que vous définissez pour la propriété de dépendance doit être nommé `LocationProperty`.  
  
 Dans cet exemple, le nom de la propriété de dépendance et son [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accesseur est `State`; le champ d’identificateur est `StateProperty`; le type de la propriété est <xref:System.Boolean>; et le type qui inscrit la propriété de dépendance est `MyStateControl`.  
  
 Si vous ne respectez pas ce modèle d’affectation de noms, les concepteurs risquent de ne pas signaler correctement votre propriété et certains aspects de l’application des styles du système de propriétés risquent de ne pas se comporter comme prévu.  
  
 Vous pouvez également spécifier des métadonnées par défaut pour une propriété de dépendance. Cet exemple inscrit `false` comme valeur par défaut de la propriété de dépendance `State`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Pour plus d’informations sur la façon d’implémenter une propriété de dépendance et sur les raisons pour lesquelles vous devriez le faire, plutôt que de simplement stocker une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] dans un champ privé, consultez [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
