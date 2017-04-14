---
title: "Comment&#160;: cr&#233;er du texte avec contour | Microsoft Docs"
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
  - "pinceau dégradé"
  - "pinceau dégradé linéaire"
  - "texte avec contour"
  - "typographie, pinceau dégradé linéaire"
  - "typographie, effets de contour"
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er du texte avec contour
Dans la plupart des cas, lorsque vous ajoutez l'ornementation aux chaînes de texte dans votre application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vous utilisez le texte en terme de collection de caractères discrets, ou glyphes.  Par exemple, vous pourriez créer un pinceau à dégradé linéaire et l'appliquer à la propriété <xref:System.Windows.Controls.Control.Foreground%2A> d'un objet <xref:System.Windows.Controls.TextBox>.  Lorsque vous affichez ou modifiez la zone de texte, le pinceau à dégradé linéaire est appliqué automatiquement au jeu actuel de caractères dans la chaîne de texte.  
  
 ![Texte affiché avec un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext01.png "OutlinedText01")  
Exemple d'un pinceau à dégradé linéaire appliqué à une zone de texte  
  
 Cependant, vous pouvez également convertir le texte en objets <xref:System.Windows.Media.Geometry>, ce qui vous permet de créer d'autres types de texte visuellement enrichi.  Par exemple, vous pouvez créer un objet <xref:System.Windows.Media.Geometry> basé sur le contour d'une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
Exemple d'un pinceau à dégradé linéaire appliqué à la géométrie de plan de texte  
  
 Lorsque le texte est converti en objet <xref:System.Windows.Media.Geometry>, il ne constitue plus une collection de caractères — autrement dit, vous ne pouvez pas modifier les caractères dans la chaîne de texte.  Vous pouvez néanmoins modifier l'apparence du texte converti en changeant ses propriétés de trait et de remplissage.  Le trait fait référence au plan du texte converti et le remplissage à la zone située à l'intérieur du plan du texte converti.  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels en modifiant le trait et le remplissage du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
Exemple de définition du trait et du remplissage de différentes couleurs  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
Exemple de pinceau image appliqué au trait  
  
 Il est également possible de modifier le rectangle de zone englobante, ou surbrillance, du texte converti.  L'exemple suivant illustre une manière de créer des effets visuels en modifiant le trait et la surbrillance du texte converti.  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
Exemple de pinceau image appliqué au trait et surbrillance  
  
## Exemple  
 La clé pour convertir du texte en un objet <xref:System.Windows.Media.Geometry> est d'utiliser l'objet <xref:System.Windows.Media.FormattedText>.  Une fois que vous avez créé cet objet, vous pouvez utiliser les méthodes <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> et <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> pour convertir le texte en objets <xref:System.Windows.Media.Geometry>.  La première méthode retourne la géométrie du texte mis en forme; la deuxième méthode retourne la géométrie de la zone englobante du texte mis en forme.  Le code suivant montre comment créer un objet <xref:System.Windows.Media.FormattedText> et récupérer les géométries du texte mis en forme et son cadre englobant.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Pour afficher les objets <xref:System.Windows.Media.Geometry> récupérés, vous devez accéder au <xref:System.Windows.Media.DrawingContext> de l'objet qui affiche le texte converti.  Dans ces exemples de code, cela est fait en créant un objet de contrôle personnalisé dérivé d'une classe qui prend en charge le rendu défini par l'utilisateur.  
  
 Pour afficher des objets <xref:System.Windows.Media.Geometry> dans le contrôle personnalisé, fournissez une substitution pour la méthode <xref:System.Windows.UIElement.OnRender%2A>.  Votre méthode de substitution doit utiliser la méthode <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> pour dessiner les objets <xref:System.Windows.Media.Geometry>.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## Voir aussi  
 [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)