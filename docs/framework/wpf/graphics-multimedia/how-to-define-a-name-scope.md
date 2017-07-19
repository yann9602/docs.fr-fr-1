---
title: "Comment&#160;: d&#233;finir une port&#233;e de nom | Microsoft Docs"
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
  - "animation, Animations, en code procédural"
  - "portée de nom, définition"
  - "Animations, animer en code procédural"
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: d&#233;finir une port&#233;e de nom
Pour animer avec <xref:System.Windows.Media.Animation.Storyboard> dans du code, vous devez créer un <xref:System.Windows.NameScope> et enregistrer les noms des objets cibles avec l'élément qui possède cette portée de nom.  Dans l'exemple suivant, un <xref:System.Windows.NameScope> est créé pour `myMainPanel`.  Deux boutons, `button1` et `button2`, sont ajoutés au panneau, et leurs noms sont enregistrés.  Plusieurs animations et un <xref:System.Windows.Media.Animation.Storyboard> sont créés.  La méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de la table de montage séquentiel est utilisée pour démarrer les animations.  
  
 Comme `button1`, `button2` et `myMainPanel` partagent tous les trois la même portée de nom, n'importe lequel d'entre eux peut être utilisé avec la méthode <xref:System.Windows.Media.Animation.Storyboard><xref:System.Windows.Media.Animation.Storyboard.Begin%2A> pour démarrer les animations.  
  
## Exemple  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## Voir aussi  
 [Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)