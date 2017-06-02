---
title: "Comment&#160;: cr&#233;er du texte avec une ombre | Microsoft Docs"
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
  - "effets d'ombre dans du texte"
  - "texte, masqué"
  - "typographie, effets d'ombre"
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er du texte avec une ombre
Les exemples de cette section indiquent comment créer un effet d'ombre pour du texte affiché.  
  
## Exemple  
 L'objet <xref:System.Windows.Media.Effects.DropShadowEffect> vous permet de créer divers effets d'ombre portée pour les objets [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  L'exemple suivant présente un effet d'ombre portée appliqué au texte.  Dans ce cas, l'ombre est une ombre légère, ce qui signifie que la couleur ombrée devient floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.png "ShadowText01")  
Exemple de texte avec une ombre légère  
  
 Vous pouvez contrôler la largeur d'une ombre en définissant la propriété <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A>.  Une valeur de `4.0` indique une largeur d'ombre de 4 pixels.  Vous pouvez contrôler la douceur, ou flou d'une ombre en modifiant la propriété <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A>.  Une valeur de `0.0` n'indique aucun flou.  L'exemple de code suivant montre comment créer une ombre légère.  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Ces effets d'ombre ne traversent pas le pipeline de rendu de texte de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  En conséquence, ClearType est désactivé lors de l'utilisation de ces effets.  
  
 L'exemple suivant présente un effet d'ombre portée important appliqué au texte.  Dans ce cas, l'ombre n'est pas floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.png "ShadowText02")  
Exemple de texte avec une ombre foncée  
  
 Vous pouvez créer une ombre foncée en définissant la propriété <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> à `0.0`, ce qui indique qu'aucun flou n'est utilisé.  Vous pouvez contrôler la direction de l'ombre en modifiant la propriété <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>.  Définissez la valeur directionnelle de cette propriété à un degré entre `0` et `360`.  L'illustration suivante montre les valeurs de direction du paramètre de propriété <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A>.  
  
 ![Paramètre de degré DropShadow de l'ombre](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
Diagramme de direction DropShadow  
  
 L'exemple de code suivant montre comment créer une ombre foncée.  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## Utilisation d'un effet flou  
 Un <xref:System.Windows.Media.Effects.BlurBitmapEffect> peut être utilisé pour créer un effet similaire à une ombre pouvant être placé derrière une chaîne de texte.  Un effet bitmap flou appliqué au texte rend le texte flou uniformément dans toutes les directions.  
  
 L'exemple suivant présente un effet flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.png "ShadowText06")  
Exemple de texte avec un effet flou  
  
 L'exemple de code suivant montre comment créer un effet flou .  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## Utiliser une transformation de traduction  
 Une <xref:System.Windows.Media.TranslateTransform> peut être utilisée pour créer un effet similaire à l'ombre pouvant être placé derrière un objet de texte.  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.TranslateTransform> pour décaler le texte.   Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d'ombre.  
  
 ![Ombre du texte utilisant TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.png "ShadowText07")  
Exemple de texte utilisant une transformation pour un effet d'ombre  
  
 L'exemple de code suivant indique comment créer une transformation pour un effet d'ombre.  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]