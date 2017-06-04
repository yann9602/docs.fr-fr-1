---
title: "Fusion d&#39;&#233;l&#233;ments de menu dans le contr&#244;le MenuStrip Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MenuStrip, fusionner"
  - "fusionner, concepts généraux"
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Fusion d&#39;&#233;l&#233;ments de menu dans le contr&#244;le MenuStrip Windows Forms
Si vous possédez une application d'interface multidocument \(MDI\), vous pouvez fusionner des éléments de menu ou des menus entiers du formulaire enfant dans les menus du formulaire parent.  
  
 Cette rubrique décrit les concepts de base associés à la fusion d'éléments de menu dans une application MDI.  
  
## Concepts généraux  
 Les procédures de fusion impliquent à la fois un contrôle cible et un contrôle de code source :  
  
-   La cible est le contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire principal ou parent MDI dans lequel vous fusionnez des éléments de menu.  
  
-   La source est le contrôle <xref:System.Windows.Forms.MenuStrip> sur le formulaire enfant MDI qui contient les éléments de menu à fusionner dans le menu cible.  
  
 La propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> identifie l'élément de menu dont vous remplissez la liste déroulante avec les titres des enfants MDI du formulaire parent MDI actuel.  Par exemple, vous répertoriez en général les enfants MDI qui sont actuellement ouverts dans le menu **Fenêtre**.  
  
 La propriété <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> identifie les éléments de menu qui proviennent d'un <xref:System.Windows.Forms.MenuStrip> sur un formulaire enfant MDI.  
  
 Vous pouvez fusionner des éléments de menu manuellement ou automatiquement.  Les éléments de menu fusionnent de la même façon pour les deux méthodes, mais la fusion est activée différemment, comme abordé dans les sections « Fusion manuelle » et « Fusion automatique », plus loin dans cette rubrique.  Dans les fusions manuelle et automatique, chaque action de fusion affecte l'action de fusion suivante.  
  
 La fusion <xref:System.Windows.Forms.MenuStrip> déplace des éléments de menu d'un <xref:System.Windows.Forms.ToolStrip> à un autre plutôt que de les cloner, comme c'était le cas avec <xref:System.Windows.Forms.MainMenu>.  
  
## Valeurs MergeAction  
 Vous définissez l'action de fusion sur les éléments de menu dans le <xref:System.Windows.Forms.MenuStrip> de code source à l'aide de la propriété <xref:System.Windows.Forms.MergeAction>.  
  
 Le tableau suivant décrit la signification et l'utilisation classique des actions de fusion disponibles.  
  
|Valeur MergeAction|Description|Utilisation courante|  
|------------------------|-----------------|--------------------------|  
|<xref:System.Windows.Forms.MergeAction>|\(Valeur par défaut\) Ajoute l'élément source à la fin de la collection de l'élément cible.|Ajout d'éléments de menu à la fin du menu lorsqu'une partie du programme est activée.|  
|<xref:System.Windows.Forms.MergeAction>|Ajoute l'élément source à la collection de l'élément cible, à l'emplacement spécifié par la propriété <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> définie sur l'élément source.|Ajout d'éléments de menu au milieu ou au début du menu lorsqu'une partie du programme est activée.<br /><br /> Si la valeur de <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> est la même pour les deux éléments de menu, ils sont ajoutés dans l'ordre inverse.  Définissez <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> convenablement pour conserver l'ordre d'origine.|  
|<xref:System.Windows.Forms.MergeAction>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n'est trouvée, puis remplace l'élément de menu cible correspondant par l'élément de menu source.|Remplacement d'un élément de menu cible par un élément de menu source du même nom dont la fonction est différente.|  
|<xref:System.Windows.Forms.MergeAction>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n'est trouvée, puis ajoute tous les éléments déroulants de la source à la cible.|Génération d'une structure de menu qui insère ou ajoute des éléments de menu dans un sous\-menu, ou supprime des éléments de menu d'un sous\-menu.  Par exemple, vous pouvez ajouter un élément de menu d'un enfant MDI à un menu **Enregistrer sous** <xref:System.Windows.Forms.MenuStrip> principal.<br /><br /> <xref:System.Windows.Forms.MergeAction> vous permet de naviguer dans la structure de menu sans prendre de mesure.  Il offre un moyen d'évaluer les éléments suivants.|  
|<xref:System.Windows.Forms.MergeAction>|Recherche une correspondance de texte ou utilise la valeur <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> si aucune correspondance de texte n'est trouvée, puis supprime l'élément de la cible.|Suppression d'un élément de menu du <xref:System.Windows.Forms.MenuStrip> cible.|  
  
## Fusion manuelle  
 Seuls les contrôles <xref:System.Windows.Forms.MenuStrip> participent à la fusion automatique.  Pour combiner les éléments d'autres contrôles, tels que les contrôles <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.StatusStrip>, vous devez les fusionner manuellement, en appelant les méthodes <xref:System.Windows.Forms.ToolStripManager.Merge%2A> et <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> dans votre code selon les besoins.  
  
## Fusion automatique  
 Vous pouvez utiliser la fusion automatique pour les applications MDI en activant le formulaire source.  Pour utiliser un <xref:System.Windows.Forms.MenuStrip> dans une application MDI, définissez la propriété <xref:System.Windows.Forms.Form.MainMenuStrip%2A> en fonction du <xref:System.Windows.Forms.MenuStrip> cible afin que les actions de fusion exécutées sur le <xref:System.Windows.Forms.MenuStrip> de code source soient répercutées dans le <xref:System.Windows.Forms.MenuStrip> cible.  
  
 Vous pouvez déclencher la fusion automatique en activant le <xref:System.Windows.Forms.MenuStrip> sur la source MDI.  Lors de l'activation, le <xref:System.Windows.Forms.MenuStrip> de code source est fusionné dans la cible MDI.  Lorsqu'un nouveau formulaire devient actif, la fusion est rétablie sur le dernier formulaire et déclenchée sur le nouveau.  Vous pouvez contrôler ce comportement en définissant la propriété <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> selon les besoins sur chaque <xref:System.Windows.Forms.ToolStripItem> et en définissant la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> sur chaque <xref:System.Windows.Forms.MenuStrip>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripManager>   
 <xref:System.Windows.Forms.MenuStrip>   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [Comment : créer une liste des fenêtres MDI avec MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)   
 [Comment : configurer la fusion de menus automatique pour les applications MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)