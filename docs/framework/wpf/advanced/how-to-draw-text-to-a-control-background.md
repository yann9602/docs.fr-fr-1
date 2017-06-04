---
title: "Comment&#160;: dessiner du texte sur l&#39;arri&#232;re-plan d&#39;un contr&#244;le | Microsoft Docs"
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
  - "arrière-plans, dessiner du texte dans"
  - "contrôles, dessiner du texte sur les arrière-plans"
  - "dessiner, texte sur les arrière-plans de contrôles"
  - "texte, dessiner sur les arrière-plans de contrôles"
  - "typographie, dessiner du texte sur les arrière-plans de contrôles"
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: dessiner du texte sur l&#39;arri&#232;re-plan d&#39;un contr&#244;le
Vous pouvez attirer directement le texte à l'arrière\-plan d'un contrôle en convertissant une chaîne de texte en objet <xref:System.Windows.Media.FormattedText>, et attirer ensuite l'objet au <xref:System.Windows.Media.DrawingContext> du contrôle.  Vous pouvez également utiliser cette technique pour attirer à l'arrière\-plan d'objets dérivés de <xref:System.Windows.Controls.Panel>, tels que <xref:System.Windows.Controls.Canvas> et <xref:System.Windows.Controls.StackPanel>.  
  
 ![Contrôles affichant le texte en arrière&#45;plan](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Exemple de contrôles avec les arrière\-plan de texte personnalisés  
  
## Exemple  
 Pour attirer à l'arrière\-plan d'un contrôle, créez un objet <xref:System.Windows.Media.DrawingBrush> et attirez le texte converti sur le <xref:System.Windows.Media.DrawingContext>de l'objet.  Puis, assignez le nouveau <xref:System.Windows.Media.DrawingBrush> à la propriété d'arrière\-plan du contrôle.  
  
 L'exemple de code suivant montre comment créer un objet <xref:System.Windows.Media.FormattedText> et attirer à l'arrière\-plan d'un objet <xref:System.Windows.Controls.Label> et <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## Voir aussi  
 <xref:System.Windows.Media.FormattedText>   
 [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)