---
title: "Comment&#160;: impl&#233;menter PriorityBinding | Microsoft Docs"
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
  - "classes, PriorityBinding"
  - "liaison de données, PriorityBinding (classe)"
  - "PriorityBinding (classe)"
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: impl&#233;menter PriorityBinding
<xref:System.Windows.Data.PriorityBinding> dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionne en spécifiant une liste de liaisons.  Cette liste est classée de la priorité la plus élevée à la priorité la plus basse.  Si la liaison de priorité la plus élevée retourne une valeur avec succès lors de son traitement, le traitement des autres liaisons de la liste est inutile.  Dans le cas où l'évaluation de la liaison de priorité la plus élevée nécessite du temps, la priorité la plus élevée suivante qui retourne une valeur avec succès sera alors utilisée jusqu'à ce qu'une liaison d'une priorité supérieure retourne avec succès une valeur.  
  
## Exemple  
 Pour expliquer le fonctionnement de <xref:System.Windows.Data.PriorityBinding>, l'objet `AsyncDataSource` a été créé avec les trois propriétés suivantes : `FastDP`, `SlowerDP` et `SlowestDP`.  
  
 L'accesseur get de `FastDP` retourne la valeur des données membre `_fastDP`.  
  
 L'accesseur get de `SlowerDP` attend trois secondes avant de retourner la valeur des données membre `_slowerDP`.  
  
 L'accesseur get de `SlowestDP` attend cinq secondes avant de retourner la valeur des données membre `_slowestDP`.  
  
> [!NOTE]
>  Cet exemple est fourni à des fins de démonstration uniquement.  Le [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recommande de ne pas définir de propriétés plus lentes que ne le serait un champ set.  Pour plus d'informations, consultez [NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/fr-fr/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 La propriété <xref:System.Windows.Controls.TextBlock.Text%2A> crée une liaison avec `AsyncDS` ci\-dessus à l'aide de <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Lorsque le moteur de liaison traite les objets <xref:System.Windows.Data.Binding>, il commence par le premier élément <xref:System.Windows.Data.Binding>, qui est lié à la propriété `SlowestDP`.  Lorsque cet élément <xref:System.Windows.Data.Binding> est traité, il ne retourne pas de valeur avec succès, car il est en état de veille pour 5 secondes ; l'élément <xref:System.Windows.Data.Binding> suivant est alors traité.  L'élément <xref:System.Windows.Data.Binding> suivant ne retourne pas de valeur avec succès, car il est en état de veille pour 3 secondes.  Le moteur de liaison se place ensuite sur l'objet <xref:System.Windows.Data.Binding> suivant, qui est lié à la propriété `FastDP`.  Cet élément <xref:System.Windows.Data.Binding> retourne la valeur « Fast Value ».  Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « Fast Value ».  
  
 Après 3 secondes, la propriété `SlowerDP` retourne la valeur « Slower Value ».  Le <xref:System.Windows.Controls.TextBlock> affiche ensuite la valeur « Slower Value ».  
  
 Après 5 secondes, la propriété `SlowestDP` retourne la valeur « Slowest Value ».  Cette liaison a la priorité la plus élevée, car elle est affichée en premier.  Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « Slowest Value ».  
  
 Consultez <xref:System.Windows.Data.PriorityBinding> pour plus d'informations sur le concept de valeur de retour avec succès à partir d'une liaison.  
  
## Voir aussi  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=fullName>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)