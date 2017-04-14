---
title: "Interop&#233;rabilit&#233; WPF et Windows&#160;Forms | Microsoft Docs"
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
  - "contrôle hybride (interopérabilité WPF)"
  - "interopérabilité (WPF), Windows Forms"
  - "interopérabilité imbriquée (WPF)"
  - "Windows Forms (WPF), interopérabilité avec"
  - "Windows Forms, interopérabilité WPF"
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Interop&#233;rabilit&#233; WPF et Windows&#160;Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] présentent deux architectures différentes pour créer des interfaces d'applications.  L'espace de noms <xref:System.Windows.Forms.Integration?displayProperty=fullName> fournit des classes permettant des scénarios d'interopérabilité communs.  Les deux principales classes qui implémentent les fonctions d'interopérabilité sont <xref:System.Windows.Forms.Integration.WindowsFormsHost> et <xref:System.Windows.Forms.Integration.ElementHost>.  Cette rubrique décrit les scénarios d'interopérabilité pris en charge et non pris en charge.  
  
> [!NOTE]
>  Une attention particulière est accordée au scénario de *contrôle hybride*.  Un contrôle hybride possède un contrôle d'une technologie imbriqué dans un contrôle d'une autre technologie.  Il est également appelé *interopérabilité imbriquée*.  Un *contrôle hybride à plusieurs niveaux* possède plusieurs niveaux d'imbrication de contrôle hybride.  Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui contient un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], contenant un autre contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], est un exemple d'interopérabilité imbriquée à plusieurs niveaux.  Les contrôles hybrides à plusieurs niveaux ne sont pas pris en charge.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## Hébergement des contrôles Windows Forms dans WPF  
 Les scénarios d'interopérabilité suivants sont pris en charge lorsqu'un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] héberge un contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] :  
  
-   Le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut héberger un ou plusieurs contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l'aide de XAML.  
  
-   Il peut héberger un ou plusieurs contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l'aide de code.  
  
-   Il peut héberger les contrôles conteneur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui contiennent d'autres contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Il peut héberger un formulaire maître\/détail avec un maître [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des détails [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Il peut héberger un formulaire maître\/détail avec un maître [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des détails [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Il peut héberger un ou plusieurs contrôles [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)].  
  
-   Il peut héberger un ou plusieurs contrôles composites.  
  
-   Il peut héberger des contrôles hybrides à l'aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   Il peut héberger des contrôles hybrides à l'aide de code.  
  
### Prise en charge de la disposition  
 La liste suivante décrit les limitations connues lorsque l'élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> essaie d'intégrer son contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans le système de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Dans certains cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas être redimensionnés ou peuvent l'être uniquement à des dimensions spécifiques.  Par exemple, un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> prend en charge la seule hauteur définie par la taille de police du contrôle.  Dans une disposition dynamique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui suppose que les éléments peuvent être étirés verticalement, un contrôle <xref:System.Windows.Forms.ComboBox> hébergé ne s'étirera pas comme prévu.  
  
-   Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne peuvent pas subir de rotation ni d'inclinaison.  Par exemple, lorsque vous faites pivoter l'interface utilisateur de 90 degrés, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés conservent leur position droite.  
  
-   Dans la plupart des cas, les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la mise à l'échelle proportionnelle.  Même si les dimensions générales du contrôle sont mises à l'échelle, les contrôles enfants et les éléments de composant du contrôle peuvent ne pas être redimensionnés comme prévu.  Cette limitation dépend de la prise en charge de la mise à l'échelle de chaque contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous pouvez modifier l'ordre de plan des éléments afin d'en contrôler la superposition.  Un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est dessiné dans un handle de fenêtre \(HWND\) séparé ; ainsi, il apparaît toujours au\-dessus des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prennent en charge la mise à l'échelle automatique en fonction de la taille de police.  Dans une interface utilisateur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la modification de la taille de police n'entraîne pas de redimensionnement de la disposition entière, bien que chaque élément individuel puisse être redimensionné dynamiquement.  
  
### Propriétés ambiantes  
 Certaines propriétés ambiantes des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] disposent d'équivalents [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  Ces propriétés ambiantes sont propagées par les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés et exposées comme propriétés publiques sur le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> convertit chaque propriété ambiante [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en son équivalent [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Pour plus d'informations, consultez [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### Comportement  
 Le tableau suivant décrit le comportement d'interopérabilité.  
  
|Comportement|Pris en charge|Non pris en charge|  
|------------------|--------------------|------------------------|  
|Transparence|Le rendu d'un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] prend en charge la transparence.  L'arrière\-plan du contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parent peut devenir l'arrière\-plan de contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés.|Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ne prennent pas en charge la transparence.  Par exemple, les contrôles <xref:System.Windows.Forms.TextBox> et <xref:System.Windows.Forms.ComboBox> ne sont pas transparents lorsqu'ils sont hébergés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Tabulation|L'ordre de tabulation des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés est identique à ceux des contrôles hébergés dans une application [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> La tabulation à partir d'un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vers un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l'aide des touches TAB et MAJ\+TAB fonctionne normalement.<br /><br /> Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dont la propriété <xref:System.Windows.Forms.Control.TabStop%2A> a la valeur `false` ne reçoivent pas le focus lorsque l'utilisateur utilise la tabulation entre les contrôles.<br /><br /> -   Chaque contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> dispose d'une valeur <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>, qui détermine à quel moment ce contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> recevra le focus.<br />-   Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] figurant dans un conteneur <xref:System.Windows.Forms.Integration.WindowsFormsHost> respectent l'ordre spécifié par la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>.  La tabulation à partir du dernier index de tabulation donne le focus au contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivant, s'il existe.  S'il n'existe aucun autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant recevoir le focus, la tabulation retourne au premier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l'ordre de tabulation.<br />-   Les valeurs <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> de contrôles figurant dans <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont associées aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] frères contenus dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-   La tabulation respecte le comportement spécifique aux contrôles.  Par exemple, le fait d'appuyer sur la touche TAB dans un contrôle <xref:System.Windows.Forms.TextBox> dont la propriété <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> a la valeur `true` entraîne l'ajout d'une tabulation dans la zone de texte plutôt que le déplacement du focus.|Non applicable.|  
|Navigation à l'aide des touches de direction|-   La navigation à l'aide des touches de direction dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> est identique à la navigation dans un contrôle conteneur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ordinaire : les touches HAUT et GAUCHE permettent de sélectionner le contrôle précédent et les touches BAS et DROITE permettent de sélectionner le contrôle suivant.<br />-   Les touches HAUT et GAUCHE à partir du premier contrôle contenu dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> permettent d'effectuer la même action que le raccourci clavier MAJ\+TAB.  S'il existe un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant prendre le focus, le focus est déplacé à l'extérieur du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Ce comportement diffère du comportement <xref:System.Windows.Forms.ContainerControl> standard car aucun déplacement vers le dernier contrôle ne se produit.  S'il n'existe aucun autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant recevoir le focus, le focus est déplacé vers le dernier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l'ordre de tabulation.<br />-   Les touches BAS et DROITE à partir du dernier contrôle contenu dans le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> permettent d'effectuer la même action que la touche TAB.  S'il existe un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant prendre le focus, le focus est déplacé à l'extérieur du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  Ce comportement diffère du comportement <xref:System.Windows.Forms.ContainerControl> standard car aucun déplacement vers le premier contrôle ne se produit.  S'il n'existe aucun autre contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pouvant recevoir le focus, le focus est déplacé vers le premier contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans l'ordre de tabulation.|Non applicable.|  
|Accélérateurs|Les accélérateurs fonctionnent normalement, sauf si la mention Non pris en charge figure dans la colonne.|Les accélérateurs en double entre les technologies ne fonctionnent pas comme les accélérateurs ordinaires en double.  Si un accélérateur est dupliqué entre des technologies, avec au moins un sur un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et l'autre sur un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] reçoit toujours l'accélérateur.  Le focus n'est pas basculé entre les contrôles lorsque l'accélérateur en double est utilisé.|  
|Touches de raccourci|Les touches de raccourci fonctionnent normalement, sauf si la mention Non pris en charge figure dans la colonne.|-   Les touches de raccourci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] gérées lors de la phase de prétraitement ont toujours priorité sur les touches de raccourci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Par exemple, si vous disposez d'un contrôle <xref:System.Windows.Forms.ToolStrip> avec les touches de raccourci CTRL\+S définies, et qu'une commande [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est liée à CTRL\+S, le gestionnaire de contrôle <xref:System.Windows.Forms.ToolStrip> est toujours appelé en premier, sans tenir compte du focus.<br />-   Les touches de raccourci [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] gérées par l'événement <xref:System.Windows.Forms.Control.KeyDown> sont traitées en dernier dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Vous pouvez éviter ce comportement en substituant la méthode <xref:System.Windows.Forms.Control.IsInputKey%2A> du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou en gérant l'événement <xref:System.Windows.Forms.Control.PreviewKeyDown>.  Retournez `true` à partir de la méthode <xref:System.Windows.Forms.Control.IsInputKey%2A>, ou affectez `true` à la propriété <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=fullName> dans votre gestionnaire d'événements <xref:System.Windows.Forms.Control.PreviewKeyDown>.|  
|AcceptsReturn, AcceptsTab, et autre comportement spécifique aux contrôles|Les propriétés qui modifient le comportement par défaut du clavier fonctionnent normalement, en supposant que le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se substitue à la méthode <xref:System.Windows.Forms.Control.IsInputKey%2A> pour retourner `true`.|Les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] qui modifient le comportement par défaut du clavier en gérant l'événement <xref:System.Windows.Forms.Control.KeyDown> sont traités en dernier dans le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé.  Étant donné que ces contrôles sont traités en dernier, leur comportement peut être inattendu.|  
|Événements Enter et Leave|Lorsque le focus n'est pas donné au contrôle <xref:System.Windows.Forms.Integration.ElementHost> conteneur, les événements Enter et Leave sont déclenchés si le focus est modifié dans un seul contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|Les événements Enter et Leave ne sont pas déclenchés lorsque la modification suivante de focus se produit :<br /><br /> -   De l'intérieur vers l'extérieur d'un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-   De l'extérieur vers l'intérieur d'un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> .<br />-   À l'extérieur d'un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-   D'un contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé dans un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> vers un contrôle <xref:System.Windows.Forms.Integration.ElementHost> contrôle hébergé dans le même <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supposent l'utilisation d'un modèle concurrentiel monothread.  Lors du débogage, les appels aux objets d'infrastructure d'autres threads lèvent une exception pour faire appliquer ces spécifications.|  
|Sécurité|Tous les scénarios d'interopérabilité nécessitent une confiance totale.|Aucun scénario d'interopérabilité n'est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d'accessibilité sont pris en charge.  Les produits de technologie d'assistance fonctionnent correctement s'ils sont utilisés pour des applications hybrides qui contiennent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Presse\-papiers|Toutes les opérations de Presse\-papiers fonctionnent normalement.  Notamment les opérations couper\-coller entre les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Fonctionnalité glisser\-déplacer|Toutes les opérations glisser\-déplacer fonctionnent normalement.  Notamment les opérations glisser\-déplacer entre les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## Hébergement des contrôles WPF dans les Windows Forms  
 Les scénarios d'interopérabilité suivants sont pris en charge lorsqu'un contrôle [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] héberge un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
-   Hébergement d'un ou plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l'aide de code.  
  
-   Association d'une feuille de propriétés et d'un ou plusieurs contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés.  
  
-   Hébergement d'une ou plusieurs pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un formulaire.  
  
-   Démarrage d'une fenêtre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Hébergement d'un formulaire maître\/détail avec un maître [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des détails [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   Hébergement d'un formulaire maître\/détail avec un maître [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et des détails [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
-   Hébergement de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personnalisés.  
  
-   Hébergement de contrôles hybrides.  
  
### Propriétés ambiantes  
 Certaines propriétés ambiantes des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] disposent d'équivalents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Ces propriétés ambiantes sont propagées par les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés et exposées comme propriétés publiques sur le contrôle <xref:System.Windows.Forms.Integration.ElementHost>.  Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> convertit chaque propriété ambiante [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] en son équivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Pour plus d'informations, consultez [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### Comportement  
 Le tableau suivant décrit le comportement d'interopérabilité.  
  
|Comportement|Pris en charge|Non pris en charge|  
|------------------|--------------------|------------------------|  
|Transparence|Le rendu d'un contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la transparence.  L'arrière\-plan du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] parent peut devenir l'arrière\-plan de contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergés.|Non applicable.|  
|Multithreading|Tous les types de multithreading sont pris en charge.|Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supposent l'utilisation d'un modèle concurrentiel monothread.  Lors du débogage, les appels aux objets d'infrastructure d'autres threads lèvent une exception pour faire appliquer ces spécifications.|  
|Sécurité|Tous les scénarios d'interopérabilité nécessitent une confiance totale.|Aucun scénario d'interopérabilité n'est autorisé avec une confiance partielle.|  
|Accessibilité|Tous les scénarios d'accessibilité sont pris en charge.  Les produits de technologie d'assistance fonctionnent correctement s'ils sont utilisés pour des applications hybrides qui contiennent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et des contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Presse\-papiers|Toutes les opérations de Presse\-papiers fonctionnent normalement.  Notamment les opérations couper\-coller entre les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
|Fonctionnalité glisser\-déplacer|Toutes les opérations glisser\-déplacer fonctionnent normalement.  Notamment les opérations glisser\-déplacer entre les contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Non applicable.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [Procédure pas à pas : hébergement d'un contrôle composite WPF dans les Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [Mappage de propriétés Windows Forms et WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)