---
title: Dessin du texte mis en forme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1d85e85079504e28a5b0ae78dc8be3a4b928ea3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="drawing-formatted-text"></a>Dessin du texte mis en forme
Cette rubrique fournit une vue d’ensemble des fonctionnalités de la <xref:System.Windows.Media.FormattedText> objet. Cet objet offre un contrôle de bas niveau pour le dessin de texte dans des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 Le <xref:System.Windows.Media.FormattedText> objet vous permet de dessiner du texte multiligne, dans lequel chaque caractère dans le texte peut être mis en forme individuellement. L’exemple suivant montre un texte auquel plusieurs formats sont appliqués.  
  
 ![Texte affiché à l’aide de l’objet FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Texte affiché à l’aide de la méthode FormattedText  
  
> [!NOTE]
>  Pour les développeurs qui migrent depuis l’API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau présenté dans la section [Migration depuis Win32](#win32_migration) répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Raisons d’utiliser du texte mis en forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l’écran. Chaque contrôle cible un scénario différent et dispose de sa propre liste de fonctionnalités et limitations. En général, les <xref:System.Windows.Controls.TextBlock> élément doit être utilisé lors de la prise en charge limitée de texte est requis, par exemple, une brève phrase dans un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>peut être utilisé lors de la prise en charge de texte minimale est requise. Pour plus d’informations, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 Le <xref:System.Windows.Media.FormattedText> objet fournit des fonctionnalités que la mise en forme de texte supérieur [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contrôles de texte et peut être utile dans les cas où vous souhaitez utiliser le texte comme élément décoratif. Pour plus d’informations, consultez la section suivante, [Conversion du texte mis en forme en géométrie](#converting_formatted_text).  
  
 En outre, le <xref:System.Windows.Media.FormattedText> objet est utile pour créer orienté texte <xref:System.Windows.Media.DrawingVisual>-objets dérivés. <xref:System.Windows.Media.DrawingVisual>est une classe de dessin légère qui permet de restituer des formes, des images ou texte. Pour plus d’informations, consultez [Test de positionnement à l’aide de DrawingVisuals, exemple](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Utilisation de l’objet FormattedText  
 Pour créer le texte mis en forme, appelez le <xref:System.Windows.Media.FormattedText.%23ctor%2A> constructeur pour créer un <xref:System.Windows.Media.FormattedText> objet. Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer différents styles de mise en forme.  
  
 Utilisez le <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> propriété pour limiter le texte à une largeur spécifique. Le texte est alors automatiquement renvoyé à la ligne pour éviter de dépasser la largeur spécifiée. Utilisez le <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> propriété pour limiter le texte à une hauteur spécifique. Le texte affiche des points de suspension (...) en lieu et place du texte qui dépasse la hauteur spécifiée.  
  
 ![Texte affiché à l’aide de l’objet FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Texte affiché présentant des retours à la ligne et des points de suspension  
  
 Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères. Par exemple, vous pouvez appeler à la fois le <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> méthodes pour modifier la mise en forme des cinq premiers caractères dans le texte.  
  
 L’exemple de code suivant crée un <xref:System.Windows.Media.FormattedText> de l’objet et applique ensuite plusieurs styles de mise en forme du texte.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unité de mesure de la taille de police  
 Comme avec d’autres objets de texte dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications, le <xref:System.Windows.Media.FormattedText> objet utilise des pixels indépendants du périphérique comme unité de mesure. Toutefois, la plupart des applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] utilisent des points comme unité de mesure. Si vous souhaitez afficher le texte en unités de points dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vous devez convertir [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] en points. L’exemple de code suivant montre comment effectuer cette conversion.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Conversion du texte mis en forme en géométrie  
 Vous pouvez convertir le texte mis en forme dans <xref:System.Windows.Media.Geometry> objets, ce qui vous permet de créer d’autres types de texte visuellement intéressant. Par exemple, vous pouvez créer un <xref:System.Windows.Media.Geometry> objet basé sur le contour d’une chaîne de texte.  
  
 ![Contour du texte à l’aide d’un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Contour du texte utilisant un pinceau de dégradé linéaire  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Exemple de définition du trait et du remplissage de différentes couleurs  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Exemple de pinceau image appliqué au trait  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Exemple de pinceau image appliqué au trait et surbrillance  
  
 Lorsque le texte est converti en un <xref:System.Windows.Media.Geometry> de l’objet, il n’est plus une collection de caractères, vous ne pouvez pas modifier les caractères dans la chaîne de texte. Vous pouvez néanmoins modifier l’apparence du texte converti en changeant ses propriétés de trait et de remplissage. Le trait fait référence au contour du texte converti et le remplissage à la zone située à l’intérieur du contour du texte converti. Pour plus d’informations, consultez [Créer du texte avec contour](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Vous pouvez également convertir le texte mis en forme à un <xref:System.Windows.Media.PathGeometry> de l’objet et utiliser l’objet pour mettre en surbrillance le texte. Par exemple, vous pouvez appliquer une animation à le <xref:System.Windows.Media.PathGeometry> afin qu’elle suive le plan du texte mis en forme de l’objet.  
  
 L’exemple suivant montre le texte mis en forme qui a été convertie en un <xref:System.Windows.Media.PathGeometry> objet. Une ellipse animée suit le tracé des traits du texte rendu.  
  
 ![Sphère suivant la géométrie de tracé du texte](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Sphère suivant la géométrie de tracé du texte  
  
 Pour plus d’informations, consultez [Guide pratique pour créer une animation PathGeometry pour du texte](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Vous pouvez créer les autres utilisations intéressantes pour le texte mis en forme une fois qu’il a été converti en un <xref:System.Windows.Media.PathGeometry> objet. Par exemple, vous pouvez y insérer une vidéo.  
  
 ![Vidéo s’affichant dans la géométrie de tracé du texte](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Vidéo s’affichant dans la géométrie de tracé du texte  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migration depuis Win32  
 Les fonctionnalités de <xref:System.Windows.Media.FormattedText> pour dessiner le texte sont semblables aux fonctionnalités de la [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] fonction DrawText. Pour les développeurs qui migrent depuis l’API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau suivant répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Indicateur DrawText|Équivalent WPF|Notes|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une propriété [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' position.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.Height%2A> et <xref:System.Windows.Media.FormattedText.Width%2A> propriétés pour calculer le rectangle de sortie.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur est définie sur <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Aucun.|Non requis La largeur de l’espace et le rendu de la dernière ligne sont les mêmes que dans le contrôle d’édition du framework.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Utilisez <xref:System.Windows.TextTrimming.WordEllipsis> pour obtenir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS avec DT_WORD_ELIPSIS fin : dans ce cas, les points de suspension caractère se produit uniquement sur les mots qui ne tiennent pas sur une seule ligne.|  
|DT_EXPAND_TABS|Aucun.|Non requis Des tabulations sont créées automatiquement avec des taquets tous les 4 cadratins, ce qui correspond plus ou moins à la largeur de 8 caractères indépendants du langage.|  
|DT_EXTERNALLEADING|Aucun.|Non requis L’espacement externe est toujours inclus dans l’interligne. Utilisez le <xref:System.Windows.Media.FormattedText.LineHeight%2A> propriété à créer l’interligne défini par l’utilisateur.|  
|DT_HIDEPREFIX|Aucun.|Non pris en charge. Supprimez le '&' à partir de la chaîne avant de construire le <xref:System.Windows.Media.FormattedText> objet.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Il s’agit de l’alignement de texte par défaut. Utilisez le <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur est définie sur <xref:System.Windows.TextAlignment.Left>. (WPF uniquement)|  
|DT_MODIFYSTRING|Aucun.|Non pris en charge.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Le découpage n’est pas effectué automatiquement. Si vous souhaitez découper le texte, utilisez le <xref:System.Windows.Media.Visual.VisualClip%2A> propriété.|  
|DT_NOFULLWIDTHCHARBREAK|Aucun.|Non pris en charge.|  
|DT_NOPREFIX|Aucun.|Non requis Le caractère '&' présent dans les chaînes est toujours traité comme un caractère normal.|  
|DT_PATHELLIPSIS|Aucun.|Utilisez le <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Aucun.|Non pris en charge. Si vous souhaitez utiliser des traits de soulignement pour le texte, tels qu’une touche d’accès ou un lien, utilisez la <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> (méthode).|  
|DT_PREFIXONLY|Aucun.|Non pris en charge.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriété avec la valeur est définie sur <xref:System.Windows.TextAlignment.Right>. (WPF uniquement)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Affectez à la propriété <xref:System.Windows.Media.FormattedText.FlowDirection%2A> la valeur <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Aucun.|Non requis <xref:System.Windows.Media.FormattedText>les objets se comportent comme un contrôle à ligne unique, à moins que soit le <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> propriété est définie ou le texte contient un chariot / saut de ligne (CR/LF).|  
|DT_TABSTOP|Aucun.|Les positions des taquets de tabulation définies par l’utilisateur ne sont pas prises en charge.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non requis La justification en haut est la valeur par défaut. Autres valeurs de positionnement vertical peuvent être définies à l’aide de la <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une propriété [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' position.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une propriété [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' position.|  
|DT_WORDBREAK|Aucun.|Non requis Analyse lexicale s’effectue automatiquement avec <xref:System.Windows.Media.FormattedText> objets. Vous ne pouvez pas la désactiver.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez le <xref:System.Windows.Media.FormattedText.Trimming%2A> propriété avec la valeur <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.FormattedText>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Créer du texte avec contour](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Guide pratique pour créer une animation PathGeometry pour du texte](http://msdn.microsoft.com/en-us/29f8051e-798a-463f-a926-a099a99e9c67)
