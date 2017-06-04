---
title: "Utilisation de contr&#244;les WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "interopérabilité (WPF)"
  - "Concepteur Windows Forms, interopérabilité avec WPF"
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Utilisation de contr&#244;les WPF
Vous pouvez utiliser des contrôles WPF \(Windows Presentation Foundation\) dans vos applications Windows Forms.  Bien qu'il s'agisse de deux technologies d'affichage différentes, elles interagissent intimement.  
  
 Le Concepteur Windows Forms fournit un environnement de conception visuel pour héberger les contrôles WPF \(Windows Presentation Foundation\).  Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>.  Ce contrôle permet au contrôle WPF de participer à la disposition du formulaire et de recevoir des messages du clavier et de la souris.  Au moment du design, vous pouvez réorganiser juste le contrôle <xref:System.Windows.Forms.Integration.ElementHost>, comme dans tout contrôle Windows Forms.  
  
 Vous pouvez également utiliser des contrôles Windows Forms dans vos applications WPF.  Pour plus d'informations, consultez [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## Dans cette section  
 [Comment : copier et coller un contrôle ElementHost au moment du design](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Indique comment copier un contrôle WPF \(Windows Presentation Foundation\) sur un Windows Form.  
  
 [Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Indique comment utiliser les fonctionnalités de disposition Windows Forms, telles que l'ancrage et les lignes d'alignement \(SnapLines\), pour réorganiser les contrôles WPF \(Windows Presentation Foundation\).  
  
 [Procédure pas à pas : modification des propriétés d'un élément WPF hébergé au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pour modifier des propriétés sur les contrôles WPF.  
  
 [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Indique comment créer un contrôle WPF \(Windows Presentation Foundation\) pour une utilisation dans vos applications Windows Forms.  
  
 [Procédure pas à pas : copier\-coller d'un contrôle ElementHost dans d'autres Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Indique comment copier un contrôle WPF \(Windows Presentation Foundation\) d'un Windows Form vers un autre.  
  
 [Procédure pas à pas : assignation du contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Affiche comment sélectionner les types de contrôles WPF \(Windows Presentation Foundation\) que vous souhaitez afficher sur votre formulaire.  
  
 [Procédure pas à pas : application de styles au contenu WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pour appliquer des styles aux contrôles WPF \(Windows Presentation Foundation\).  
  
## Référence  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Décrit une classe que vous pouvez utiliser pour héberger des contrôles WPF \(Windows Presentation Foundation\) dans vos applications Windows Forms.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Décrit une classe que vous pouvez utiliser pour héberger des contrôles Windows Forms dans votre application WPF \(Windows Presentation Foundation\).  
  
## Rubriques connexes  
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Décrit l'interopérabilité entre les technologies Windows Presentation Foundation et Windows Forms.  
  
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)  
 Décrit comment concevoir des contrôles WPF \(Windows Presentation Foundation\) dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].