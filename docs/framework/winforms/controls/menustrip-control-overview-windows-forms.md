---
title: "Vue d'ensemble du contrôle MenuStrip (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb27503fffc798b644f95fd213f8f23bdb3e228a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="menustrip-control-overview-windows-forms"></a>Vue d'ensemble du contrôle MenuStrip (Windows Forms)
Les menus exposent des fonctionnalités à vos utilisateurs en maintenant les commandes regroupées par un thème commun.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle est nouveau dans cette version de Visual Studio et .NET Framework. Avec le contrôle, vous pouvez créer facilement des menus tels que ceux de Microsoft Office.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle prend en charge l’interface multidocument (MDI) et la fusion de menus, les info-bulles, les dépassement de capacité. Vous pouvez améliorer la facilité d’utilisation et la lisibilité de vos menus en ajoutant des touches d’accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.  
  
 Le <xref:System.Windows.Forms.MenuStrip> contrôle remplace et ajoute des fonctionnalités à la <xref:System.Windows.Forms.MainMenu> contrôle ; Toutefois, le <xref:System.Windows.Forms.MainMenu> contrôle est conservé pour la compatibilité descendante et l’utilisation future si vous choisissez.  
  
## <a name="ways-to-use-the-menustrip-control"></a>Comment utiliser le contrôle MenuStrip  
 Utilisez le <xref:System.Windows.Forms.MenuStrip> le contrôle à :  
  
-   Créez facilement personnalisées, employées couramment menus qui prennent en charge utilisateur interface et mise en page fonctionnalités avancées, telles que texte et image classement et alignement, opérations de glisser-déplacer, MDI, dépassement de capacité et autres modes d’accès aux commandes de menu.  
  
-   Prend en charge de l’apparence par défaut et le comportement du système d’exploitation.  
  
-   Gérer les événements de manière cohérente pour tous les conteneurs et les éléments contenus, de la même façon que vous gérez des événements pour d’autres contrôles.  
  
 Le tableau suivant indique certaines propriétés particulièrement importantes de <xref:System.Windows.Forms.MenuStrip> et des classes associées.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> qui est utilisé pour afficher une liste de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|Obtient ou définit comment les menus enfants sont fusionnés avec les menus parents dans les applications MDI.|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|Obtient ou définit une valeur indiquant si les info-bulles sont affichées pour le <xref:System.Windows.Forms.MenuStrip>.|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|Obtient ou définit les touches de raccourci associés à la <xref:System.Windows.Forms.ToolStripMenuItem>.|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|Obtient ou définit une valeur qui indique si les touches de raccourci sont associés les <xref:System.Windows.Forms.ToolStripMenuItem> s’affichent en regard du <xref:System.Windows.Forms.ToolStripMenuItem>.|  
  
 Le tableau suivant présente les importantes <xref:System.Windows.Forms.MenuStrip> classes auxiliaires.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|Représente une option sélectionnable affichée sur un <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|Représente un menu contextuel.|  
|<xref:System.Windows.Forms.ToolStripDropDown>|Représente un contrôle qui permet à l’utilisateur à sélectionner un seul élément dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou un élément de menu de niveau supérieur.|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|Fournit des fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments de liste déroulante lorsque vous cliquez sur.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
