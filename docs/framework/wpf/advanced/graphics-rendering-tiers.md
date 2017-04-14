---
title: "Couches de rendu graphiques | Microsoft Docs"
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
  - "couches de rendu graphiques"
  - "graphiques, performances"
  - "graphiques, couches de rendu"
  - "restituer des graphiques"
  - "couches de rendu"
ms.assetid: 08dd1606-02a2-4122-9351-c0afd2ec3a70
caps.latest.revision: 44
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 43
---
# Couches de rendu graphiques
Une couche de rendu définit un niveau des capacités et des performances du matériel graphique pour un périphérique qui exécute une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="graphics_hardware"></a>   
## Matériel graphique  
 Les fonctionnalités du matériel graphique qui impactent le plus les niveaux de la couche de rendu sont les suivantes :  
  
-   **RAM vidéo** La quantité de mémoire vidéo sur le matériel graphique détermine la taille et le nombre de mémoires tampon qui peuvent être utilisées pour la composition de graphiques.  
  
-   **Nuanceur de pixels** Un nuanceur de pixels est une fonction de traitement des graphiques qui calcule les effets pixel par pixel.  En fonction de la résolution des graphiques affichés, il peut y avoir plusieurs millions de pixels à traiter pour chaque frame d'affichage.  
  
-   **Vertex shader** Un vertex shader est une fonction de traitement des graphiques qui effectue des opérations mathématiques sur les données de vertex de l'objet.  
  
-   **Prise en charge de la multitexture** La prise en charge de la multitexture fait référence à la possibilité d'appliquer au moins deux textures distinctes pendant une opération de mélange sur un objet graphique 3D.  Le degré de prise en charge de la multitexture est déterminé par le nombre d'unités de multitexture sur le matériel graphique.  
  
<a name="rendering_tier_definitions"></a>   
## Définitions de couche de rendu  
 Les fonctionnalités du matériel graphique déterminent la fonction de rendu d'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit trois couches de rendu :  
  
-   **Couche de rendu 0** Aucune accélération du matériel graphique.  Toutes les fonctionnalités graphiques utilisent l'accélération logicielle.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est inférieur à la version 9.0.  
  
-   **Couche de rendu 1** Certaines fonctionnalités graphiques utilisent l'accélération matérielle graphique.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 9.0.  
  
-   **Couche de rendu 2** La plupart des caractéristiques graphiques utilisent l'accélération du matériel graphique.  Le niveau de version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est supérieur ou égal à la version 9.0.  
  
 La propriété <xref:System.Windows.Media.RenderCapability.Tier%2A?displayProperty=fullName> vous permet d'extraire la couche de rendu au moment de l'exécution de l'application.  La couche de rendu permet de déterminer si le périphérique prend en charge certaines fonctionnalités graphiques à accélération matérielle.  Votre application peut alors prendre des chemins de code différents au moment de l'exécution selon la couche de rendu prise en charge par le périphérique.  
  
### Couche de rendu 0  
 Une valeur de couche de rendu de 0 signifie qu'il n'y a aucune accélération de matériel vidéo disponible pour l'application sur le périphérique.  À ce niveau de la couche, vous devez supposer que tous les graphiques seront restitués par le logiciel sans accélération matérielle.  Les fonctionnalités de cette couche correspondent à une version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] qui est inférieure à la version 9.0.  
  
### Couche de rendu 1 et couche de rendu 2  
  
> [!NOTE]
>  À partir de .NET Framework 4, la couche de rendu 1 a été redéfinie pour n'inclure que le matériel graphique prenant en charge [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 9.0 ou version ultérieure.  Le matériel graphique prenant en charge [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 7 ou 8 est désormais défini comme la couche de rendu 0.  
  
 Une valeur de couche de rendu de 1 ou de 2 signifie que la plupart des fonctionnalités graphiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utiliseront l'accélération matérielle si les ressources système nécessaires sont disponibles et n'ont pas été épuisées.  Cela correspond à une version [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] qui est ultérieure ou égale à la version 9.0.  
  
 Le tableau suivant indique les différences entre la couche de rendu 1 et la couche de rendu 2 au niveau des spécifications de matériel graphique :  
  
|Fonctionnalité|Couche 1|Couche 2|  
|--------------------|--------------|--------------|  
|Version de [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]|Doit être supérieure ou égale à 9.0.|Doit être supérieure ou égale à 9.0.|  
|RAM vidéo|Doit être supérieure ou égale à 60 Mo.|Doit être supérieure ou égale à 120 Mo.|  
|Nuanceur de pixels|Le niveau de version doit être supérieur ou égal à 2.0.|Le niveau de version doit être supérieur ou égal à 2.0.|  
|Vertex shader|Aucune exigence.|Le niveau de version doit être supérieur ou égal à 2.0.|  
|Unités de multitexture|Aucune exigence.|Le nombre d'unités doit être supérieur ou égal à 4.|  
  
 Les fonctionnalités et fonctions suivantes ne sont pas accélérées par le matériel pour les couches de rendu 1 et 2 :  
  
|Fonctionnalité|Remarques|  
|--------------------|---------------|  
|Rendu 2D|La plupart des types de rendu 2D sont pris en charge.|  
|Rastérisation 3D|La plupart des types de rastérisation 3D sont pris en charge.|  
|Filtrage anisotropique 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tente d'utiliser le filtrage anisotropique lors de l'affichage du contenu 3D.  Le filtrage anisotropique correspond à l'amélioration de la qualité de la texture des surfaces éloignées et en biais par rapport à l'appareil photo.|  
|Mappage MIP 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tente d'utiliser le mappage MIP lors de l'affichage du contenu 3D. Le mappage MIP améliore la qualité du rendu de la texture lorsque celle\-ci occupe un champ plus restreint dans un <xref:System.Windows.Controls.Viewport3D>.|  
|Dégradés radiaux|Même s'il est pris en charge, évitez d'utiliser <xref:System.Windows.Media.RadialGradientBrush> sur les grands objets.|  
|Calculs d'éclairage 3D|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exécute l'éclairage par vertex, ce qui signifie qu'une intensité légère doit être calculée à chaque vertex pour chaque matériel appliqué à un maillage.|  
|Rendu de texte|Le rendu de police de sous\-pixel utilise les nuanceurs de pixels disponibles sur le matériel vidéo.|  
  
 Les fonctionnalités et fonctions suivantes ne sont accélérées par le matériel que pour la couche de rendu 2 :  
  
|Fonctionnalité|Remarques|  
|--------------------|---------------|  
|Anticrénelage 3D|L'anticrénelage 3D est pris en charge uniquement sur les systèmes d'exploitation prenant en charge Windows Display Driver Model \(WDDM\), tels que [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] et [!INCLUDE[win7](../../../../includes/win7-md.md)].|  
  
 Les fonctionnalités et fonctions suivantes n'utilisent **pas** l'accélération matérielle :  
  
|Fonctionnalité|Remarques|  
|--------------------|---------------|  
|Contenu imprimé|Tout le contenu imprimé est restitué à l'aide du pipeline logiciel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Contenu rastérisé qui utilise <xref:System.Windows.Media.Imaging.RenderTargetBitmap>|Tout le contenu restitué à l'aide de la méthode <xref:System.Windows.Media.Imaging.RenderTargetBitmap.Render%2A> de <xref:System.Windows.Media.Imaging.RenderTargetBitmap>.|  
|Contenu en mosaïque qui utilise <xref:System.Windows.Media.TileBrush>|Tout le contenu en mosaïque dans lequel la propriété <xref:System.Windows.Media.TileBrush.TileMode%2A> de <xref:System.Windows.Media.TileBrush> a la valeur <xref:System.Windows.Media.TileMode>.|  
|Surfaces qui dépassent la taille de texture maximale du matériel vidéo|Pour la plupart du matériel vidéo, les grandes surfaces ont une taille de 2 048 x 2 048 ou 4 096 x 4 096 pixels.|  
|Toute opération dont la spécification de RAM vidéo dépasse la mémoire du matériel vidéo|Vous pouvez surveiller l'utilisation de la RAM vidéo par l'application à l'aide de l'outil Perforator compris dans la [WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md) du Kit de développement logiciel \(SDK\) Windows.|  
|Fenêtres superposées|Les fenêtres superposées permettent aux applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de restituer le contenu à l'écran dans une fenêtre non rectangulaire.  Sur les systèmes d'exploitation prenant en charge Windows Display Driver Model \(WDDM\), tels que [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] et [!INCLUDE[win7](../../../../includes/win7-md.md)], les fenêtres superposées sont accélérées par le matériel.  Sur autres systèmes, tels que [!INCLUDE[winxp](../../../../includes/winxp-md.md)], les fenêtres superposées sont restituées par logiciel sans accélération matérielle.<br /><br /> Vous pouvez activer des fenêtres superposées dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en définissant les propriétés <xref:System.Windows.Window> suivantes :<br /><br /> -   <xref:System.Windows.Window.WindowStyle%2A> \= <xref:System.Windows.WindowStyle><br />-   <xref:System.Windows.Window.AllowsTransparency%2A> \= `true`<br />-   <xref:System.Windows.Controls.Control.Background%2A> \= <xref:System.Windows.Media.Brushes.Transparent%2A>|  
  
<a name="other_resources"></a>   
## Autres ressources  
 Les ressources suivantes peuvent vous aider à analyser les caractéristiques de performance de votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Paramètres du Registre pour le rendu des graphiques  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit quatre paramètres du Registre pour contrôler le rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Désactiver l'option d'accélération matérielle**|Spécifie si l'accélération matérielle doit être activée.|  
|**Valeur d'échantillonnage multiple maximale**|Spécifie le degré d'échantillonnage multiple pour l'anticrénelage de contenu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].|  
|**Paramètre de la date du pilote vidéo requis**|Spécifie si le système désactive l'accélération matérielle pour les pilotes commercialisés avant novembre 2004.|  
|**Utiliser l'option du module de rastérisation de référence**|Spécifie si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit utiliser le module de rastérisation de référence.|  
  
 Ces paramètres sont accessibles à tout utilitaire de configuration externe capable de référencer les paramètres du Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Ils peuvent également être créés ou modifiés en accédant directement aux valeurs en utilisant l'Éditeur du Registre [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  Pour plus d'informations, consultez [Paramètres du Registre pour le rendu des graphiques](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md).  
  
### Outils de profilage des performances WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une suite d'outils de profilage des performances qui vous permettent d'analyser le comportement au moment de l'exécution de votre application et de déterminer les types d'optimisations des performances que vous pouvez appliquer.  Le tableau suivant répertorie les outils de profilage des performances qui sont inclus dans l'outil [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)], WPF Performance Suite :  
  
|Outil|Description|  
|-----------|-----------------|  
|Perforator|À utiliser pour analyser le comportement de rendu.|  
|Visual Profiler|À utiliser pour le profilage de l'utilisation des services [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tels que la disposition et la gestion des événements, pour chaque élément de l'arborescence d'éléments visuels.|  
  
 L'outil WPF Performance Suite fournit une vue graphique, très riche des données de performance.  Pour plus d'informations sur les outils de performance WPF, consultez [WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md).  
  
### Outil de diagnostic DirectX  
 L'Outil de diagnostic [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], Dxdiag.exe, est conçu pour vous aider à résoudre les problèmes liés à [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)].  Le dossier d'installation par défaut pour l'Outil de diagnostic [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] est :  
  
 `~\Windows\System32`  
  
 Lorsque vous exécutez l'Outil de diagnostic [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)], la fenêtre principale contient un jeu d'onglets qui vous permettent d'afficher et de diagnostiquer les problèmes liés à [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)].  Par exemple, l'onglet **Système** fournit des informations système à propos de votre ordinateur et spécifie la version de [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] installée sur votre ordinateur.  
  
 ![Capture d'écran : Outil de diagnostic DirectX](../../../../docs/framework/wpf/advanced/media/directxdiagnostictool-01.png "DirectXDiagnosticTool\_01")  
Fenêtre principale de l'Outil de diagnostic DirectX  
  
## Voir aussi  
 <xref:System.Windows.Media.RenderCapability>   
 <xref:System.Windows.Media.RenderOptions>   
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [WPF Performance Suite](../Topic/WPF%20Performance%20Suite.md)   
 [Paramètres du Registre pour le rendu des graphiques](../../../../docs/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings.md)   
 [Conseils et astuces sur les animations](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)