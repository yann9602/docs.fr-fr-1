---
title: "Mappage de propri&#233;t&#233;s Windows Forms et WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interopérabilité (WPF), Windows Forms"
  - "propriétés (mappage) (interopérabilité WPF)"
  - "Windows Forms (WPF), interopérabilité avec"
  - "Windows Forms, interopérabilité WPF"
  - "WindowsFormsHost (mappage des propriétés des éléments)"
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Mappage de propri&#233;t&#233;s Windows Forms et WPF
Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont deux modèles de propriété semblables mais différents.  Le *mappage de propriété* prend en charge l'interopérabilité entre les deux architectures et fournit les fonctionnalités suivantes.  
  
-   Simplifie le mappage des modifications de propriété dans l'environnement hôte au contrôle ou à l'élément hébergé.  
  
-   Fournit la gestion par défaut pour le mappage des propriétés les plus couramment utilisées.  
  
-   Autorise la suppression, la substitution ou l'extension des propriétés par défaut.  
  
-   Vérifie que les modifications apportées aux valeurs des propriétés sur l'hôte sont automatiquement détectées et traduites dans le contrôle ou l'élément hébergé.  
  
> [!NOTE]
>  Les événements de modification de propriété ne sont pas propagés jusqu'à l'hébergement du contrôle ou la hiérarchie d'élément.  La propriété n'est pas traduite si la valeur locale d'une propriété n'est pas modifiée en raison d'un paramètre direct, de styles, d'héritage, de liaison de données ou d'autres mécanismes qui modifient la valeur de la propriété.  
  
 Utilisez la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> sur l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> et la propriété <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> sur le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour accéder au mappage de propriétés.  
  
## Mappage de propriétés à l'aide de l'élément WindowsFormsHost  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> traduit les propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut en leurs équivalents [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l'aide de la table de traduction suivante.  
  
|Hébergement Windows Presentation Foundation|Windows Forms|Comportement d'interopérabilité|  
|-------------------------------------------------|-------------------|-------------------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> définit la propriété <xref:System.Windows.Forms.Control.BackColor%2A> et la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé.  Le mappage est exécuté à l'aide des règles suivantes :<br /><br /> -   Si <xref:System.Windows.Controls.Control.Background%2A> est une couleur unie, il est converti et utilisé pour définir la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle hébergé.  La propriété <xref:System.Windows.Forms.Control.BackColor%2A> n'est pas définie sur le contrôle hébergé, car celui\-ci peut hériter de la valeur de la propriété <xref:System.Windows.Forms.Control.BackColor%2A>. **Note:**  Le contrôle hébergé ne prend pas en charge la transparence.  Toute couleur assignée à <xref:System.Windows.Forms.Control.BackColor%2A> doit être totalement opaque, avec une valeur alpha 0xFF. <br /><br /> -   Si <xref:System.Windows.Controls.Control.Background%2A> n'est une couleur unie, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> crée une image bitmap de la propriété <xref:System.Windows.Controls.Control.Background%2A>.  Le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> assigne cette image bitmap à la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé.  L'effet obtenu est similaire à la transparence. **Note:**  Vous pouvez substituer ce comportement ou supprimer le mappage de propriétés <xref:System.Windows.Controls.Control.Background%2A>.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Si le mappage par défaut n'a pas été réassigné, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> parcourt sa hiérarchie ancêtre jusqu'à ce qu'il trouve un ancêtre avec son jeu de propriétés <xref:System.Windows.FrameworkElement.Cursor%2A>.  Cette valeur est traduite en curseur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] correspondant le plus.<br /><br /> Si le mappage par défaut de la propriété <xref:System.Windows.FrameworkElement.ForceCursor%2A> n'a pas été réassigné, le parcours s'arrête sur le premier ancêtre avec un <xref:System.Windows.FrameworkElement.ForceCursor%2A> ayant la valeur `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FlowDirection> correspond à <xref:System.Windows.Forms.RightToLeft>.<br /><br /> <xref:System.Windows.FlowDirection> correspond à <xref:System.Windows.Forms.RightToLeft>.<br /><br /> <xref:System.Windows.Forms.RightToLeft> n'est pas mappé.<br /><br /> <xref:System.Windows.FlowDirection?displayProperty=fullName> correspond à <xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> sur <xref:System.Drawing.Font?displayProperty=fullName> du contrôle hébergé|Le jeu de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font> correspondant.  Si une de ces propriétés est modifiée, un nouveau <xref:System.Drawing.Font> est créé.  Pour <xref:System.Windows.FontStyles.Normal%2A> : <xref:System.Drawing.FontStyle> est désactivé.  Pour <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A> : <xref:System.Drawing.FontStyle> est activé.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> sur <xref:System.Drawing.Font?displayProperty=fullName> du contrôle hébergé|Le jeu de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font> correspondant.  Si une de ces propriétés est modifiée, un nouveau <xref:System.Drawing.Font> est créé.  Pour <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A> ou <xref:System.Windows.FontWeights.UltraBold%2A> : <xref:System.Drawing.FontStyle> est activé.  Pour <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A> ou <xref:System.Windows.FontWeights.UltraLight%2A> : <xref:System.Drawing.FontStyle> est désactivé.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|Le jeu de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font> correspondant.  Si une de ces propriétés est modifiée, un nouveau <xref:System.Drawing.Font> est créé.  Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est redimensionné en fonction de la taille de police.<br /><br /> La taille de police dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est exprimée sous la forme de un quatre\-vingt\-seizième d'un pouce et dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sous la forme de un soixante\-douzième d'un pouce.  La conversion correspondante est :<br /><br /> Taille de police [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] \= Taille de police [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \* 72.0 \/ 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|Le mappage de propriétés <xref:System.Windows.Controls.Control.Foreground%2A> est exécuté à l'aide des règles suivantes :<br /><br /> -   Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.SolidColorBrush>, utilisez <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-   Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.GradientBrush>, utilisez la couleur du <xref:System.Windows.Media.GradientStop> avec la valeur de décalage la plus basse pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-   Pour tout autre type <xref:System.Windows.Media.Brush>, laissez <xref:System.Windows.Forms.Control.ForeColor%2A> inchangé.  Le paramètre par défaut est donc utilisé.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Si <xref:System.Windows.UIElement.IsEnabled%2A> est défini, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> définit la propriété <xref:System.Windows.Forms.Control.Enabled%2A> sur le contrôle hébergé.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Les quatre valeurs de la propriété <xref:System.Windows.Forms.Control.Padding%2A> sur le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé ont la même valeur <xref:System.Windows.Thickness>.<br /><br /> -   Les valeurs supérieures à la valeur <xref:System.Int32.MaxValue> prennent la valeur <xref:System.Int32.MaxValue>.<br />-   Les valeurs inférieures à la valeur <xref:System.Int32.MinValue> prennent la valeur <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility> correspond à <xref:System.Windows.Forms.Control.Visible%2A> \= `true`.  Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est visible.  Il n'est pas recommandé d'affecter explicitement `false` à la propriété <xref:System.Windows.Forms.Control.Visible%2A> sur le contrôle hébergé.<br />-   <xref:System.Windows.Visibility> correspond à <xref:System.Windows.Forms.Control.Visible%2A> \= `true` ou `false`.  Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé n'est pas dessiné et sa zone est réduite.<br />-   <xref:System.Windows.Visibility>: Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé occupe l'espace dans la présentation, mais il n'est pas visible.  Dans ce cas, la propriété <xref:System.Windows.Forms.Control.Visible%2A> a la valeur `true`.  Il n'est pas recommandé d'affecter explicitement `false` à la propriété <xref:System.Windows.Forms.Control.Visible%2A> sur le contrôle hébergé.|  
  
 Les propriétés attachées sur les éléments conteneurs sont totalement prises en charge par l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Pour plus d'informations, consultez [Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## Mises à jour des propriétés parent  
 Les modifications apportées à la plupart des propriétés parent entraînent des notifications sur le contrôle enfant hébergé.  La liste suivante décrit les propriétés qui n'entraînent pas notifications lorsque leur valeur est modifiée.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Par exemple, si vous modifiez la valeur de la propriété <xref:System.Windows.Controls.Control.Background%2A> de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle hébergé n'est pas modifiée.  
  
## Mappage de propriétés à l'aide du contrôle ElementHost  
 Les propriétés suivantes fournissent une notification de modification intégrée.  N'appelez pas la méthode <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> lorsque vous mappez ces propriétés.  
  
-   AutoSize  
  
-   BackColor  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Curseur  
  
-   Dock  
  
-   Activé  
  
-   Police  
  
-   ForeColor  
  
-   Emplacement  
  
-   Margin  
  
-   Padding  
  
-   Parent  
  
-   Region  
  
-   RightToLeft  
  
-   Taille  
  
-   TabIndex  
  
-   TabStop  
  
-   Texte  
  
-   Visible  
  
 Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> traduit les propriétés [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] par défaut en leurs équivalents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l'aide de la table de traduction suivante.  
  
 Pour plus d'informations, consultez [Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hébergement Windows Forms|Windows Presentation Foundation|Comportement d'interopérabilité|  
|-------------------------------|-------------------------------------|-------------------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> \(<xref:System.Drawing.Color?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\) sur l'élément hébergé|La définition de cette propriété force à repeindre avec un <xref:System.Windows.Media.ImageBrush>.  Si la propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> a la valeur `false` \(valeur par défaut\), ce <xref:System.Windows.Media.ImageBrush> est basé sur l'apparence du contrôle <xref:System.Windows.Forms.Integration.ElementHost>, notamment ses propriétés <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> et les gestionnaires de peinture attachés.<br /><br /> Si la propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> a la valeur `true`, <xref:System.Windows.Media.ImageBrush> est basé sur l'apparence du parent du contrôle <xref:System.Windows.Forms.Integration.ElementHost>, notamment les propriétés <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> du parent et les gestionnaires de peinture attachés.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> \(<xref:System.Drawing.Image?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\) sur l'élément hébergé|La définition de cette propriété provoque le même comportement que celui décrit pour le mappage <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> \(<xref:System.Windows.Media.Brush?displayProperty=fullName>\) sur l'élément hébergé|La définition de cette propriété provoque le même comportement que celui décrit pour le mappage <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> \(<xref:System.Windows.Forms.Cursor?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> \(<xref:System.Windows.Input.Cursor?displayProperty=fullName>\)|Le curseur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] standard est traduit en curseur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standard correspondant.  Si [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] n'est pas un curseur standard, la valeur par défaut est assignée.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Si <xref:System.Windows.Forms.Control.Enabled%2A> est défini, le contrôle <xref:System.Windows.Forms.Integration.ElementHost> définit la propriété <xref:System.Windows.UIElement.IsEnabled%2A> sur l'élément hébergé.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> \(<xref:System.Drawing.Font?displayProperty=fullName>\)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|La valeur <xref:System.Windows.Forms.Control.Font%2A> est traduite en un jeu correspondant de propriétés de police [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> sur l'élément hébergé|Si <xref:System.Drawing.Font.Bold%2A> est `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Si <xref:System.Drawing.Font.Bold%2A> est `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> sur l'élément hébergé|Si <xref:System.Drawing.Font.Italic%2A> est `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Si <xref:System.Drawing.Font.Italic%2A> est `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> sur l'élément hébergé|S'applique uniquement lors de l'hébergement d'un contrôle <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> sur l'élément hébergé|S'applique uniquement lors de l'hébergement d'un contrôle <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> \(<xref:System.Windows.Forms.RightToLeft?displayProperty=fullName>\)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> \(<xref:System.Windows.FlowDirection>\)|<xref:System.Windows.Forms.RightToLeft> correspond à <xref:System.Windows.FlowDirection>.<br /><br /> <xref:System.Windows.Forms.RightToLeft> correspond à <xref:System.Windows.FlowDirection>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> définit la propriété <xref:System.Windows.UIElement.Visibility%2A> sur l'élément hébergé à l'aide des règles suivantes :<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> \= `true` correspond à <xref:System.Windows.Visibility>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> \= `false` correspond à <xref:System.Windows.Visibility>.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Interopérabilité WPF et Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)   
 [Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)   
 [Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)