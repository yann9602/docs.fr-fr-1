---
title: "Mappage de propriétés Windows Forms et WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0af1015747e2f27b19c2cac2c896dd60214264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mappage de propriétés Windows Forms et WPF
Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologies disposent de deux modèles de propriété semblables mais différents. *Mappage de propriété* prend en charge l’interopérabilité entre les deux architectures et fournit les fonctionnalités suivantes :  
  
-   Facilite le mappage des modifications de propriété dans l’environnement d’hôte à l’élément ou le contrôle hébergé.  
  
-   Fournit des propriétés de gestion par défaut pour le mappage le plus couramment utilisées.  
  
-   Autorise la suppression, substitution ou l’extension de propriétés par défaut.  
  
-   Garantit que les modifications de valeur de propriété sur l’ordinateur hôte sont automatiquement détectées et traduites à l’élément ou le contrôle hébergé.  
  
> [!NOTE]
>  Événements de modification de propriété ne sont pas propagées de l’hébergement du contrôle ou de la hiérarchie de l’élément. Traduction de la propriété n’est pas effectuée si la valeur locale d’une propriété n’est pas en raison de la définition directe, styles, l’héritage, la liaison de données ou autres mécanismes qui modifient la valeur de la propriété.  
  
 Utilisez le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriété sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément et la <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriété sur <xref:System.Windows.Forms.Integration.ElementHost> contrôle pour accéder au mappage de propriété.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mappage de propriété avec l’élément WindowsFormsHost  
 Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément traduit par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés à leurs [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] équivalents à l’aide de la table de traduction suivante.  
  
|Hébergement de Windows Presentation Foundation|Windows Forms|Comportement d’interopérabilité|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> ensembles d’éléments le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du contrôle hébergé et le <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété du contrôle hébergé. Le mappage est effectué en utilisant les règles suivantes :<br /><br /> -If <xref:System.Windows.Controls.Control.Background%2A> est une couleur unie, il est converti et utilisé pour définir le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du contrôle hébergé. Le <xref:System.Windows.Forms.Control.BackColor%2A> propriété n’est pas définie sur le contrôle hébergé, car le contrôle hébergé peut hériter de la valeur de la <xref:System.Windows.Forms.Control.BackColor%2A> propriété. **Remarque :** le contrôle hébergé ne prend pas en charge la transparence. Toute couleur assignée à <xref:System.Windows.Forms.Control.BackColor%2A> doit être entièrement opaque, avec une valeur alpha 0xFF. <br /><br /> -If <xref:System.Windows.Controls.Control.Background%2A> n’est pas une couleur unie, le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle crée une image bitmap à partir de la <xref:System.Windows.Controls.Control.Background%2A> propriété. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle affecte cette image bitmap à la <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété du contrôle hébergé. Cela fournit un effet similaire à la transparence. **Remarque :** vous pouvez substituer ce comportement, ou vous pouvez supprimer la <xref:System.Windows.Controls.Control.Background%2A> mappage de propriété.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Si le mappage par défaut n’a pas été réassigné, <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle parcourt sa hiérarchie ancêtre jusqu'à ce qu’il trouve un ancêtre avec son <xref:System.Windows.FrameworkElement.Cursor%2A> jeu de propriétés. Cette valeur est traduite correspondant le plus proche [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] curseur.<br /><br /> Si le mappage par défaut pour le <xref:System.Windows.FrameworkElement.ForceCursor%2A> propriété n’a pas été réassignée, le parcours s’arrête sur le premier ancêtre avec <xref:System.Windows.FrameworkElement.ForceCursor%2A> la valeur `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> correspond à <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> correspond à <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>n’est pas mappé.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> correspond à <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>sur le contrôle hébergé<xref:System.Drawing.Font?displayProperty=nameWithType>|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduite correspondante <xref:System.Drawing.Font>. Lorsqu’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Pour <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> est désactivé. Pour <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> est activé.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>sur le contrôle hébergé<xref:System.Drawing.Font?displayProperty=nameWithType>|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduite correspondante <xref:System.Drawing.Font>. Lorsqu’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Pour <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, ou <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> est activé. Pour <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, ou <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> est désactivé.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduite correspondante <xref:System.Drawing.Font>. Lorsqu’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est redimensionné en fonction de la taille de police.<br /><br /> Taille de police en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est exprimée sous la forme d’un quatre-vingt-seizième d’un pouce et dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] comme une seconde 70 de pouce. La conversion correspondante est :<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]la taille de police = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la taille de police * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Le <xref:System.Windows.Controls.Control.Foreground%2A> mappage de propriété est effectué en utilisant les règles suivantes :<br /><br /> -If <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.SolidColorBrush>, utilisez <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-If <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.GradientBrush>, la couleur de la <xref:System.Windows.Media.GradientStop> avec la valeur de décalage la plus basse pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Pour n’importe quel autre <xref:System.Windows.Media.Brush> de type, laissez <xref:System.Windows.Forms.Control.ForeColor%2A> inchangée. Cela signifie que la valeur par défaut est utilisée.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Lorsque <xref:System.Windows.UIElement.IsEnabled%2A> est défini, <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément définit le <xref:System.Windows.Forms.Control.Enabled%2A> propriété sur le contrôle hébergé.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Les quatre valeurs de la <xref:System.Windows.Forms.Control.Padding%2A> propriété hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle sont définis sur les mêmes <xref:System.Windows.Thickness> valeur.<br /><br /> -Les valeurs supérieures à <xref:System.Int32.MaxValue> ont la valeur <xref:System.Int32.MaxValue>.<br />-Les valeurs moins <xref:System.Int32.MinValue> ont la valeur <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>mappe à <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle est visible. Si vous affectez explicitement la <xref:System.Windows.Forms.Control.Visible%2A> propriété sur le contrôle hébergé `false` n’est pas recommandée.<br />-   <xref:System.Windows.Visibility.Collapsed>mappe à <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` ou `false`. Hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle n’est pas dessiné et sa zone est réduite.<br />-   <xref:System.Windows.Visibility.Hidden>: Hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle occupe l’espace dans la mise en page, mais n’est pas visible. Dans ce cas, le <xref:System.Windows.Forms.Control.Visible%2A> est définie sur `true`. Si vous affectez explicitement la <xref:System.Windows.Forms.Control.Visible%2A> propriété sur le contrôle hébergé `false` n’est pas recommandée.|  
  
 Propriétés jointes sur les éléments de conteneur sont entièrement pris en charge par le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément.  
  
 Pour plus d’informations, consultez [procédure pas à pas : mappage de propriétés à l’aide de le WindowsFormsHost élément](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Mises à jour des propriétés Parent  
 Modifications apportées à la plupart des propriétés parent entraînent des notifications pour le contrôle enfant hébergé. La liste suivante décrit les propriétés qui n’entraînent pas de notifications lorsque leurs valeurs changent.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Par exemple, si vous modifiez la valeur de la <xref:System.Windows.Controls.Control.Background%2A> propriété de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément, le <xref:System.Windows.Forms.Control.BackColor%2A> propriété du contrôle hébergé ne change pas.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mappage de propriété avec le contrôle ElementHost  
 Les propriétés suivantes fournissent la notification de modification intégrée. N’appelez pas la <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> méthode lorsque vous mappez ces propriétés :  
  
-   AutoSize  
  
-   Couleur d’arrière-plan  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Curseur  
  
-   Station d' accueil  
  
-   Activé  
  
-   Police  
  
-   Couleur de premier plan  
  
-   Emplacement  
  
-   Marge  
  
-   Padding  
  
-   Parent  
  
-   Region  
  
-   RightToLeft  
  
-   Taille  
  
-   TabIndex  
  
-   TabStop  
  
-   Texte  
  
-   Visible  
  
 Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle convertit par défaut [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriétés à leurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] équivalents à l’aide de la table de traduction suivante.  
  
 Pour plus d’informations, consultez [procédure pas à pas : mappage de propriétés à l’aide du contrôle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hébergement Windows Forms|Windows Presentation Foundation|Comportement d’interopérabilité|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|Définition de cette propriété force à repeindre avec un <xref:System.Windows.Media.ImageBrush>. Si le <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> est définie sur `false` (la valeur par défaut), cela <xref:System.Windows.Media.ImageBrush> est basé sur l’apparence de la <xref:System.Windows.Forms.Integration.ElementHost> contrôler, y compris son <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> propriétés et peinture attaché gestionnaires.<br /><br /> Si le <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> est définie sur `true`, le <xref:System.Windows.Media.ImageBrush> est basé sur l’apparence de la <xref:System.Windows.Forms.Integration.ElementHost> parent du contrôle, y compris du parent <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> des propriétés et peinture attaché gestionnaires.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|Cette propriété, le même comportement que celui indiqué pour le <xref:System.Windows.Forms.Control.BackColor%2A> mappage.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|Cette propriété, le même comportement que celui indiqué pour le <xref:System.Windows.Forms.Control.BackColor%2A> mappage.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] curseur standard est traduit correspondant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] curseur standard. Si le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] n’est pas un curseur standard, la valeur par défaut est affectée.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Lorsque <xref:System.Windows.Forms.Control.Enabled%2A> est défini, le <xref:System.Windows.Forms.Integration.ElementHost> jeux de contrôles le <xref:System.Windows.UIElement.IsEnabled%2A> propriété sur l’élément hébergé.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Le <xref:System.Windows.Forms.Control.Font%2A> valeur est convertie en un jeu correspondant de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés de police.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>sur l’élément hébergé|Si <xref:System.Drawing.Font.Bold%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Si <xref:System.Drawing.Font.Bold%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>sur l’élément hébergé|Si <xref:System.Drawing.Font.Italic%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Si <xref:System.Drawing.Font.Italic%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>sur l’élément hébergé|S’applique uniquement lorsque vous hébergez un <xref:System.Windows.Controls.TextBlock> contrôle.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>sur l’élément hébergé|S’applique uniquement lorsque vous hébergez un <xref:System.Windows.Controls.TextBlock> contrôle.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> correspond à <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> correspond à <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle définit le <xref:System.Windows.UIElement.Visibility%2A> propriété sur l’élément hébergé en utilisant les règles suivantes :<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`mappe à <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`mappe à <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Interopérabilité WPF et Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
