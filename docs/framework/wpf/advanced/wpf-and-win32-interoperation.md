---
title: "Interop&#233;rabilit&#233; WPF et Win32 | Microsoft Docs"
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
  - "héberger un contenu WPF dans une fenêtre Win32"
  - "interopérabilité HWND (WPF)"
  - "interopérabilité (WPF), Win32"
  - "code Win32, interopérabilité WPF"
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# Interop&#233;rabilit&#233; WPF et Win32
Cette rubrique fournit une vue d'ensemble de l'interopérabilité du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un environnement riche pour créer des applications.  Toutefois, si vous avez beaucoup investi dans du code [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], il peut s'avérer plus intéressant de réutiliser une partie de ce code.  
  
   
  
<a name="basics"></a>   
## Notions de base de l'interopérabilité WPF et Win32  
 Il existe deux techniques de base liées à l'interopérabilité entre du code [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Hébergement de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Grâce cette technique, vous pouvez bénéficier des capacités graphiques avancées de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans l'infrastructure d'une application et d'une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] standard.  
  
-   Hébergement d'une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Grâce à cette technique, vous pouvez utiliser un contrôle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] personnalisé existant dans le contexte d'un autre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], puis passer des données au\-delà des limites.  
  
 Les concepts inhérents à chacune de ces techniques sont présentés dans cette rubrique.  Pour obtenir une illustration plus orientée code de l'hébergement de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], consultez [Procédure pas à pas : hébergement de contenu WPF dans Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  Pour obtenir une illustration plus orientée code de l'hébergement de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez [Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## Projets d'interopérabilité WPF  
 Les interfaces [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont constituées de code managé. Toutefois, la plupart des programmes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existants sont écrits en [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] non managé.  Il est impossible d'appeler une interface [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir d'un vrai programme non managé.  Cependant, si vous utilisez l'option `/clr` avec le compilateur [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)], vous pouvez créer un programme managé\/non managé mixte dans lequel vous pouvez mélanger des appels [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] managés et non managés de façon transparente.  
  
 L'un des problèmes au niveau du projet est l'impossibilité de compiler des fichiers [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dans un projet [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Il existe toutefois plusieurs techniques de division du projet qui permettent de contourner ce problème.  
  
-   Créez une DLL [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] qui contient l'ensemble de vos pages [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sous la forme d'assembly compilé, puis intégrez cette [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] en tant que référence dans le fichier exécutable [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  
  
-   Créez un exécutable [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] pour le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et faites\-le référencer une [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] qui intègre le contenu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Utilisez <xref:System.Windows.Markup.XamlReader.Load%2A> pour charger le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au moment de l'exécution, au lieu de compiler le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   N'utilisez pas le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et écrivez tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans du code, en élaborant l'arborescence d'éléments à partir de <xref:System.Windows.Application>.  
  
 Utilisez la technique qui vous convient le mieux.  
  
> [!NOTE]
>  Si vous n'avez pas utilisé [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] avant, vous pouvez remarquer certains «  » nouveaux mots clés tels qu' `gcnew` et `nullptr` dans les exemples de code d'interopérabilité. Ces mots clés remplacent l'ancienne syntaxe de double trait de soulignement \(`__gc`\) et fournissent une syntaxe plus naturelle pour le code managé dans [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Pour en savoir plus sur les fonctionnalités managées de [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], consultez [Extensions de composant pour les plateformes Runtime](../Topic/Component%20Extensions%20for%20Runtime%20Platforms.md) et [Hello, C\+\+\/CLI \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## Utilisation des HWND par WPF  
 Pour tirer le meilleur parti de l'interopérabilité HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez comprendre comment [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise les HWND.  Pour un HWND, vous ne pouvez pas mélanger le rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec le rendu [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] ou [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] \/ [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)],  ce qui entraîne plusieurs implications.  D'une part, pour pouvoir mélanger ces modèles de rendu, vous devez créer une solution d'interopérabilité et utiliser les segments d'interopérabilité désignés pour chaque modèle de rendu à utiliser.  D'autre part, le comportement de rendu crée une restriction d'« espace de rendu » \('airspace' en anglais\) relative aux objectifs de la solution d'interopérabilité.  Le concept d'« espace de rendu » est expliqué en détail dans la rubrique [Vue d'ensemble des régions de technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
 Tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] affichés à l'écran sont stockés par un HWND.  Lorsque vous créez un <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée un HWND de niveau supérieur et utilise un <xref:System.Windows.Interop.HwndSource> pour placer <xref:System.Windows.Window> et son contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans le HWND.  Le reste du contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de l'application partage ce HWND singulier.  Les menus, les zones de liste déroulante et les autres menus contextuels constituent une exception à ce principe.  Ces éléments créent leur propre fenêtre de niveau supérieur. Par conséquent, un menu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut potentiellement dépasser le bord du HWND de fenêtre qui le contient.  Si vous utilisez <xref:System.Windows.Interop.HwndHost> pour placer un HWND dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] indique à [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] comment positionner le nouveau HWND enfant par rapport au HWND <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 La transparence dans et entre les HWND constitue un concept connexe des HWND.  Il est également abordé à la rubrique [Vue d'ensemble des régions de technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## Hébergement de contenu WPF dans une fenêtre Microsoft Win32  
 L'élément principal de l'hébergement d'un objet [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] est la classe <xref:System.Windows.Interop.HwndSource>.  Cette classe encapsule le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], afin que le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] puisse être incorporé dans votre [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] en tant que fenêtre enfant.  L'approche suivante combine [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans une application unique.  
  
1.  Implémentez le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(l'élément racine de contenu\) en tant que classe managée.  En règle générale, la classe hérite d'une classe qui peut contenir plusieurs éléments enfants et\/ou être utilisée en tant qu'élément racine, comme <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Page>.  Dans les étapes suivantes, cette classe est appelée « classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] » et les instances de la classe sont appelées « objets de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ».  
  
2.  Implémentez une application [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] avec [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)].  Si vous démarrez avec une application [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] non managée existante, vous pouvez généralement lui permettre d'appeler le code managé en modifiant les paramètres du projet afin d'inclure l'indicateur de compilateur `/clr` \(cette rubrique ne décrit pas la portée complète des éléments nécessaires à la prise en charge de la compilation `/clr`\).  
  
3.  Affectez au modèle de thread un thread cloisonné \(STA, Single\-Threaded Apartment\).  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ce modèle de thread.  
  
4.  Gérez la notification WM\_CREATE dans votre procédure de fenêtre.  
  
5.  Dans le gestionnaire \(ou une fonction appelée par le gestionnaire\), effectuez les opérations suivantes :  
  
    1.  Créez un objet <xref:System.Windows.Interop.HwndSource> en utilisant le HWND de fenêtre parente comme paramètre `parent`.  
  
    2.  Créez une instance de la classe de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3.  Attribuez une référence à l'objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l'objet <xref:System.Windows.Interop.HwndSource>.  
  
    4.  La propriété <xref:System.Windows.Interop.HwndSource.Handle%2A> de l'objet <xref:System.Windows.Interop.HwndSource> contient le handle de fenêtre \(HWND\).  Pour obtenir un HWND que vous pouvez utiliser dans la partie non managée de l'application, effectuez un cast de `Handle.ToPointer()` en un HWND.  
  
6.  Implémentez une classe managée qui contient un champ statique comportant une référence à l'objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette classe permet d'obtenir une référence à l'objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à partir du code [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et, surtout, empêche <xref:System.Windows.Interop.HwndSource> d'être récupéré par inadvertance par le garbage collector.  
  
7.  Recevez les notifications de l'objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en attachant un gestionnaire à un ou plusieurs des événements d'objet de contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8.  Communiquez avec l'objet de contenu d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l'aide de la référence que vous stockez dans le champ statique pour définir des propriétés, des méthodes d'appel, etc..  
  
> [!NOTE]
>  Vous pouvez en faire ou toute la définition de classe de contenu d' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de l'étape dans une [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] à l'aide de la classe partielle par défaut de la classe de contenu, si vous générez un assembly distinct et le référencer. Bien que vous inclure en général un objet d' <xref:System.Windows.Application> dans le cadre de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compiler dans un assembly, vous n'exécutez pas à cet <xref:System.Windows.Application> dans le cadre de l'interopérabilité, vous utilisez simplement un ou plusieurs des classes racine des fichiers d' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] visés par l'application et référencez leurs classes partielles.  Le reste de la procédure est semblable à celle présentée ci\-dessus.  
>   
>  Chacune de ces étapes est illustrée à l'aide de code à la rubrique [Procédure pas à pas : hébergement de contenu WPF dans Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## Hébergement d'une fenêtre Microsoft Win32 dans WPF  
 L'élément principal de l'hébergement d'une fenêtre [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dans un autre contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est la classe <xref:System.Windows.Interop.HwndHost>.  Cette classe englobe la fenêtre dans un wrapper dans un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui peut être ajouté à une arborescence d'éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.Windows.Interop.HwndHost> prend également en charge les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] qui vous permettent de réaliser certaines tâches telles que le traitement des messages de la fenêtre hébergée.  La procédure de base est la suivante :  
  
1.  Créez une arborescence d'éléments pour une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(à l'aide de code ou de balises\).  Recherchez un point approprié et autorisé dans l'arborescence d'éléments où l'implémentation <xref:System.Windows.Interop.HwndHost> peut être ajoutée en tant qu'élément enfant.  Dans les étapes suivantes, cet élément est appelé "élément de réservation".  
  
2.  Effectuez une dérivation de <xref:System.Windows.Interop.HwndHost> afin de créer un objet stockant le contenu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
3.  Dans cette classe hôte, substituez la méthode <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> <xref:System.Windows.Interop.HwndHost>.  Retournez le HWND de la fenêtre hébergée.  Vous pouvez inclure dans un wrapper le ou les contrôles réels en tant que fenêtre enfant de la fenêtre retournée. L'inclusion des contrôles dans un wrapper dans une fenêtre hôte permet au contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de recevoir facilement les notifications issues des contrôles.  Cette technique permet de corriger certains problèmes [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] liés à la gestion des messages au niveau de la limite de contrôles hébergés.  
  
4.  Substituez les méthodes <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> et <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  L'objectif est de traiter le nettoyage et de supprimer les références au contenu hébergé, plus particulièrement si vous avez créé des références à des objets non managés.  
  
5.  Dans votre fichier code\-behind, créez une instance de la classe d'hébergement de contrôles et définissez\-la comme enfant de l'élément de réservation.  En général, vous utilisez un gestionnaire d'événements \(<xref:System.Windows.FrameworkElement.Loaded>, par exemple\) ou le constructeur de classe partielle.  Vous pouvez toutefois ajouter le contenu d'interopérabilité avec un comportement au moment de l'exécution.  
  
6.  Traitez les messages de fenêtre sélectionnés, telles les notifications de contrôle.  Les deux approches possibles  fournissent un accès identique au flux de messages. Vous devez dès lors guider votre choix en fonction de la commodité de programmation.  
  
    -   Implémentez le traitement pour tous les messages \(pas seulement les messages d'arrêt\) dans la substitution de la méthode <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Confiez le traitement des messages à l'élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] d'hébergement en gérant l'événement <xref:System.Windows.Interop.HwndHost.MessageHook>.  Cet événement est déclenché pour chaque message envoyé à la procédure de fenêtre principale de la fenêtre hébergée.  
  
    -   Vous ne pouvez pas traiter les messages provenant de fenêtres hors processus à l'aide de <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Communiquez avec la fenêtre hébergée à l'aide d'un appel de code non managé pour appeler la fonction `SendMessage` non managée.  
  
 L'exécution de ces étapes crée une application qui fonctionne avec les entrées de la souris.  Vous pouvez ajouter la prise en charge de la tabulation pour la fenêtre hébergée en implémentant l'interface <xref:System.Windows.Interop.IKeyboardInputSink>.  
  
 Chacune de ces étapes est illustrée à l'aide de code à la rubrique [Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### HWND dans WPF  
 Vous pouvez envisager <xref:System.Windows.Interop.HwndHost> comme un contrôle spécial.  \(théoriquement, <xref:System.Windows.Interop.HwndHost> est une classe dérivée de <xref:System.Windows.FrameworkElement>, et non une classe dérivée de <xref:System.Windows.Controls.Control>, mais elle peut être considérée comme un contrôle à des fins d'interopérabilité\). <xref:System.Windows.Interop.HwndHost> soustrait la nature [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] sous\-jacente du contenu hébergé de sorte que le reste de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] considère le contenu hébergé comme un autre objet de contrôle, qui doit restituer et traiter l'entrée.  <xref:System.Windows.Interop.HwndHost>se comporte généralement comme tout autre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.FrameworkElement>, bien qu'il y ait des différences importantes en termes de sortie \(dessin et graphiques\) et d'entrée \(souris et clavier\) dues aux limitations de prise en charge des HWND sous\-jacents.  
  
#### Principales différences dans le comportement de sortie  
  
-   <xref:System.Windows.FrameworkElement>, qui correspond à la classe de base <xref:System.Windows.Interop.HwndHost>, comporte de nombreuses propriétés qui impliquent la modification de l'interface utilisateur.  Il s'agit notamment de propriétés telles que <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName>, qui modifie la disposition des éléments dans cet élément en tant que parent.  Toutefois, la plupart de ces propriétés ne sont pas mappées aux équivalents possibles de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], même si ces équivalents existent.  Un nombre trop important de ces propriétés et de leur signification repose essentiellement sur la technologie de rendu, ce qui rend les mappages peu pratiques.  Par conséquent, la définition de propriétés telles que <xref:System.Windows.FrameworkElement.FlowDirection%2A> dans <xref:System.Windows.Interop.HwndHost> n'a aucun effet.  
  
-   Une transformation n'a aucun impact sur <xref:System.Windows.Interop.HwndHost>, par exemple pour le faire pivoter, le mettre à l'échelle ou l'incliner.  
  
-   <xref:System.Windows.Interop.HwndHost> ne prend pas en charge la propriété <xref:System.Windows.UIElement.Opacity%2A> \(fusion alpha\).  Si le contenu de <xref:System.Windows.Interop.HwndHost> effectue des opérations <xref:System.Drawing> qui incluent des informations alpha, il ne s'agit pas d'une violation en soi. Toutefois, dans son ensemble, <xref:System.Windows.Interop.HwndHost> ne prend en charge qu'une opacité égale à 1.0 \(100 %\).  
  
-   <xref:System.Windows.Interop.HwndHost> apparaît sur les autres éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans la même fenêtre de niveau supérieur.  Toutefois, un menu généré <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ContextMenu> étant une fenêtre de niveau supérieur distincte, il se comporte correctement avec <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> ne respecte pas la zone de découpage du <xref:System.Windows.UIElement> parent.  Il s'agit d'un problème potentiel si vous tentez de placer une classe <xref:System.Windows.Interop.HwndHost> dans une zone de défilement ou <xref:System.Windows.Controls.Canvas>.  
  
#### Principales différences dans le comportement d'entrée  
  
-   En général, lorsque la portée des périphériques d'entrée est définie dans la zone [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] hébergée par <xref:System.Windows.Interop.HwndHost>, les événements d'entrée sont directement placés dans [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Lorsque la souris passe sur <xref:System.Windows.Interop.HwndHost>, l'application ne reçoit pas d'événement de souris [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et la propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsMouseOver%2A> a la valeur `false`.  
  
-   Lorsque <xref:System.Windows.Interop.HwndHost> a le focus clavier, l'application ne reçoit pas d'événement de clavier [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et la propriété [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> a la valeur `false`.  
  
-   Lorsque le focus est dans <xref:System.Windows.Interop.HwndHost> et passe à un autre contrôle dans <xref:System.Windows.Interop.HwndHost>, l'application ne reçoit pas les événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.GotFocus> ou <xref:System.Windows.UIElement.LostFocus>.  
  
-   Les événements et propriétés de stylet connexes sont semblables et ne signalent pas d'informations lorsque le stylet est sur <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## Tabulation, mnémoniques et accélérateurs  
 Grâce aux interfaces <xref:System.Windows.Interop.IKeyboardInputSink> et <xref:System.Windows.Interop.IKeyboardInputSite>, vous pouvez créer une expérience de clavier transparente pour les applications mixtes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] :  
  
-   Tabulation entre des composants [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Mnémoniques et accélérateurs fonctionnant lorsque le focus est sur un composant Win32 et sur un composant WPF.  
  
 Les classes <xref:System.Windows.Interop.HwndHost> et <xref:System.Windows.Interop.HwndSource> fournissent des implémentations de <xref:System.Windows.Interop.IKeyboardInputSink>, mais elles ne peuvent pas gérer tous les messages d'entrée nécessaires dans le cadre de scénarios plus évolués.  Substituez les méthodes appropriées pour obtenir le comportement du clavier souhaité.  
  
 Les interfaces assurent uniquement la prise en charge des événements qui ont lieu lors de la transition entre les zones [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  Dans la zone [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], le comportement de tabulation est entièrement déterminé par la logique [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implémentée pour la tabulation, le cas échéant.  
  
## Voir aussi  
 <xref:System.Windows.Interop.HwndHost>   
 <xref:System.Windows.Interop.HwndSource>   
 <xref:System.Windows.Interop>   
 [Procédure pas à pas : hébergement d'un contrôle Win32 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)   
 [Procédure pas à pas : hébergement de contenu WPF dans Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)