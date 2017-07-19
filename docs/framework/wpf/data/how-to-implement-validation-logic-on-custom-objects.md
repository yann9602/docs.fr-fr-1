---
title: "Comment&#160;: impl&#233;menter une logique de validation sur des objets personnalis&#233;s | Microsoft Docs"
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
  - "rechercher les erreurs de validation (WPF)"
  - "objets personnalisés (WPF), implémenter une logique de validation sur"
  - "implémenter une logique de validation sur des objets personnalisés (WPF)"
  - "erreurs de validation (WPF), rechercher"
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: impl&#233;menter une logique de validation sur des objets personnalis&#233;s
Cet exemple montre comment implémenter une logique de validation sur un objet personnalisé, puis créer une liaison avec lui.  
  
## Exemple  
 Vous pouvez fournir une logique de validation sur la couche métier si votre objet source implémente <xref:System.ComponentModel.IDataErrorInfo>, comme dans l'exemple suivant :  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 Dans l'exemple suivant, la propriété Texte de la zone de texte crée une liaison avec la propriété `Age` de l'objet `Person`, dont on a fait en sorte qu'il soit disponible pour une liaison via une déclaration de ressource qui reçoit le `x:Key``data`.  <xref:System.Windows.Controls.DataErrorValidationRule> recherche les erreurs de validation déclenchées par l'implémentation <xref:System.ComponentModel.IDataErrorInfo>.  
  
 [!code-xml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 Au lieu d'utiliser le <xref:System.Windows.Controls.DataErrorValidationRule>, vous pouvez affecter à la propriété <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> la valeur `true`.  
  
## Voir aussi  
 <xref:System.Windows.Controls.ExceptionValidationRule>   
 [Implémenter la validation de la liaison](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)