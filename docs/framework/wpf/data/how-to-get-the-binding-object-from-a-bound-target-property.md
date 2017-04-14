---
title: "Comment&#160;: obtenir l&#39;objet de liaison d&#39;une propri&#233;t&#233; cible li&#233;e aux donn&#233;es | Microsoft Docs"
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
  - "liaison de données, obtenir des objets de liaison à partir de propriétés cibles liées"
  - "propriétés, obtenir des objets de liaison à partir de"
ms.assetid: 87974c5f-136b-4de7-b07d-9285b62ab123
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: obtenir l&#39;objet de liaison d&#39;une propri&#233;t&#233; cible li&#233;e aux donn&#233;es
Cet exemple montre comment obtenir l'objet de liaison d'une propriété cible liée aux données.  
  
## Exemple  
 Vous pouvez obtenir l'objet <xref:System.Windows.Data.Binding> en effectuant la procédure suivante :  
  
 [!code-csharp[BindValidation#GetBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml.cs#getbinding)]  
  
> [!NOTE]
>  Vous devez spécifier la [propriété de dépendance](GTMT) pour la liaison que vous voulez car il est possible que plusieurs propriétés de l'objet cible utilisent la liaison des données.  
  
 Vous pouvez également obtenir <xref:System.Windows.Data.BindingExpression>, puis la valeur de la propriété <xref:System.Windows.Data.BindingExpression.ParentBinding%2A>.  
  
 Pour obtenir l'exemple complet, consultez [Validation de liaison, exemple](http://go.microsoft.com/fwlink/?LinkID=159972).  
  
> [!NOTE]
>  Si votre liaison est <xref:System.Windows.Data.MultiBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetMultiBinding%2A>.  S'il s'agit de <xref:System.Windows.Data.PriorityBinding>, utilisez <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetPriorityBinding%2A>.  Si vous ne pouvez pas déterminer avec certitude si la propriété cible est liée à l'aide de <xref:System.Windows.Data.Binding>, de <xref:System.Windows.Data.MultiBinding> ou de <xref:System.Windows.Data.PriorityBinding>, vous pouvez utiliser <xref:System.Windows.Data.BindingOperations>.<xref:System.Windows.Data.BindingOperations.GetBindingBase%2A>.  
  
## Voir aussi  
 [Créer une liaison dans du code](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)