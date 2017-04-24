---
title: "Dessin du texte mis en forme | Microsoft Docs"
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
  - "dessiner, texte mis en forme"
  - "texte mis en forme (WPF)"
  - "texte (WPF)"
  - "typographie, dessiner du texte mis en forme"
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Dessin du texte mis en forme
Cette rubrique fournit une vue d'ensemble des fonctionnalités de l'objet <xref:System.Windows.Media.FormattedText>.  Cet objet offre un contrôle de bas niveau pour le dessin de texte dans des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
   
  
<a name="technology_overview"></a>   
## Vue d'ensemble de la technologie  
 L'objet <xref:System.Windows.Media.FormattedText> vous permet de dessiner du texte multiligne, dans lequel chaque caractère du texte peut être mis en forme individuellement.  L'exemple suivant montre un texte auquel plusieurs formats sont appliqués.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.png "FormattedText01")  
Texte affiché à l'aide de la méthode FormattedText  
  
> [!NOTE]
>  Pour les développeurs qui migrent depuis l'API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau présenté dans la section [Migration depuis Win32](#win32_migration) répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### Raisons pour lesquelles utiliser le texte mis en forme  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l'écran.  Chaque contrôle est ciblé sur un scénario différent et dispose de sa propre liste de fonctionnalités et limitations.  En général, l'élément <xref:System.Windows.Controls.TextBlock> doit être utilisé lorsqu'une prise en charge de texte limitée est requise, par exemple pour une courte phrase dans une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  <xref:System.Windows.Controls.Label> peut être utilisé lorsqu'une prise en charge de texte minimale est requise.  Pour plus d'informations, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 L'objet <xref:System.Windows.Media.FormattedText> fournit des fonctionnalités de mise en forme du texte supérieures aux contrôles de texte [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], et peut être utile si vous souhaitez utiliser du texte comme élément décoratif. Pour plus d'informations, consultez la section suivante [Conversion du texte mis en forme en géométrie](#converting_formatted_text).  
  
 De plus, l'objet <xref:System.Windows.Media.FormattedText> est utile pour créer des objets dérivés de <xref:System.Windows.Media.DrawingVisual> et orientés texte.  <xref:System.Windows.Media.DrawingVisual> est une classe de dessin légère qui permet de restituer des formes, des images ou du texte.  Pour plus d'informations, consultez [Test de positionnement à l'aide de DrawingVisuals, exemple](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="using_the_formattedtext_object"></a>   
## Utilisation de l'objet FormattedText  
 Pour créer le texte mis en forme, appelez le constructeur <xref:System.Windows.Media.FormattedText.%23ctor%2A> pour créer un objet <xref:System.Windows.Media.FormattedText>.  Une fois que vous avez créé la chaîne initiale de texte mis en forme, vous pouvez appliquer un éventail de mises en forme de styles.  
  
 Utilisez la propriété <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> pour limiter le texte à une largeur spécifique.  Le texte est alors automatiquement renvoyé à la ligne pour éviter de dépasser la largeur spécifiée.  Utilisez la propriété <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> pour limiter le texte à une hauteur spécifique.  Le texte affiche des points de suspension, "...", en lieu et place du texte qui dépasse la hauteur spécifiée.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Texte affiché présentant des retours à la ligne et des points de suspension  
  
 Vous pouvez appliquer plusieurs styles de mise en forme à un ou plusieurs caractères.  Par exemple, vous pouvez appeler simultanément les méthodes <xref:System.Windows.Media.FormattedText.SetFontSize%2A> et <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> pour modifier la mise en forme des cinq premiers caractères du texte.  
  
 L'exemple de code suivant crée un objet <xref:System.Windows.Media.FormattedText> et applique ensuite plusieurs styles de mise en forme au texte.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### Unité de mesure de la taille de police  
 De même que pour d'autres objets de texte des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], l'objet <xref:System.Windows.Media.FormattedText> utilise des pixels indépendants du périphérique comme unité de mesure.  La plupart des applications [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] utilisent toutefois des points comme unité de mesure.  Si vous souhaitez afficher le texte en unités de points dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], vous devez convertir les [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] en points.  L'exemple de code suivant vous montre comment effectuer cette conversion.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### Conversion du texte mis en forme en géométrie  
 Vous pouvez convertir le texte mis en forme en objets <xref:System.Windows.Media.Geometry>, ce qui vous permet de créer d'autres types de texte présentant un intérêt visuel.  Par exemple, vous pouvez créer un objet <xref:System.Windows.Media.Geometry> basé sur le contour d'une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
Contour du texte à l'aide d'un pinceau à dégradé linéaire  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
Exemple de définition du trait et du remplissage de différentes couleurs  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
Exemple de pinceau image appliqué au trait  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
Exemple de pinceau image appliqué au trait et surbrillance  
  
 Lorsque le texte est converti en objet <xref:System.Windows.Media.Geometry>, il ne constitue plus une collection de caractères — autrement dit, vous ne pouvez pas modifier les caractères dans la chaîne de texte.  Vous pouvez néanmoins modifier l'apparence du texte converti en changeant ses propriétés de trait et de remplissage.  Le trait fait référence au plan du texte converti et le remplissage à la zone située à l'intérieur du plan du texte converti.  Pour plus d'informations, consultez [Créer du texte avec contour](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Vous pouvez également convertir le texte mis en forme en objet <xref:System.Windows.Media.PathGeometry> et utiliser celui\-ci pour mettre le texte en surbrillance.  Par exemple, vous pouvez appliquer une animation à l'objet <xref:System.Windows.Media.PathGeometry> afin qu'elle suive le plan du texte mis en forme.  
  
 L'exemple suivant montre le texte mis en forme qui a été converti en objet <xref:System.Windows.Media.PathGeometry>.  Une ellipse animée suit le tracé des traits du texte rendu.  
  
 ![Sphère suivant la géométrie de tracé du texte](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.png "TextPathGeometry01")  
Sphère suivant la géométrie de tracé du texte  
  
 Pour plus d'informations, consultez [How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/fr-fr/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Vous pouvez créer d'autres utilisations intéressantes pour le texte mis en forme une fois qu'il a été converti en objet <xref:System.Windows.Media.PathGeometry>.  Par exemple, vous pouvez y insérer une vidéo.  
  
 ![Vidéo s'affichant dans la géométrie de tracé du texte](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Vidéo s'affichant dans la géométrie de tracé du texte  
  
<a name="win32_migration"></a>   
## Migration depuis Win32  
 Les fonctionnalités de <xref:System.Windows.Media.FormattedText> utilisées pour dessiner le texte sont similaires à celles de la fonction DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)].  Pour les développeurs qui migrent depuis l'API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], le tableau suivant répertorie les indicateurs DrawText de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et leur équivalent approximatif dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Indicateur DrawText|Équivalent WPF|Remarques|  
|-------------------------|--------------------|---------------|  
|DT\_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position "y" appropriée de DrawText dans [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)].|  
|DT\_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Utilisez les propriétés <xref:System.Windows.Media.FormattedText.Height%2A> et <xref:System.Windows.Media.FormattedText.Width%2A> pour calculer le rectangle de sortie.|  
|DT\_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur définie à <xref:System.Windows.TextAlignment>.|  
|DT\_EDITCONTROL|Aucun|Non requise.  La largeur de l'espace et le rendu de la dernière ligne sont les mêmes que dans le contrôle d'édition de l'infrastructure.|  
|DT\_END\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming>.<br /><br /> Utilisez <xref:System.Windows.TextTrimming> pour obtenir DT\_END\_ELLIPSIS [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] avec l'ellipse de fin DT\_WORD\_ELIPSIS. Dans ce cas, des caractères ne sont remplacés par des points de suspension que dans les mots qui ne tiennent pas sur une ligne unique.|  
|DT\_EXPAND\_TABS|Aucun|Non requise.  Des tabulations sont créées automatiquement avec des taquets tous les 4 cadratins, ce qui correspond plus ou moins à la largeur de 8 caractères indépendamment de la langue.|  
|DT\_EXTERNALLEADING|Aucun|Non requise.  L'espacement externe est toujours inclus dans l'interligne.  Utilisez la propriété <xref:System.Windows.Media.FormattedText.LineHeight%2A> pour créer une interligne définie par l'utilisateur.|  
|DT\_HIDEPREFIX|Aucun|Non pris en charge.  Supprimez le '&' de la chaîne avant de construire l'objet <xref:System.Windows.Media.FormattedText>.|  
|DT\_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Il s'agit de l'alignement de texte par défaut.  Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur <xref:System.Windows.TextAlignment>.  \(WPF uniquement\)|  
|DT\_MODIFYSTRING|Aucun|Non pris en charge.|  
|DT\_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Le découpage n'est pas effectué automatiquement.  Si vous souhaitez découper le texte, utilisez la propriété <xref:System.Windows.Media.Visual.VisualClip%2A>.|  
|DT\_NOFULLWIDTHCHARBREAK|Aucun|Non pris en charge.|  
|DT\_NOPREFIX|Aucun|Non requise.  Le caractère '&' présent dans les chaînes est toujours traité comme un caractère normal.|  
|DT\_PATHELLIPSIS|Aucun|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming>.|  
|DT\_PREFIX|Aucun|Non pris en charge.  Si vous souhaitez utiliser des traits de soulignement pour du texte, tel qu'une touche d'accès rapide ou une liaison, utilisez la méthode <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>.|  
|DT\_PREFIXONLY|Aucun|Non pris en charge.|  
|DT\_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.TextAlignment%2A> avec la valeur <xref:System.Windows.TextAlignment>.  \(WPF uniquement\)|  
|DT\_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Affectez à la propriété <xref:System.Windows.Media.FormattedText.FlowDirection%2A> la valeur <xref:System.Windows.FlowDirection>.|  
|DT\_SINGLELINE|Aucun|Non requise.  Les objets <xref:System.Windows.Media.FormattedText> se comportent comme un contrôle de ligne unique, sauf si la propriété <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> est définie ou si le texte contient un retour chariot\/saut de ligne.|  
|DT\_TABSTOP|Aucun|Les positions des taquets de tabulation définies par l'utilisateur ne sont pas prises en charge.|  
|DT\_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Non requise.  La justification en haut est la valeur par défaut.  D'autres valeurs de positionnement vertical peuvent être définies à l'aide de la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position "y" appropriée de DrawText dans [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)].|  
|DT\_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Height%2A> pour calculer une position "y" appropriée de DrawText dans [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)].|  
|DT\_WORDBREAK|Aucun|Non requise.  La césure des mots se fait automatiquement avec les objets <xref:System.Windows.Media.FormattedText>.  Vous ne pouvez pas la désactiver.|  
|DT\_WORD\_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Utilisez la propriété <xref:System.Windows.Media.FormattedText.Trimming%2A> avec la valeur <xref:System.Windows.TextTrimming>.|  
  
## Voir aussi  
 <xref:System.Windows.Media.FormattedText>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [Créer du texte avec contour](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)   
 [How to: Create a PathGeometry Animation for Text](http://msdn.microsoft.com/fr-fr/29f8051e-798a-463f-a926-a099a99e9c67)