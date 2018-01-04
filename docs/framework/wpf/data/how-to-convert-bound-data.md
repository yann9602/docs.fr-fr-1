---
title: "Comment : convertir des données liées"
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
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f4bcde15940e76e1d022658e32ff6ef8676e45e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-bound-data"></a>Comment : convertir des données liées
Cet exemple montre comment appliquer la conversion de données qui sont utilisées dans les liaisons.  
  
 Pour convertir des données lors de la liaison, vous devez créer une classe qui implémente le <xref:System.Windows.Data.IValueConverter> interface, qui inclut le <xref:System.Windows.Data.IValueConverter.Convert%2A> et <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> méthodes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’implémentation d’un convertisseur de date qui convertit la valeur de date passée pour qu’il affiche uniquement l’année, mois et jour. Lorsque vous implémentez le <xref:System.Windows.Data.IValueConverter> interface, il est conseillé de décorer l’implémentation avec un <xref:System.Windows.Data.ValueConversionAttribute> attribut pour indiquer au développement d’outils de types de données impliqués dans la conversion, comme dans l’exemple suivant :  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 Une fois que vous avez créé un convertisseur, vous pouvez l’ajouter en tant que ressource dans votre [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] fichier. Dans l’exemple suivant, *src* est mappé à l’espace de noms dans lequel *convertisseur de date* est défini.  
  
 [!code-xaml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 Enfin, vous pouvez utiliser le convertisseur dans votre liaison à l’aide de la syntaxe suivante. Dans l’exemple suivant, le contenu textuel de la <xref:System.Windows.Controls.TextBlock> est lié à *StartDate*, qui est une propriété de source de données externe.  
  
 [!code-xaml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 Les ressources de style référencées dans l’exemple ci-dessus sont définies dans une section de ressources ne pas présentée dans cette rubrique.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter la validation de la liaison](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
