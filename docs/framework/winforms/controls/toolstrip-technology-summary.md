---
title: "Résumé de la technologie ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4777a6cb30f641faf2305bc6d8bca55d243c94b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-technology-summary"></a>Résumé de la technologie ToolStrip
Cette rubrique rassemble des informations sur le contrôle `ToolStrip` et les classes qui prennent en charge son utilisation.  
  
 Le contrôle `ToolStrip` et les classes qui lui sont associées fournissent une solution complète pour la création de barres d'outils, de barres d'état et de menus.  
  
## <a name="namespaces"></a>Espaces de noms  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Présentation  
 Grâce au contrôle `ToolStrip` et à ses classes, vous pouvez créer des fonctionnalités de barre d'outils avancées dont l'apparence et le comportement sont à la fois professionnels et cohérents. Le contrôle `ToolStrip` et ses classes offrent les améliorations suivantes par rapport aux contrôles précédents :  
  
-   Un modèle d'événement plus cohérent.  
  
-   Un comportement au moment du design plus cohérent avec des listes de tâches et des éditeurs de collections Items.  
  
-   Un rendu personnalisé grâce à `ToolStripManager` et `ToolStripRenderer`.  
  
-   Un rafting intégré (partage de l'espace horizontal ou vertical dans la zone d'outils quand celle-ci est ancrée) avec `ToolStripContainer` et `ToolStripPanel`.  
  
-   La réorganisation des éléments au moment du design et de l'exécution avec la propriété <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>.  
  
-   Le déplacement des éléments vers un menu de dépassement de capacité avec la propriété <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>.  
  
-   Un emplacement du contrôle entièrement configurable avec `ToolStripContainer`, `ToolStripPanel` et `ToolStripContentPanel`.  
  
-   L'hébergement de contrôles `ToolStrip`, traditionnels ou personnalisés à l'aide de `ToolStripControlHost`.  
  
-   La fusion des contrôles `ToolStrip` à l'aide de `ToolStripPanel`.  
  
 `ToolStrip` est la classe de base extensible de `MenuStrip`, `ContextMenuStrip` et `StatusStrip`. Ces contrôles sont des conteneurs <xref:System.Windows.Forms.ToolStripItem> qui héritent d'un comportement commun et de la gestion des événements, et qui sont étendus pour que chaque implémentation gère le comportement qui lui est associé. Les contrôles qui dérivent de <xref:System.Windows.Forms.ToolStripItem> sont répertoriés dans le tableau suivant. La classe de base `ToolStrip` gère les événements de peinture, d'entrée utilisateur et de glisser-déplacer pour ces contrôles.  
  
 Les contrôles `ToolStrip`, `MenuStrip`, `ContextMenuStrip` et `StatusStrip` remplacent les précédents contrôles de barre d'outils, de menu, de menu contextuel et de barre d'état. Toutefois, ces contrôles ont été conservés pour permettre une compatibilité descendante.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Classes ToolStrip  
 Le tableau suivant montre les classes ToolStrip groupées par technologie.  
  
|Technologie|Classe|  
|---------------------|-----------|  
|Conteneurs de barre d'outils, de barre d'état et de menu|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Éléments ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Emplacement|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Présentation et rendu|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>Fonctionnalités de ToolStrip au moment du design  
 La famille de contrôles <xref:System.Windows.Forms.ToolStrip> fournit un ensemble complet d'outils et de modèles permettant de définir et de modifier sur place les bases de l'interface utilisateur pour que vous puissiez créer rapidement une application prête à l'emploi.  
  
### <a name="task-dialog-boxes"></a>Boîtes de dialogue de tâches  
 Dans Visual Studio, le fait de cliquer sur le Smart Tag d’un contrôle du concepteur affiche une liste de tâches pour accéder facilement à de nombreuses commandes fréquemment utilisées.  
  
-   [Tâches MenuStrip, boîte de dialogue](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [Tâches ToolStrip, boîte de dialogue](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [Tâches ContextMenuStrip, boîte de dialogue](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [Tâches StatusStrip, boîte de dialogue](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [Tâches ToolStripContainer, boîte de dialogue](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Éditeurs de collections Items  
 Dans Visual Studio, lorsque vous cliquez sur **modifier les éléments** sur la tâche de liste ou cliquez sur le contrôle, puis sélectionnez **modifier les éléments** dans le menu contextuel, l’éditeur de collections du contrôle s’affiche. Les éditeurs de collections vous permettent d’ajouter, de supprimer et de réorganiser les éléments que contient le contrôle. Vous pouvez également afficher et modifier les propriétés du contrôle et de ses éléments.  
  
-   [Éditeur de collections d’éléments MenuStrip](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [Éditeur de collections d’éléments StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [Éditeur de collections d’éléments ContextMenuStrip](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [Éditeur de collections d’éléments ToolStrip](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Hébergement des contrôles  
 La classe <xref:System.Windows.Forms.ToolStripControlHost> fournit des wrappers intégrés pour les contrôles <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox> et <xref:System.Windows.Forms.ToolStripProgressBar>. Vous pouvez également héberger tout autre contrôle existant ou contrôle COM dans un <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Pour obtenir un exemple d’hébergement de contrôles, consultez [Comment : encapsuler un contrôle Windows Forms avec ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Rendu  
 Les classes <xref:System.Windows.Forms.ToolStrip> implémentent un schéma de rendu qui est très différent des autres contrôles Windows Forms. Avec ce schéma, vous pouvez facilement appliquer des styles et des thèmes.  
  
 Pour appliquer un style à un <xref:System.Windows.Forms.ToolStrip> et à tous les objets <xref:System.Windows.Forms.ToolStripItem> qu'il contient, il n'est pas nécessaire de gérer l'événement <xref:System.Windows.Forms.ToolStripItem.Paint> pour chaque élément. Vous pouvez définir la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> sur l'une des valeurs <xref:System.Windows.Forms.ToolStripRenderMode> autres que <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Vous pouvez également définir <xref:System.Windows.Forms.ToolStrip.Renderer%2A> directement sur n'importe quelle classe qui hérite de la classe <xref:System.Windows.Forms.ToolStripRenderer>. Le fait de définir cette propriété définit automatiquement <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Vous pouvez appliquer un même style à plusieurs objets <xref:System.Windows.Forms.ToolStrip> d'une même application en définissant <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> sur <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> et en définissant la propriété <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> sur le <xref:System.Windows.Forms.ToolStripManagerRenderMode> de votre choix ou sur la <xref:System.Windows.Forms.ToolStripRenderer> valeur, respectivement.  
  
 Pour obtenir des exemples de rendu, consultez [Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Styles et thèmes  
 <xref:System.Windows.Forms.ToolStrip> et les classes qui lui sont associées permettent de prendre en charge facilement les styles visuels et les apparences personnalisées qui ne nécessitent pas la substitution des méthodes <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> pour chaque élément. Utilisez <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>, ainsi que les propriétés <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> et <xref:System.Windows.Forms.ToolStrip.Renderer%2A>.  
  
## <a name="rafting-and-docking"></a>Rafting et ancrage  
 Les contrôles <xref:System.Windows.Forms.ToolStrip> peuvent faire l'objet d'un rafting, d'un ancrage ou d'un positionnement absolu. Les éléments <xref:System.Windows.Forms.ToolStrip> sont positionnés par le <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> du conteneur.  
  
 *Rafting* est la capacité des barres d’outils à partager l’espace horizontal ou vertical. Un formulaire Windows peut avoir un <xref:System.Windows.Forms.ToolStripContainer> qui contient des panneaux gauche, droit, haut et bas pour le positionnement, ainsi que les contrôles <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.StatusStrip> pour le rafting. Plusieurs contrôles <xref:System.Windows.Forms.ToolStrip> s'empilent verticalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> de gauche ou de droite. Ils s'empilent horizontalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> du haut ou du bas. Vous pouvez utiliser le <xref:System.Windows.Forms.ToolStripContentPanel> central du <xref:System.Windows.Forms.ToolStripContainer> pour positionner les contrôles traditionnels sur le formulaire.  
  
 Tous les contrôles <xref:System.Windows.Forms.ToolStripContainer> sont directement sélectionnables au moment du design et peuvent être supprimés. Un <xref:System.Windows.Forms.ToolStripContainer> est extensible et réductible, et peut être redimensionné avec les contrôles qu'il contient.  
  
 *Ancrage* consiste à spécifier l’emplacement d’un contrôle simples sur la gauche, droite, haut ou bas du formulaire.  
  
 L'avantage du rafting par rapport à l'ancrage est que les contrôles <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.StatusStrip> peuvent partager l'espace horizontal ou vertical avec d'autres contrôles.  
  
 Si vous n'utilisez pas le rafting, la plupart des contrôles <xref:System.Windows.Forms.ToolStrip> peuvent être ancrés dans le formulaire comme les autres contrôles. Vous pouvez également spécifier qu'un contrôle <xref:System.Windows.Forms.ToolStrip> soit librement positionné sur le formulaire en le supprimant de son <xref:System.Windows.Forms.ToolStripContainer> et en définissant sa propriété `Dock` sur `None`. Vous pouvez également spécifier sa position absolue en définissant la propriété <xref:System.Windows.Forms.Control.Location%2A>. Consultez [Comment : déplacer un ToolStrip hors d’un ToolStripContainer dans un formulaire](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Utilisez un ou plusieurs contrôles <xref:System.Windows.Forms.ToolStripPanel> pour plus de souplesse, en particulier pour les applications MDI, ou si vous n'avez pas besoin d'un <xref:System.Windows.Forms.ToolStripContainer>. Un <xref:System.Windows.Forms.ToolStripPanel> offre un espace ancrable pour le positionnement et le rafting des contrôles <xref:System.Windows.Forms.ToolStrip>, mais pas pour les contrôles traditionnels. Par défaut, le <xref:System.Windows.Forms.ToolStripPanel> n’apparaît pas dans le concepteur **boîte à outils**, mais vous pouvez l’y placer en cliquant sur le **boîte à outils**, puis cliquez sur **choisir des éléments de**. Vous pouvez également accéder par programmation à <xref:System.Windows.Forms.ToolStripPanel>, comme à toute autre classe.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.StatusStrip> permettent le dépassement de capacité des éléments. Ceci est similaire à la façon dont ces éléments se comportent dans les barres d'outils de Microsoft Office.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
