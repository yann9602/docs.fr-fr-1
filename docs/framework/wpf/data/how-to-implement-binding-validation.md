---
title: "Comment&#160;: impl&#233;menter la validation de la liaison | Microsoft Docs"
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
  - "liaison, validation de"
  - "liaison de données, validation de liaison"
  - "validation de liaison"
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: impl&#233;menter la validation de la liaison
Cet exemple montre comment utiliser un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> et un déclencheur de style pour fournir la rétroaction visuelle pour signaler à l'utilisateur l'entrée d'une valeur non valide en fonction d'une règle de validation personnalisée.  
  
## Exemple  
 Le contenu de texte de la <xref:System.Windows.Controls.TextBox> dans l'exemple suivant est lié à la propriété `Age` \(de type int\) d'un objet [de source de liaison](GTMT) nommé `ods`.  La liaison est définie pour utiliser la règle de validation `AgeRangeRule` pour que, lorsque l'utilisateur entre des caractères non numériques ou une valeur inférieure à 21 ou supérieure à 130, un point d'exclamation rouge apparaisse à côté de la zone de texte et une info\-bulle avec le message d'erreur s'affiche lorsque l'utilisateur place le pointeur de la souris sur la zone de texte.  
  
 [!code-xml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 L'exemple suivant montre l'implémentation `AgeRangeRule` qui hérite de <xref:System.Windows.Controls.ValidationRule> et remplace la méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A>.  La méthode Int32.Parse \(\) est appelée sur la valeur pour vérifier qu'elle ne contient pas de caractères non valides.  La méthode <xref:System.Windows.Controls.ValidationRule.Validate%2A> retourne un <xref:System.Windows.Controls.ValidationResult> qui indique si la valeur est valide en fonction de l'interception d'une exception pendant l'analyse et si la valeur d'âge ne se trouve pas entre la limite inférieure et la limite supérieure.  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 L'exemple suivant montre le <xref:System.Windows.Controls.ControlTemplate>`validationTemplate` personnalisé qui crée un point d'exclamation rouge pour signaler à l'utilisateur une erreur de validation.  Les modèles de contrôle sont utilisés pour redéfinir l'apparence d'un contrôle.  
  
 [!code-xml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 Comme indiqué dans l'exemple suivant, l'<xref:System.Windows.Controls.ToolTip> qui affiche le message d'erreur est créée à l'aide du style `textBoxInError`.  Si la valeur de <xref:System.Windows.Controls.Validation.HasError%2A> est `true`, le déclencheur affecte à l'info\-bulle de la <xref:System.Windows.Controls.TextBox> actuelle sa première erreur de validation.  La <xref:System.Windows.Data.Binding.RelativeSource%2A> a la valeur <xref:System.Windows.Data.RelativeSourceMode> en faisant référence à l'élément actuel.  
  
 [!code-xml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 Pour obtenir l'exemple complet, consultez [Validation de liaison, exemple](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
 Notez que si vous ne fournissez pas un <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> personnalisé, le modèle d'erreur par défaut apparaît pour fournir la rétroaction visuelle à l'utilisateur lorsqu'il existe une erreur de validation.  Consultez la rubrique « Validation des données » dans [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md) pour plus d'informations.  En outre, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une règle de validation intégrée qui intercepte les exceptions levées pendant la mise à jour de la propriété de source de liaison.  Pour plus d'informations, consultez <xref:System.Windows.Controls.ExceptionValidationRule>.  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)