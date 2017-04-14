---
title: "Vue d&#39;ensemble du contr&#244;le MenuStrip (Windows Forms) | Microsoft Docs"
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
  - "MenuStrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "menus, créer"
  - "MenuStrip (contrôle Windows Forms), à propos du contrôle MenuStrip"
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du contr&#244;le MenuStrip (Windows Forms)
Les menus exposent des fonctionnalités aux utilisateurs en stockant des commandes regroupées selon un thème commun.  
  
 Le contrôle <xref:System.Windows.Forms.MenuStrip> est nouveau dans cette version de Visual Studio et dans le .NET Framework.  Grâce à ce contrôle, vous pouvez créer facilement des menus, tels que ceux de Microsoft Office.  
  
 Le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge l'interface MDI \(Multiple\-Document Interface\) ainsi que la fusion de menus, les info\-bulles et le dépassement de capacité.  Vous pouvez améliorer l'utilisation et la lisibilité de vos menus en ajoutant des touches d'accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.  
  
 Le contrôle <xref:System.Windows.Forms.MenuStrip> remplace le contrôle <xref:System.Windows.Forms.MainMenu> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
## Méthodes d'utilisation du contrôle MenuStrip  
 Utilisez le contrôle <xref:System.Windows.Forms.MenuStrip> pour :  
  
-   Créer des menus facilement personnalisés, employés couramment et qui prennent en charge des fonctionnalités avancées d'interface utilisateur et de disposition, telles que l'organisation et l'alignement de texte et d'images, les opérations de glisser\-déplacer, l'interface MDI, le dépassement de capacité et les autres modes d'accès aux commandes de menu.  
  
-   Prendre en charge l'aspect et le comportement généraux du système d'exploitation.  
  
-   Gérer des événements de façon homogène pour tous les conteneurs et les éléments qu'ils contiennent, de la même façon que vous gérez des événements applicables à d'autres contrôles.  
  
 Le tableau suivant indique certaines propriétés particulièrement importantes de <xref:System.Windows.Forms.MenuStrip> et des classes associées.  
  
|Propriété|Description|  
|---------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> utilisé pour afficher une liste de formulaires MDI enfants.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=fullName>|Obtient ou définit la méthode de fusion des menus enfants avec les menus parents dans les applications MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=fullName>|Obtient ou définit la position d'un élément fusionné au sein d'un menu dans les applications MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=fullName>|Obtient ou définit une valeur qui indique si le formulaire est un conteneur pour les formulaires MDI enfants.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtient ou définit une valeur qui précise si des info\-bulles sont affichées pour <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si <xref:System.Windows.Forms.MenuStrip> prend en charge la fonction de dépassement de capacité.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtient ou définit les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtient ou définit une valeur qui indique si les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem> sont affichées en regard de <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Le tableau suivant affiche les classes auxiliaires <xref:System.Windows.Forms.MenuStrip> importantes.  
  
|Classe|Description|  
|------------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Représente une option pouvant être sélectionnée, qui est affichée sur un <xref:System.Windows.Forms.MenuStrip> ou un <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Représente un menu contextuel.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Représente un contrôle qui permet à l'utilisateur de sélectionner un seul élément dans une liste affichée lorsqu'il clique sur <xref:System.Windows.Forms.ToolStripDropDownButton> ou sur un élément de menu de niveau supérieur.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fournit les fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments déroulants lorsque l'utilisateur clique dessus.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>