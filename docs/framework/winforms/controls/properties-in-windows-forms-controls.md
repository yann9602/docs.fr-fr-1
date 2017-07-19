---
title: "Propri&#233;t&#233;s dans les contr&#244;les Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), propriétés"
  - "contrôles personnalisés (Windows Forms), vue d'ensemble des propriétés à l'aide du code"
  - "propriétés (Windows Forms)"
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Propri&#233;t&#233;s dans les contr&#244;les Windows Forms
Un contrôle Windows Forms hérite de nombreuses propriétés de la classe de base <xref:System.Windows.Forms.Control?displayProperty=fullName>.  Celles\-ci incluent des propriétés telles que <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, et beaucoup d'autres.  Pour plus d'informations sur les propriétés héritées, consultez <xref:System.Windows.Forms.Control?displayProperty=fullName>.  
  
 Vous pouvez substituer les propriétés héritées de votre contrôle ainsi qu'en définir de nouvelles.  
  
## Dans cette section  
 [Définition d'une propriété](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Montre comment implémenter une propriété pour un contrôle ou un composant personnalisé et montre comment intégrer la propriété dans l'environnement de design.  
  
 [Définition de valeurs par défaut avec les méthodes ShouldSerialize et Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Montre comment définir les valeurs de propriété par défaut pour un contrôle ou un composant personnalisé.  
  
 [Événements de modification de propriété](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Décrit comment activer des notifications de modification de propriété lorsqu'une valeur de propriété change.  
  
 [Comment : exposer les propriétés des contrôles constitutifs](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Montre comment exposer des propriétés de contrôles constituants d'un contrôle composite personnalisé.  
  
 [Implémentation de méthode dans les contrôles personnalisés](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Décrit comment implémenter des méthodes dans des contrôles et composants personnalisés.  
  
## Référence  
 <xref:System.Windows.Forms.UserControl>  
 Documente la classe de base pour implémenter des contrôles composites.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Documente l'attribut qui spécifie le <xref:System.ComponentModel.TypeConverter> à utiliser pour un type de propriété personnalisé.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Documente l'attribut qui spécifie le <xref:System.Drawing.Design.UITypeEditor> à utiliser pour une propriété personnalisée.  
  
## Rubriques connexes  
 [Attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Décrit les attributs que vous pouvez appliquer aux propriétés et à d'autres membres de vos contrôles et composants personnalisés.  
  
 [Design\-Time Attributes for Components](../Topic/Design-Time%20Attributes%20for%20Components.md)  
 Répertorie les attributs de métadonnées à appliquer aux composants et contrôles de sorte que les concepteurs visuels les affichent correctement au moment du design.  
  
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)  
 Décrit comment implémenter des classes telles que des éditeurs et des concepteurs qui fournissent la prise en charge au moment du design.