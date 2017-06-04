---
title: "Consid&#233;rations sur la disposition de l&#39;&#233;l&#233;ment WindowsFormsHost | Microsoft Docs"
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
  - "dip (device independent pixel)"
  - "présentation dynamique (interopérabilité WPF)"
  - "interopérabilité (WPF), Windows Forms"
  - "Windows Forms (WPF), interopérabilité avec"
  - "Windows Forms, interopérabilité WPF"
  - "considérations sur la disposition des éléments WindowsFormsHost"
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Consid&#233;rations sur la disposition de l&#39;&#233;l&#233;ment WindowsFormsHost
Cette rubrique décrit comment l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> interagit avec le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prennent en charge des logiques différentes mais comparables pour dimensionner et positionner des éléments sur un formulaire ou une page.  Lorsque vous créez une interface utilisateur hybride qui héberge des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> intègre les deux méthodes de disposition.  
  
## Différences de disposition entre WPF et Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise une disposition indépendante de la résolution.  Toutes les dimensions de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont spécifiées à l'aide de *pixels indépendants du périphérique*.  Un pixel indépendant du périphérique ou DIP \(Device Independent Pixel\) mesure un quatre\-vingt\-seizième d'un pouce et est indépendant de la résolution ; ainsi, le rendu obtenu sur un moniteur 72 ppp sera identique à celui obtenu sur une imprimante 19 200 ppp.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est également basé sur la *disposition dynamique*.  Cela signifie qu'un élément d'interface se positionne sur un formulaire ou une page en fonction de son contenu, de son conteneur de disposition parent et de la dimension d'écran disponible.  La disposition dynamique facilite la localisation en ajustant automatiquement la taille et la position des éléments d'interface lorsque la longueur des chaînes qu'ils contiennent est modifiée.  
  
 La disposition dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est dépendante du périphérique et plus vraisemblablement statique.  En général, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sont positionnés de façon absolue sur un formulaire à l'aide de dimensions spécifiées en pixels matériel.  Toutefois, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prend également en charge des fonctionnalités de disposition dynamique, comme décrit dans le tableau suivant.  
  
|Fonctionnalité de disposition|Description|  
|-----------------------------------|-----------------|  
|Redimensionnement automatique|Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se redimensionnent afin que leur contenu s'affiche correctement.  Pour plus d'informations, consultez [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Ancrage|Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prennent en charge le positionnement et le dimensionnement en fonction du conteneur parent.  Pour plus d'informations, consultez <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName> et <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>.|  
|Mise à l'échelle automatique|Les contrôles conteneur se redimensionnent et redimensionnent leurs enfants selon la résolution du périphérique de sortie ou la taille, en pixels, de la police de conteneur par défaut.  Pour plus d'informations, consultez [Mise à l'échelle automatique dans les Windows Forms](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Conteneurs de disposition|Les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> organisent leurs contrôles enfants et se dimensionnent en fonction de leur contenu.|  
  
## Limitations de disposition  
 En général, vous ne pouvez pas mettre à l'échelle et transformer les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] autant que vous pouvez le faire dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La liste suivante décrit les limitations connues lorsque l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> essaie d'intégrer son contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Dans certains cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas être redimensionnés ou peuvent l'être uniquement à des dimensions spécifiques.  Par exemple, un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> prend en charge la seule hauteur définie par la taille de police du contrôle.  Dans une disposition dynamique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] où les éléments peuvent être étirés verticalement, un contrôle <xref:System.Windows.Forms.ComboBox> hébergé ne s'étirera pas comme prévu.  
  
-   Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas subir de rotation ni d'inclinaison.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> déclenche l'événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> si vous effectuez une inclinaison ou une rotation.  Si vous ne gérez pas l'événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, une exception <xref:System.InvalidOperationException> est levée.  
  
-   Dans la plupart des cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la mise à l'échelle proportionnelle.  Même si les dimensions générales du contrôle sont mises à l'échelle, les contrôles enfants et les éléments de composant du contrôle peuvent ne pas être redimensionnés comme prévu.  Cette limitation dépend de la prise en charge de la mise à l'échelle de chaque contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  En outre, vous ne pouvez pas réduire de contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à une taille de 0 pixel.  
  
-   Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prennent en charge la mise à l'échelle automatique, qui entraîne un redimensionnement automatique du formulaire et de ses contrôles en fonction de la taille de police.  Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la modification de la taille de police n'entraîne pas de redimensionnement de la disposition entière, bien que chaque élément individuel puisse être redimensionné dynamiquement.  
  
### Ordre de plan  
 Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous pouvez modifier l'ordre de plan des éléments afin d'en contrôler la superposition.  Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est dessiné dans un handle de fenêtre \(HWND\) séparé ; ainsi, il apparaît toujours au\-dessus des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé sera également dessiné au dessus des éléments <xref:System.Windows.Documents.Adorner>.  
  
## Comportement de disposition  
 Les sections suivantes décrivent les aspects spécifiques du comportement de disposition lorsque des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sont hébergés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Mise à l'échelle, conversion d'unité et indépendance vis\-à\-vis du périphérique  
 Chaque fois que l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> exécute des opérations qui impliquent des dimensions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], deux systèmes de coordonnées sont impliqués : un système de pixels indépendants du périphérique pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et un système de pixels matériel pour [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Par conséquent, vous devez appliquer des conversions d'unité et de mise à l'échelle appropriées afin d'obtenir une disposition cohérente.  
  
 La conversion entre les systèmes de coordonnées dépend de la résolution de périphérique actuelle et des transformations appliquées à la disposition ou au rendu de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> ou de ses ancêtres.  
  
 Si le périphérique de sortie a une résolution de 96 ppp et si aucune mise à l'échelle n'a été appliquée à l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, un pixel indépendant du périphérique équivaut à un pixel matériel.  
  
 Dans tous les autres cas, une mise à l'échelle des systèmes de coordonnées est requise.  Le contrôle hébergé n'est pas redimensionné,  mais l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> essaie de mettre à l'échelle le contrôle hébergé et tous ses contrôles enfants.  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prenant pas totalement en charge la mise à l'échelle, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est redimensionné en fonction des capacités de chaque contrôle.  
  
 Remplacez la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> afin d'obtenir une mise à l'échelle personnalisée pour le contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] hébergé.  
  
 Outre la mise à l'échelle, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> gère les cas d'arrondi et de dépassement de capacité comme décrit dans le tableau suivant.  
  
|Problème de conversion|Description|  
|----------------------------|-----------------|  
|Arrondi|Les dimensions des pixels indépendants du périphérique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont spécifiées en tant que `double`, tandis que les dimensions des pixels matériel [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sont spécifiées en tant que `int`.  Lorsque des dimensions de type `double` sont converties en dimensions de type `int`, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise l'arrondi standard, de sorte que les valeurs fractionnaires inférieures à 0,5 sont arrondies à 0.|  
|Dépassement de capacité|Lorsque les dimensions de type `double` de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont converties en `int`, un dépassement de capacité peut se produire.  Les valeurs supérieures à la valeur <xref:System.Int32.MaxValue> prennent la valeur <xref:System.Int32.MaxValue>.|  
  
### Propriétés relatives à la disposition  
 Les propriétés qui contrôlent le comportement de disposition dans les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont mappées de manière appropriée par l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Pour plus d'informations, consultez [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### Modifications de disposition dans le contrôle hébergé  
 Les modifications apportées à la disposition dans le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé sont propagées à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] afin de déclencher des mises à jour de disposition.  La méthode <xref:System.Windows.UIElement.InvalidateMeasure%2A> appliquée à l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> garantit que les modifications apportées à la disposition dans le contrôle hébergé provoquent l'exécution du moteur de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Contrôles Windows Forms dimensionnés continuellement  
 Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui prennent en charge la mise à l'échelle continue interagissent totalement avec le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise les méthodes habituelles <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> pour dimensionner et organiser le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé.  
  
### Dimensionnement de l'algorithme  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> utilise la procédure suivante pour dimensionner le contrôle hébergé :  
  
1.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> substitue les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  
  
2.  Pour déterminer la taille du contrôle hébergé, la méthode <xref:System.Windows.FrameworkElement.MeasureOverride%2A> appelle la méthode <xref:System.Windows.Forms.Control.GetPreferredSize%2A> du contrôle hébergé avec une contrainte traduite de la contrainte passée à la méthode <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
3.  La méthode <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> essaie d'affecter la contrainte de taille donnée au contrôle hébergé.  
  
4.  Si la propriété <xref:System.Windows.Forms.Control.Size%2A> du contrôle hébergé correspond à la contrainte spécifiée, le contrôle hébergé est dimensionné selon cette contrainte.  
  
 Si la propriété <xref:System.Windows.Forms.Control.Size%2A> ne correspond pas à la contrainte spécifiée, le contrôle hébergé ne prend pas en charge le dimensionnement continu.  Par exemple, le contrôle <xref:System.Windows.Forms.MonthCalendar> autorise uniquement des tailles discrètes.  Les tailles autorisées pour ce contrôle sont des entiers \(représentant le nombre de mois\), pour la hauteur et la largeur.  Dans les cas comme celui\-ci, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> se comporte comme suit :  
  
-   Si la propriété <xref:System.Windows.Forms.Control.Size%2A> retourne une taille supérieure à la contrainte spécifiée, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> découpe le contrôle hébergé.  La hauteur et la largeur sont gérées séparément ; le contrôle hébergé peut donc être découpé en hauteur comme en largeur.  
  
-   Si la propriété <xref:System.Windows.Forms.Control.Size%2A> retourne une taille inférieure à la contrainte spécifiée, l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> accepte cette valeur et la retourne au système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Procédure pas à pas : organisation des contrôles Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)   
 [Réorganisation des contrôles Windows Forms dans l'exemple WPF](http://go.microsoft.com/fwlink/?LinkID=159971)   
 [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)