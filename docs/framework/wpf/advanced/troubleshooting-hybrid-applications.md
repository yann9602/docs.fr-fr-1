---
title: "D&#233;pannage des applications hybrides | Microsoft Docs"
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
  - "applications hybrides (interopérabilité WPF)"
  - "interopérabilité (WPF), Windows Forms"
  - "boucles de message (WPF)"
  - "contrôles superposés"
  - "Windows Forms (WPF), interopérabilité avec"
  - "Windows Forms, interopérabilité WPF"
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# D&#233;pannage des applications hybrides
<a name="introduction"></a> Cette rubrique décrit quelques problèmes courants qui peuvent se produire lors de la création d'applications hybrides qui utilisent à la fois les technologies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
   
  
<a name="overlapping_controls"></a>   
## Contrôles superposés  
 Les contrôles ne se superposent peut\-être pas comme ils le devraient.  Les [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] utilisent un handle de fenêtre \(HWND\) séparé pour chaque contrôle.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un HWND pour tout le contenu d'une page.  Cette différence d'implémentation provoque des comportements de superposition inattendus.  
  
 Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaît toujours au\-dessus du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost> apparaît dans l'ordre de plan du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  Il est possible de superposer les contrôles <xref:System.Windows.Forms.Integration.ElementHost>, mais le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé ne se mélange pas et n'interagit pas.  
  
<a name="child_property"></a>   
## Propriété Child  
 Les classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> peuvent héberger uniquement un seul contrôle ou élément enfant.  Pour héberger plusieurs contrôles ou éléments, vous devez utiliser un conteneur comme contenu enfant.  Par exemple, vous pouvez ajouter des contrôles bouton et case à cocher [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à un contrôle <xref:System.Windows.Forms.Panel?displayProperty=fullName>, puis assigner le panneau à la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Toutefois, vous ne pouvez pas ajouter les contrôles bouton et case à cocher séparément au même contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="scaling"></a>   
## Mise à l'échelle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] possèdent des modèles de mise à l'échelle différents.  Certaines transformations de mise à l'échelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont explicites pour les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], mais d'autres ne le sont pas.  Par exemple, il est possible de mettre un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à 0, mais si vous essayez de mettre à l'échelle le même contrôle pour lui redonner une valeur autre que zéro, sa taille reste 0.  Pour plus d'informations, consultez [Considérations sur la disposition de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## Adaptateur  
 L'utilisation des classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> peut provoquer une confusion, car elles comprennent un conteneur masqué.  Ces deux classes, <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost>, possèdent un conteneur masqué appelé *adaptateur*, qu'elles utilisent pour héberger du contenu.  Pour l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, l'adaptateur dérive de la classe <xref:System.Windows.Forms.ContainerControl?displayProperty=fullName>.  Pour le contrôle <xref:System.Windows.Forms.Integration.ElementHost>, l'adaptateur dérive de l'élément <xref:System.Windows.Controls.DockPanel>.  Lorsque vous voyez des références à l'adaptateur dans d'autres rubriques d'interopérabilité, il est question de ce conteneur.  
  
<a name="nesting"></a>   
## Imbrication  
 L'imbrication d'un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dans un contrôle <xref:System.Windows.Forms.Integration.ElementHost> n'est pas prise en charge.  L'imbrication d'un contrôle <xref:System.Windows.Forms.Integration.ElementHost> dans un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n'est pas prise en charge non plus.  
  
<a name="focus"></a>   
## Focus  
 Le focus fonctionne différemment dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et dans les [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], ce qui peut provoquer des problèmes de focus dans une application hybride.  Par exemple, si vous avez le focus dans un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> et que vous diminuez et restaurez la page ou que vous affichez une boîte de dialogue modale, le focus dans l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> risque d'être perdu.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> conserve le focus, mais ce n'est peut\-être pas le cas pour le contrôle.  
  
 La validation des données est également affectée par le focus.  Elle fonctionne dans un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, mais pas lorsque vous sortez de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, ni entre deux éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> différents.  
  
<a name="property_mapping"></a>   
## Mappage de propriétés  
 Certains mappages de propriétés nécessitent une interprétation approfondie pour lier des implémentations différentes entre les technologies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Les mappages de propriétés permettent à votre code de réagir aux changements de polices, de couleurs et d'autres propriétés.  En général, les mappages de propriétés fonctionnent en écoutant soit les événements *propriété*Changed, soit les appels On*propriété*Changed, puis en configurant les propriétés adéquates sur le contrôle enfant ou son adaptateur.  Pour plus d'informations, consultez [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## Propriétés relatives à la disposition sur le contenu hébergé  
 Lorsque la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=fullName> est assignée, plusieurs propriétés relatives à la disposition sur le contenu hébergé sont automatiquement configurées.  La modification de ces propriétés peut provoquer des comportements de disposition inattendus.  
  
 Votre contenu hébergé est ancré pour remplir le parent <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost>.  Pour activer ce comportement de remplissage, plusieurs propriétés sont configurées lorsque vous définissez la propriété enfant.  Le tableau suivant répertorie les propriétés de contenu qui sont définies par les classes <xref:System.Windows.Forms.Integration.ElementHost> et <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
|Classe de l'hôte|Propriétés de contenu|  
|----------------------|---------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Vous ne devez pas définir ces propriétés directement sur le contenu hébergé.  Pour plus d'informations, consultez [Considérations sur la disposition de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## Applications de navigation  
 Les applications de navigation ne conservent pas toujours l'état utilisateur.  L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> recrée ses contrôles lorsqu'il est utilisé dans une application de navigation.  Les contrôles enfants sont recréés lorsque l'utilisateur quitte la page hébergeant l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, puis l'affiche de nouveau.  Tout contenu entré par l'utilisateur sera perdu.  
  
<a name="message_loop_interoperation"></a>   
## Interopérabilité des boucles de messages  
 Lorsque vous utilisez les boucles de messages des [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], les messages peuvent ne pas être traités comme prévu.  La méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> est appelée par le constructeur <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Cette méthode ajoute un filtre de message à la boucle de messages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Ce filtre appelle la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName> si <xref:System.Windows.Forms.Control?displayProperty=fullName> était la cible du message, puis traduit\/distribue le message.  
  
 Si vous affichez un <xref:System.Windows.Window> dans une boucle de messages [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] avec <xref:System.Windows.Forms.Application.Run%2A?displayProperty=fullName>, vous ne pouvez rien entrer sauf si vous appelez la méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>.  La méthode <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> prend un <xref:System.Windows.Window> et ajoute un <xref:System.Windows.Forms.IMessageFilter?displayProperty=fullName> qui redirige les messages relatifs aux clés vers la boucle de messages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour plus d'informations, consultez [Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## Opacité et superposition  
 La classe <xref:System.Windows.Interop.HwndHost> ne prend pas en charge la superposition.  Cela signifie que la configuration de la propriété <xref:System.Windows.UIElement.Opacity%2A> sur l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n'a aucun effet, et aucune fusion ne sera effectuée avec d'autres fenêtres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dont la propriété <xref:System.Windows.Window.AllowsTransparency%2A> a la valeur `true`.  
  
<a name="dispose"></a>   
## Suppression  
 Si vous ne supprimez pas correctement les classes, cela peut entraîner une fuite des ressources.  Dans vos applications hybrides, vérifiez que les classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost> sont supprimées, sinon une fuite des ressources risque de se produire.  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] supprime les contrôles <xref:System.Windows.Forms.Integration.ElementHost> lorsque son parent <xref:System.Windows.Forms.Form> non modal se ferme. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supprime les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> lorsque votre application s'arrête.  Il est possible d'afficher un élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dans un <xref:System.Windows.Window> dans une boucle de messages [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Dans ce cas, votre code ne recevra peut\-être pas de notification que l'application va être arrêtée.  
  
<a name="enabling_visual_styles"></a>   
## Activation de styles visuels  
 Les styles visuels [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] sur un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne sont peut\-être pas activés.  La méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> est appelée dans le modèle pour une application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Bien que cette méthode ne soit pas appelée par défaut, si vous utilisez [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] pour créer un projet, vous obtiendrez des styles visuels d' [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] pour les contrôles, si la version 6,0 de Comctl32.dll est disponible. Vous devez appeler la méthode d' <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> avant que les handles soient créés sur le thread.  Pour plus d'informations, consultez [Comment : activer des styles visuels dans une application hybride](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## Contrôles sous licence  
 Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sous licence qui affichent une boîte de message avec les informations relatives à la licence peuvent provoquer un comportement inattendu pour une application hybride.  Certains de ces contrôles affichent une boîte de dialogue en réponse à la création du handle.  Par exemple, un contrôle sous licence peut informer l'utilisateur qu'une licence est requise ou qu'il dispose encore de trois essais pour le contrôle.  
  
 L'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> dérive de la classe <xref:System.Windows.Interop.HwndHost> et le handle du contrôle enfant est créé dans la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>.  La classe <xref:System.Windows.Interop.HwndHost> ne permet pas de traiter les messages dans la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>, mais l'affichage d'une boîte de dialogue peut déclencher l'envoi des messages.  Pour activer ce scénario d'attribution de licences, appelez la méthode <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=fullName> sur le contrôle avant de l'assigner comme enfant de l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="wpf_designer"></a>   
## Concepteur WPF  
 Vous pouvez concevoir votre contenu WPF à l'aide du [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)].  Les sections suivantes décrivent certains problèmes courants qui peuvent se produire lors de la création d'applications hybrides avec le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### BackColorTransparent est ignoré au moment du design.  
 Il est possible que la propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> ne fonctionne pas comme prévu au moment du design.  
  
 Si un contrôle WPF n'est pas sur un parent visible, l'exécution de WPF ignore la valeur <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>.  <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> peut notamment être ignoré si l'objet <xref:System.Windows.Forms.Integration.ElementHost> est créé dans un <xref:System.AppDomain> distinct.  Par contre, lorsque vous lancez l'application, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> fonctionne normalement.  
  
### La liste d'erreurs au moment du design apparaît lorsque le dossier obj est supprimé.  
 Si le dossier obj est supprimé, la liste d'erreurs au moment du design apparaît.  
  
 En cas de design à l'aide de <xref:System.Windows.Forms.Integration.ElementHost>, le Concepteur Windows Forms utilise des fichiers générés dans le dossier Debug ou Release situé dans le dossier obj de votre projet.  Si vous supprimez ces fichiers, le système affiche la liste d'erreurs au moment du design.  Pour résoudre ce problème, recréez votre projet.  Pour plus d'informations, consultez [Erreurs au moment du design dans le Concepteur Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## ElementHost et IME  
 Les contrôles WPF hébergés dans un <xref:System.Windows.Forms.Integration.ElementHost> ne prennent actuellement pas en charge la propriété <xref:System.Windows.Forms.Control.ImeMode%2A>.  Toute modification apportée à <xref:System.Windows.Forms.Control.ImeMode%2A> sera ignorée par les contrôles hébergés.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Interopérabilité avec le Concepteur WPF](http://msdn.microsoft.com/fr-fr/2cb7c1ca-2a75-463b-8801-fba81e2b7042)   
 [Architecture d'entrée pour l'interopérabilité entre Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)   
 [Comment : activer des styles visuels dans une application hybride](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)   
 [Considérations sur la disposition de l'élément WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)   
 [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)   
 [Erreurs au moment du design dans le Concepteur Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)