---
title: "Comment : rendre des données disponibles pour la liaison en XAML"
ms.custom: 
ms.date: 01/29/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f4e8e785b246e191ae8052f676331ea116b8c0d
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2018
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Comment : rendre des données disponibles pour la liaison en XAML
Cette rubrique décrit les différentes façons de vous rendre les données disponibles pour la liaison dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], en fonction des besoins de votre application.  
  
## <a name="example"></a>Exemple  
 Si vous avez un [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vous souhaitez lier à partir de l’objet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], une façon de faire l’objet disponible pour la liaison est pour la définir en tant que ressource et lui donner un `x:Key`. Dans l’exemple suivant, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`. Le `Person` objet, qui est indiqué par la ligne en surbrillance qui contient le `<src>` élément, est défini dans l’espace de noms appelé `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Vous pouvez ensuite lier la <xref:System.Windows.Controls.TextBlock> contrôle à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme la mise en surbrillance de la ligne qui contient le `<TextBlock>` affiche de l’élément. 
  
 Vous pouvez également utiliser le <xref:System.Windows.Data.ObjectDataProvider> (classe), comme dans l’exemple suivant :  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vous définissez la liaison de la même façon, la ligne en surbrillance qui contient le `<TextBlock>` affiche de l’élément.  
  
 Dans cet exemple particulier, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe`. Toutefois, la <xref:System.Windows.Data.ObjectDataProvider> classe fournit des fonctionnalités telles que la capacité à lier au résultat d’une méthode. Vous pouvez choisir d’utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe si vous avez besoin de la fonctionnalité qu’elle fournit.  
  
 Toutefois, si vous établissez une liaison à un objet qui a déjà été créé, vous devez définir le `DataContext` dans le code, comme dans l’exemple suivant.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pour accéder à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données de la liaison à l’aide du <xref:System.Windows.Data.XmlDataProvider> de classe, consultez [lier à l’aide de données XML, requêtes XMLDataProvider et XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pour accéder à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données de la liaison à l’aide du <xref:System.Windows.Data.ObjectDataProvider> de classe, consultez [lier à XDocument, XElement ou LINQ pour des résultats de requête XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Pour plus d’informations sur les différentes méthodes que vous pouvez spécifier les données que vous liez à, consultez [spécifier la Source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Pour plus d’informations sur les types de données que vous pouvez lier à ou comment implémenter votre propre [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objets pour la liaison, consultez [vue d’ensemble des Sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
