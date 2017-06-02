---
title: "UI Automation and Microsoft Active Accessibility | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Active Accessibility"
  - "UI Automation, Active Accessibility compared to"
  - "UI Automation, Microsoft Active Accessibility"
  - "Active Accessibility, UI Automation compared to"
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
caps.latest.revision: 24
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 23
---
# UI Automation and Microsoft Active Accessibility
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] était la solution précédemment utilisée pour rendre les applications accessibles.[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] est le nouveau modèle d’accessibilité pour [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] et a été conçu pour répondre aux besoins des produits de technologie d’assistance et des outils de test automatisés.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] offre de nombreuses améliorations par rapport à [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Cette rubrique comprend les principales fonctionnalités d’[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] et explique en quoi ces fonctionnalités diffèrent d’[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## Langages de programmation  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] est basé sur [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] avec la prise en charge des interfaces doubles. Ainsi, il est programmable en C\/C\+\+, en [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)] et dans les langages de script.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] \(y compris la bibliothèque fournisseur côté client pour les contrôles standard\) est écrit en code managé et les applications clientes UI Automation sont programmées plus facilement à l’aide de [!INCLUDE[TLA#tla_vcshrp](../../../includes/tlasharptla-vcshrp-md.md)] ou de [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]. Les fournisseurs UI Automation, qui sont des implémentations d’interface, peuvent être écrits en code managé ou en C\/C\+\+.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## Prise en charge dans Windows Presentation Foundation  
 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] est le nouveau modèle pour la création d’interfaces utilisateur. Les éléments [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] n’assurent pas la prise en charge native d’[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] En revanche, ils prennent en charge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], qui inclut la prise en charge du pontage pour les clients [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Seuls les clients spécifiquement écrits pour [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peuvent tirer pleinement parti des fonctionnalités d’accessibilité de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], comme la prise en charge étendue pour le texte.  
  
<a name="Servers_and_Clients_compare"></a>   
## Serveurs et clients  
 Dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], les serveurs et les clients communiquent directement, en grande partie via l’implémentation d’`IAccessible` par le serveur.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], un service principal se trouve entre le serveur \(appelé fournisseur\) et le client. Ce service appelle les interfaces implémentées par les fournisseurs et fournit des services supplémentaires tels que la génération d’identificateurs d’exécution uniques pour les éléments. Les applications clientes utilisent des fonctions de bibliothèque pour appeler le service [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 Les fournisseurs UI Automation peuvent fournir des informations aux clients [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] et les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] peuvent fournir des informations aux applications clientes UI Automation. Toutefois, comme [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] n’expose pas autant d’informations qu’[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], les deux modèles ne sont pas entièrement compatibles.  
  
<a name="UI_Elements_compare"></a>   
## Éléments de l'interface utilisateur  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] présente les éléments [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] comme une interface `IAccessible` ou comme un identificateur enfant. Il est difficile de comparer deux pointeurs `IAccessible` pour déterminer s’ils font référence au même élément.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], chaque élément est représenté comme un objet <xref:System.Windows.Automation.AutomationElement>. La comparaison s’effectue à l’aide de l’opérateur d’égalité ou de la méthode <xref:System.Windows.Automation.AutomationElement.Equals%2A>, qui comparent tous les deux les identificateurs d’exécution uniques des éléments.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## Arborescences et navigation  
 À l’écran, les éléments d’[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] peuvent être affichés sous forme d’arborescence. Le bureau correspond à la racine, les fenêtres d’application aux enfants immédiats et les éléments des applications à des descendants plus lointains.  
  
 Dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], de nombreux éléments Automation sans importance pour l’utilisateur final sont exposés dans l’arborescence. Les applications clientes doivent examiner tous les éléments pour déterminer les éléments significatifs.  
  
 Les applications clientes UI Automation voient l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] via une vue filtrée. La vue ne contient que les éléments intéressants : ceux qui apportent des informations à l’utilisateur ou qui permettent l’interaction. Des vues prédéfinies contenant uniquement les éléments de contrôle et uniquement les éléments de contenu sont disponibles. En outre, les applications peuvent définir des vues personnalisées.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] simplifie la tâche consistant à décrire l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] à l’utilisateur et à aider l’utilisateur à interagir avec l’application.  
  
 Dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], la navigation entre les éléments peut être spatiale \(par exemple, un déplacement vers l’élément qui se trouve à gauche de l’écran\), logique \(par exemple, un déplacement vers l’élément de menu suivant ou vers l’élément suivant dans l’ordre de tabulation d’une boîte de dialogue\) ou hiérarchique \(par exemple, un déplacement du premier enfant dans un conteneur ou d’un enfant vers son parent\). La navigation hiérarchique est compliquée par le fait que les éléments enfants ne sont pas toujours des objets qui implémentent `IAccessible`.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], tous les éléments d’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sont des objets <xref:System.Windows.Automation.AutomationElement> qui prennent en charge les mêmes fonctionnalités de base. \(Du point de vue du fournisseur, ce sont des objets qui implémentent une interface héritée de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.\) La navigation est principalement hiérarchique : des parents aux enfants et d’un frère à un autre. \(La navigation entre frères a un élément logique, car elle peut suivre l’ordre de tabulation\). Vous pouvez naviguer à partir de n’importe quel point de départ à l’aide d’une vue filtrée de l’arborescence, en utilisant la classe <xref:System.Windows.Automation.TreeWalker>. Vous pouvez également naviguer vers des enfants ou des descendants particuliers à l’aide de <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> et <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Par exemple, il est très simple de récupérer tous les éléments d’une boîte de dialogue qui prennent en charge un modèle de contrôle spécifié.  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], la navigation est plus cohérente que dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Certains éléments tels que les listes déroulantes et les fenêtres indépendantes apparaissent deux fois dans l’arborescence [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] et le fait de naviguer depuis ces éléments peut entraîner des résultats inattendus. Il est en fait impossible d’implémenter correctement [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] pour un contrôle Rebar.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permet la définition de l’état de parent et le repositionnement, afin qu’un élément puisse être placé n’importe où dans l’arborescence en dépit de la hiérarchie imposée par la propriété des fenêtres.  
  
<a name="Roles_and_Control_Types"></a>   
## Rôles et types de contrôle  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] utilise la propriété `accRole` \(`IAccessible::get_actRole`\) pour récupérer une description du rôle de l’élément dans l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], comme ROLE\_SYSTEM\_SLIDER ou ROLE\_SYSTEM\_MENUITEM. Le rôle d’un élément est l’indice principal pour connaître ses fonctionnalités disponibles. L’interaction avec un contrôle est réalisée à l’aide de méthodes fixes telles que `IAccessible::accSelect` et `IAccessible::accDoDefaultAction`. L’interaction entre l’application cliente et l’[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] se limite à ce qui peut s’effectuer via `IAccessible`.  
  
 En revanche, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] découple en grande partie le type de contrôle de l’élément \(décrit par la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>\) de ses fonctionnalités attendues. Les fonctionnalités sont déterminées par les modèles de contrôle pris en charge par le fournisseur via son implémentation d’interfaces spécialisées. Les modèles de contrôle peuvent être combinés pour décrire l’ensemble des fonctionnalités prises en charge par un élément [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] particulier. Certains fournisseurs sont tenus de prendre en charge un modèle de contrôle particulier. Par exemple, le fournisseur d’une case à cocher doit prendre en charge le modèle de contrôle Toggle. D’autres fournisseurs doivent prendre en charge un ou plusieurs éléments d’un ensemble de modèles de contrôle. Par exemple, un bouton doit prendre en charge Toggle ou Invoke. D’autres encore ne prennent en charge aucun modèle de contrôle du tout. Par exemple, un volet qui ne peut pas être déplacé, redimensionné ni ancré n’a pas de modèle de contrôle.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prend en charge des contrôles personnalisés, identifiés par la propriété <xref:System.Windows.Automation.ControlType.Custom> et pouvant être décrits par la propriété <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>.  
  
 Le tableau suivant montre la correspondance entre les rôles [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] et les types de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Rôle [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|Type de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|ROLE\_SYSTEM\_PUSHBUTTON|Bouton|  
|ROLE\_SYSTEM\_CLIENT|Calendrier|  
|ROLE\_SYSTEM\_CHECKBUTTON|Case à cocher|  
|ROLE\_SYSTEM\_COMBOBOX|Zone de liste modifiable|  
|ROLE\_SYSTEM\_CLIENT|Personnalisé|  
|ROLE\_SYSTEM\_LIST|Grille de données|  
|ROLE\_SYSTEM\_LISTITEM|Élément de données|  
|ROLE\_SYSTEM\_DOCUMENT|Document|  
|ROLE\_SYSTEM\_TEXT|Modifier|  
|ROLE\_SYSTEM\_GROUPING|Regrouper|  
|ROLE\_SYSTEM\_LIST|En\-tête|  
|ROLE\_SYSTEM\_COLUMNHEADER|Élément d’en\-tête|  
|ROLE\_SYSTEM\_LINK|Lien hypertexte|  
|ROLE\_SYSTEM\_GRAPHIC|Image|  
|ROLE\_SYSTEM\_LIST|Liste|  
|ROLE\_SYSTEM\_LISTITEM|Élément de liste|  
|ROLE\_SYSTEM\_MENUPOPUP|Menu|  
|ROLE\_SYSTEM\_MENUBAR|Barre de menus|  
|ROLE\_SYSTEM\_MENUITEM|Menu Item|  
|ROLE\_SYSTEM\_PANE|Volet|  
|ROLE\_SYSTEM\_PROGRESSBAR|Barre de progression|  
|ROLE\_SYSTEM\_RADIOBUTTON|Case d’option|  
|ROLE\_SYSTEM\_SCROLLBAR|Barre de défilement|  
|ROLE\_SYSTEM\_SEPARATOR|Séparateur|  
|ROLE\_SYSTEM\_SLIDER|Curseur|  
|ROLE\_SYSTEM\_SPINBUTTON|Spinner|  
|ROLE\_SYSTEM\_SPLITBUTTON|Bouton Fractionner|  
|ROLE\_SYSTEM\_STATUSBAR|Barre d'état|  
|ROLE\_SYSTEM\_PAGETABLIST|Onglet|  
|ROLE\_SYSTEM\_PAGETAB|Élément d’onglet|  
|ROLE\_SYSTEM\_TABLE|Table|  
|ROLE\_SYSTEM\_STATICTEXT|Texte|  
|ROLE\_SYSTEM\_INDICATOR|Thumb|  
|ROLE\_SYSTEM\_TITLEBAR|Barre de titre|  
|ROLE\_SYSTEM\_TOOLBAR|Barre d’outils|  
|ROLE\_SYSTEM\_TOOLTIP|Info\-bulle|  
|ROLE\_SYSTEM\_OUTLINE|Arborescence|  
|ROLE\_SYSTEM\_OUTLINEITEM|Élément d’arborescence|  
|ROLE\_SYSTEM\_WINDOW|Fenêtre|  
  
 Pour plus d’informations sur les différents types de contrôle, consultez [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## États et propriétés  
 Dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], les éléments prennent en charge un ensemble commun de propriétés et certaines propriétés \(telles que `accState`\) doivent décrire des aspects très différents, selon le rôle de l’élément. Les serveurs doivent implémenter toutes les méthodes de `IAccessible` qui retournent une propriété, y compris celles qui ne sont pas pertinentes pour l’élément.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] définit de nombreuses autres propriétés, dont certaines correspondent aux états dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Certaines sont communes à tous les éléments, tandis que d’autres sont spécifiques aux types de contrôle et aux motifs de contrôle. Les propriétés se distinguent par des identificateurs uniques et la plupart des propriétés peuvent être récupérées à l’aide d’une méthode unique, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. De nombreuses propriétés sont également facilement récupérables à partir des accesseurs de propriété <xref:System.Windows.Automation.AutomationElement.Current%2A> et <xref:System.Windows.Automation.AutomationElement.Cached%2A>.  
  
 Un fournisseur UI Automation n’est pas tenu d’implémenter des propriétés non pertinentes et peut simplement retourner une valeur `null` pour toutes les propriétés qu’il ne prend pas en charge. Le service principal [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] peut également obtenir des propriétés auprès du fournisseur de fenêtres par défaut. Ces propriétés sont fusionnées avec les propriétés implémentées explicitement par le fournisseur.  
  
 Outre la prise en charge de nombreuses autres propriétés, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fournit de meilleures performances en autorisant la récupération de plusieurs propriétés via un seul appel interprocessus.  
  
 Le tableau suivant montre la correspondance entre les propriétés dans les deux modèles.  
  
|Accesseur de propriété [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|ID de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Remarques|  
|----------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|---------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> ou <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|Si les deux sont présents, `AccessKeyProperty` est prioritaire.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>|``|  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Pour la correspondance entre les rôles et les types de contrôle, consultez le tableau précédent.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName>|Valide uniquement pour les types de contrôle qui prennent en charge ValuePattern ou RangeValuePattern. Les valeurs RangeValue sont normalisées de 0 à 100 pour être cohérentes avec le comportement MSAA. Les éléments de valeur utilisent une chaîne.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Non pris en charge dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` n’avait pas de spécification claire dans MSAA ; les fournisseurs ont donc placé différentes informations dans cette propriété.|  
|`get_accHelpTopic`|Non pris en charge dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Le tableau suivant montre quelles propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] correspondent aux constantes d’état [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
|État [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|Propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Déclenche un changement d’état ?|  
|----------------------------------------------------------------------|-------------------------------------------------------------------------------------|--------------------------------------|  
|STATE\_SYSTEM\_CHECKED|Pour une case à cocher, <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Pour une case d’option, <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE\_SYSTEM\_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> \= <xref:System.Windows.Automation.ExpandCollapseState> ou <xref:System.Windows.Automation.ExpandCollapseState>|Y|  
|STATE\_SYSTEM\_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE\_SYSTEM\_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE\_SYSTEM\_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> pour des éléments de menu|N|  
|STATE\_SYSTEM\_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True et <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> entraîne <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE\_SYSTEM\_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> \=<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE\_SYSTEM\_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> \= <xref:System.Windows.Automation.ToggleState>|N|  
|STATE\_SYSTEM\_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE\_SYSTEM\_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE\_SYSTEM\_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> \= True|N|  
|STATE\_SYSTEM\_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE\_SYSTEM\_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=fullName> et <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=fullName>|N|  
|STATE\_SYSTEM\_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> est pris en charge|N|  
|STATE\_SYSTEM\_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE\_SYSTEM\_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE\_SYSTEM\_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 Les états suivants n’ont pas été implémentés par la plupart des serveurs de contrôle [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ou n’ont aucun équivalent dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|État [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|Notes|  
|----------------------------------------------------------------------|-----------|  
|STATE\_SYSTEM\_BUSY|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE\_SYSTEM\_DEFAULT|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE\_SYSTEM\_ANIMATED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE\_SYSTEM\_EXTSELECTABLE|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_MARQUEED|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_SELFVOICING|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_TRAVERSED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE\_SYSTEM\_ALERT\_HIGH|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_ALERT\_MEDIUM|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_ALERT\_LOW|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_FLOATING|Non largement implémenté par les serveurs [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]|  
|STATE\_SYSTEM\_HOTTRACKED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE\_SYSTEM\_PRESSED|Non disponible dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Pour obtenir la liste complète des identificateurs de propriété [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## Événements  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], contrairement à [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], le mécanisme d’événement ne repose pas sur le routage des événements Windows \(étroitement lié aux handles de fenêtre\) et ne requiert pas l’application cliente pour pouvoir installer des raccordements. Les abonnements aux événements peuvent être ajustés non seulement à des événements particuliers mais également à des parties spécifiques de l’arborescence. Les fournisseurs peuvent également ajuster leur déclenchement d’événements en assurant le suivi des événements qui sont écoutés.  
  
 Il est également plus facile pour les clients de récupérer les éléments qui déclenchent des événements, car ils sont passés directement au rappel d’événement. Les propriétés de l’élément sont automatiquement prérécupérées si une requête de cache était active quand le client s’est abonné à l’événement.  
  
 Le tableau suivant montre la correspondance entre les WinEvents [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] et les événements [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|WinEvent|Identificateur d’événement [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|--------------|------------------------------------------------------------------------------------------------------|  
|EVENT\_OBJECT\_ACCELERATORCHANGE|Modification de la propriété <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|  
|EVENT\_OBJECT\_CONTENTSCROLLED|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> sur les barres de défilement associées|  
|EVENT\_OBJECT\_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_DEFACTIONCHANGE|Aucun équivalent|  
|EVENT\_OBJECT\_DESCRIPTIONCHANGE|Pas d’équivalent exact. Éventuelle modification de la propriété <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> ou <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|  
|EVENT\_OBJECT\_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_OBJECT\_HELPCHANGE|Modification de <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|  
|EVENT\_OBJECT\_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_LOCATIONCHANGE|Modification de la propriété <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT\_OBJECT\_NAMECHANGE|Modification de la propriété <xref:System.Windows.Automation.AutomationElement.NameProperty>|  
|EVENT\_OBJECT\_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_REORDER|Pas utilisé de manière cohérente dans [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Aucun événement directement correspondant n’est défini dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT\_OBJECT\_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT\_OBJECT\_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT\_OBJECT\_SELECTIONWITHIN|Aucun équivalent|  
|EVENT\_OBJECT\_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT\_OBJECT\_STATECHANGE|Différents événements de modification de propriété|  
|EVENT\_OBJECT\_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=fullName> et <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=fullName> modifiés|  
|EVENT\_SYSTEM\_ALERT|Aucun équivalent|  
|EVENT\_SYSTEM\_CAPTUREEND|Aucun équivalent|  
|EVENT\_SYSTEM\_CAPTURESTART|Aucun équivalent|  
|EVENT\_SYSTEM\_CONTEXTHELPEND|Aucun équivalent|  
|EVENT\_SYSTEM\_CONTEXTHELPSTART|Aucun équivalent|  
|EVENT\_SYSTEM\_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT\_SYSTEM\_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT\_SYSTEM\_DRAGDROPEND|Aucun équivalent|  
|EVENT\_SYSTEM\_DRAGDROPSTART|Aucun équivalent|  
|EVENT\_SYSTEM\_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT\_SYSTEM\_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT\_SYSTEM\_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT\_SYSTEM\_MINIMIZEEND|Modification de la propriété <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT\_SYSTEM\_MINIMIZESTART|Modification de la propriété <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|EVENT\_SYSTEM\_MOVESIZEEND|Modification de la propriété <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT\_SYSTEM\_MOVESIZESTART|Modification de la propriété <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|  
|EVENT\_SYSTEM\_SCROLLINGEND|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|EVENT\_SYSTEM\_SCROLLINGSTART|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> ou <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|EVENT\_SYSTEM\_SOUND|Aucun équivalent|  
|EVENT\_SYSTEM\_SWITCHEND|Aucun équivalent, mais un événement <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> signale qu’une nouvelle application a reçu le focus|  
|EVENT\_SYSTEM\_SWITCHSTART|Aucun équivalent|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>|  
|Aucun équivalent|Modification de la propriété <xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>|  
|Aucun équivalent|Événement <xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>|  
|Aucun équivalent|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## Sécurité  
 Certains scénarios de personnalisation `IAccessible` nécessitent l’encapsulation d’un `IAccessible` de base et l’appel via celui\-ci. Cela a des implications en matière de sécurité, car un composant avec un niveau de confiance partiel ne doit pas être un intermédiaire sur un chemin de code.  
  
 Le modèle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] supprime le besoin qu’ont les fournisseurs d’appeler via un autre code de fournisseur. Le service principal [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] effectue toutes les opérations d’agrégation nécessaires.  
  
## Voir aussi  
 [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md)