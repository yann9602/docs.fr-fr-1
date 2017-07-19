---
title: "Comment&#160;: produire une valeur en fonction d&#39;une liste d&#39;&#233;l&#233;ments li&#233;s | Microsoft Docs"
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
  - "liaison de données, MultiBinding"
  - "MultiBinding"
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: produire une valeur en fonction d&#39;une liste d&#39;&#233;l&#233;ments li&#233;s
<xref:System.Windows.Data.MultiBinding> vous permet de lier une propriété [cible de liaison](GTMT) à une liste de propriétés source, puis d'appliquer une logique pour produire une valeur à l'aide des entrées fournies.  Cet exemple montre comment utiliser <xref:System.Windows.Data.MultiBinding>.  
  
## Exemple  
 Dans l'exemple suivant, `NameListData` fait référence à une collection d'objets `PersonName`, qui contiennent deux propriétés, `firstName` et `lastName`.  L'exemple suivant produit un <xref:System.Windows.Controls.TextBlock> qui affiche le nom et le prénom d'une personne, en commençant par le nom.  
  
 [!code-xml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 Pour comprendre comment est réalisé le format nom\-prénom, observons l'implémentation de `NameConverter`:  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` implémente l'interface <xref:System.Windows.Data.IMultiValueConverter>.  `NameConverter` prend les valeurs des liaisons individuelles et les stocke dans le tableau d'objets de valeurs.  L'ordre dans lequel les éléments <xref:System.Windows.Data.Binding> apparaissent sous l'élément <xref:System.Windows.Data.MultiBinding> est l'ordre de placement des valeurs dans le tableau.  La valeur de l'attribut <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> est référencée par l'argument de paramètre de la méthode <xref:System.Windows.Data.MultiBinding.Converter%2A>, qui bascule le paramètre pour déterminer comment formater le nom.  
  
## Voir aussi  
 [Convertir des données liées](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)