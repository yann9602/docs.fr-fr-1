---
title: "Comment : créer du texte avec une ombre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b031b0dce8e1fd06399ded0b6d612a23323ae837
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a>Comment : créer du texte avec une ombre
Les exemples de cette section indiquent comment créer un effet d’ombre pour du texte affiché.  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Windows.Media.Effects.DropShadowEffect> objet vous permet de créer plusieurs types de suppression pour les effets d’ombre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objets. L’exemple suivant présente un effet d’ombre portée appliqué au texte. Dans ce cas, l’ombre est une ombre légère, ce qui signifie que sa couleur devient floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Exemple de texte avec une ombre légère  
  
 Vous pouvez contrôler la largeur de l’ombre en définissant le <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriété. La valeur `4.0` indique une largeur de l’ombre de 4 pixels. Vous pouvez contrôler la douceur, ou flou d’une ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriété. La valeur `0.0` indique aucun flou. L’exemple de code suivant montre comment créer une ombre légère.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  Ces effets d’ombre ne traversent pas la [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pipeline de rendu de texte. En conséquence, ClearType est désactivé lors de l’utilisation de ces effets.  
  
 L’exemple suivant présente un effet d’ombre portée marquée appliqué au texte. Dans ce cas, l’ombre n’est pas floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")  
Exemple de texte avec une ombre marquée  
  
 Vous pouvez créer une ombre foncée en définissant le <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriété `0.0`, ce qui indique qu’aucun flou est utilisé. Vous pouvez contrôler la direction de l’ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriété. Définissez la valeur directionnelle de cette propriété à un degré entre `0` et `360`. L’illustration suivante montre les valeurs de direction du <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> paramètre de propriété.  
  
 ![Degré DropShadow de l’ombre](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
Diagramme de direction DropShadow  
  
 L’exemple de code suivant montre comment créer une ombre marquée.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Utilisation d’un effet de flou  
 Un <xref:System.Windows.Media.Effects.BlurBitmapEffect> peut être utilisé pour créer un effet de clichés instantanés qui peut être placé derrière un objet texte. Un effet bitmap flou appliqué au texte rend le texte flou uniformément dans toutes les directions.  
  
 L’exemple suivant présente un effet de flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Exemple de texte avec un effet de flou  
  
 L’exemple de code suivant montre comment créer un effet de flou.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Utilisation d’une transformation de traduction  
 Un <xref:System.Windows.Media.TranslateTransform> peut être utilisé pour créer un effet de clichés instantanés qui peut être placé derrière un objet texte.  
  
 Le code suivant exemple utilise un <xref:System.Windows.Media.TranslateTransform> pour décaler le texte. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 ![Ombre du texte utilisant TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")  
Exemple de texte utilisant une transformation pour un effet d’ombre  
  
 L’exemple de code suivant indique comment créer une transformation pour un effet d’ombre.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
