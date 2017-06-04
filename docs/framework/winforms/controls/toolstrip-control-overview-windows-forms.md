---
title: "Vue d&#39;ensemble du contr&#244;le ToolStrip (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Toolstrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "barres d'outils (Windows Forms)"
  - "barres d'outils (Windows Forms), nouveautés dans les Windows Forms"
  - "ToolStrip (contrôle Windows Forms), à propos du composant ToolStrip"
  - "nouveautés (Windows Forms), barres d'outils"
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Vue d&#39;ensemble du contr&#244;le ToolStrip (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.ToolStrip> et ses classes associées fournissent une infrastructure commune pour combiner les éléments de l'interface utilisateur en barres d'outils, barres d'état et menus.  Les contrôles <xref:System.Windows.Forms.ToolStrip> facilitent la conception grâce notamment à l'activation et à la modification sur place, à la disposition personnalisée et au rafting, qui permet aux barres d'outils de partager l'espace horizontal ou vertical.  
  
 Bien que <xref:System.Windows.Forms.ToolStrip> remplace le contrôle des versions antérieures \(et lui ajoute des fonctionnalités\), <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
## Fonctionnalités des contrôles ToolStrip  
 Utilisez le contrôle <xref:System.Windows.Forms.ToolStrip> pour :  
  
-   Présenter une interface utilisateur commune entre les conteneurs.  
  
-   Créer des barres d'outils facilement personnalisées, employées couramment et qui prennent en charge des fonctionnalités avancées d'interface utilisateur et de disposition \(telles que l'ancrage, le rafting, les boutons avec texte et images, les contrôles et boutons déroulants, les boutons de dépassement de capacité et la réorganisation au moment de l'exécution des éléments <xref:System.Windows.Forms.ToolStrip>\).  
  
-   Prendre en charge le dépassement de capacité et le reclassement des éléments au moment de l'exécution.  La fonction de dépassement de capacité déplace des éléments vers un menu déroulant lorsqu'il n'y a pas assez de place pour les afficher dans un <xref:System.Windows.Forms.ToolStrip>.  
  
-   Prendre en charge l'aspect et le comportement généraux du système d'exploitation par le biais d'un modèle de rendu commun.  
  
-   Gérer des événements de façon homogène pour tous les conteneurs et les éléments qu'ils contiennent, de la même façon que vous gérez des événements applicables à d'autres contrôles.  
  
-   Faire glisser les éléments d'un <xref:System.Windows.Forms.ToolStrip> vers un autre ou au sein d'un <xref:System.Windows.Forms.ToolStrip>.  
  
-   Créer des contrôles déroulants et des éditeurs de types munis d'une interface utilisateur avec des présentations avancées dans <xref:System.Windows.Forms.ToolStripDropDown>.  
  
 Utilisez la classe <xref:System.Windows.Forms.ToolStripControlHost> pour utiliser d'autres contrôles sur <xref:System.Windows.Forms.ToolStrip> et bénéficier des fonctionnalités <xref:System.Windows.Forms.ToolStrip> pour ces contrôles.  
  
 Vous pouvez étendre les fonctionnalités et modifier l'aspect et le comportement en utilisant <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer> et <xref:System.Windows.Forms.ToolStripManager> avec les énumérations <xref:System.Windows.Forms.ToolStripRenderMode> et <xref:System.Windows.Forms.ToolStripManagerRenderMode>.  
  
 Le contrôle <xref:System.Windows.Forms.ToolStrip> est hautement configurable et extensible, et fournit un nombre élevé de propriétés, de méthodes et d'événements qui permettent de personnaliser l'aspect et le comportement.  Certains des membres les plus importants figurent ci\-après :  
  
### Membres ToolStrip importants  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|Obtient ou définit le bord du conteneur parent auquel <xref:System.Windows.Forms.ToolStrip> est ancré.|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|Obtient ou définit une valeur qui indique si des opérations de glisser\-déplacer et de réorganisation d'éléments sont effectuées en privé par la classe <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|Obtient ou définit une valeur qui indique comment <xref:System.Windows.Forms.ToolStrip> expose ses éléments.|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|Obtient ou définit si <xref:System.Windows.Forms.ToolStripItem> est attaché à <xref:System.Windows.Forms.ToolStrip> ou à <xref:System.Windows.Forms.ToolStripOverflowButton>, ou peut flotter entre les deux.|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|Obtient une valeur qui indique si <xref:System.Windows.Forms.ToolStripItem> affiche d'autres éléments dans une liste déroulante en cas de clic sur <xref:System.Windows.Forms.ToolStripItem>.|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|Obtient <xref:System.Windows.Forms.ToolStripItem>, qui correspond au bouton de dépassement de capacité pour <xref:System.Windows.Forms.ToolStrip> avec dépassement de capacité activé.|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|Obtient ou définit un <xref:System.Windows.Forms.ToolStripRenderer> utilisé pour personnaliser le comportement et l'apparence de <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|Obtient ou définit les styles de peinture à appliquer à <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|Déclenché en cas de modification de la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A>.|  
  
 La souplesse du contrôle <xref:System.Windows.Forms.ToolStrip> s'obtient grâce à l'utilisation de plusieurs classes auxiliaires.  Vous trouverez ci\-dessous certaines des plus importantes :  
  
### Classes auxiliaires ToolStrip importantes  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|Remplace la classe <xref:System.Windows.Forms.MainMenu> et lui ajoute des fonctionnalités.|  
|<xref:System.Windows.Forms.StatusStrip>|Remplace la classe <xref:System.Windows.Forms.StatusBar> et lui ajoute des fonctionnalités.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Remplace la classe <xref:System.Windows.Forms.ContextMenu> et lui ajoute des fonctionnalités.|  
|<xref:System.Windows.Forms.ToolStripItem>|Classe de base abstraite qui gère les événements et la disposition de tous les éléments qu'un contrôle <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost> ou <xref:System.Windows.Forms.ToolStripDropDown> peut contenir.|  
|<xref:System.Windows.Forms.ToolStripContainer>|Fournit un conteneur avec un panneau sur chaque côté du formulaire, dans lequel les contrôles peuvent être organisés de plusieurs façons.|  
|<xref:System.Windows.Forms.ToolStripRenderer>|Gère la fonctionnalité de peinture pour les objets <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|Permet d'obtenir un aspect de style Microsoft Office.|  
|<xref:System.Windows.Forms.ToolStripManager>|Contrôle <xref:System.Windows.Forms.ToolStrip> le rendu et le rafting et la fusion des objets <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu> et <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|Spécifie le style de peinture \(personnalisé, Windows XP ou Microsoft Office Professional\) appliqué à plusieurs objets <xref:System.Windows.Forms.ToolStrip> contenus dans un formulaire.|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|Spécifie le style de peinture \(personnalisé, Windows XP ou Microsoft Office Professional\) appliqué à un objet <xref:System.Windows.Forms.ToolStrip> contenu dans un formulaire.|  
|<xref:System.Windows.Forms.ToolStripControlHost>|Héberge d'autres contrôles qui ne sont pas spécifiquement des contrôles <xref:System.Windows.Forms.ToolStrip>, mais pour lesquels vous souhaitez utiliser les fonctionnalités <xref:System.Windows.Forms.ToolStrip>.|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|Spécifie si un <xref:System.Windows.Forms.ToolStripItem> sera exposé sur le <xref:System.Windows.Forms.ToolStrip> principal, sur le <xref:System.Windows.Forms.ToolStrip> de dépassement de capacité, ou encore sur aucun des deux.|  
  
 Pour plus d'informations, consultez [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) et [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>