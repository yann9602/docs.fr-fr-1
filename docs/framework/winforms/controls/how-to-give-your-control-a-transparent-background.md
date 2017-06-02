---
title: "Comment&#160;: affecter un arri&#232;re-plan transparent &#224; votre contr&#244;le | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), arrière-plan transparent"
  - "transparence, contrôles personnalisés Windows Forms"
  - "arrière-plans transparents, contrôles personnalisés"
ms.assetid: 32433e63-f4e9-4305-9857-6de3edeb944a
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Comment&#160;: affecter un arri&#232;re-plan transparent &#224; votre contr&#244;le
Dans les versions antérieures de .NET Framework, les contrôles ne prenaient pas en charge la définition de couleurs d’arrière\-plan transparentes sans définition préalable de la méthode <xref:System.Windows.Forms.Control.SetStyle%2A> dans le constructeur du formulaire. Dans la version actuelle de l’infrastructure, vous pouvez affecter <xref:System.Drawing.Color.Transparent%2A> comme couleur d’arrière\-plan de la plupart des contrôles  dans la fenêtre **Propriétés** au moment du design ou dans le code dans le constructeur du formulaire.  
  
> [!NOTE]
>  Les contrôles Windows Forms ne prennent pas en charge la véritable transparence. L’arrière\-plan d’un contrôle Windows Forms transparent est peint par son parent.  
  
> [!NOTE]
>  Le contrôle <xref:System.Windows.Controls.Button> ne prend pas en charge une couleur d’arrière\-plan transparente même quand la propriété <xref:System.Windows.Forms.ButtonBase.BackColor%2A> a la valeur <xref:System.Drawing.Color.Transparent%2A>.  
  
### Pour affecter un arrière\-plan transparent à votre contrôle  
  
-   Dans la fenêtre Propriétés, choisissez la propriété <xref:System.Windows.Forms.ButtonBase.BackColor%2A> et affectez\-lui la valeur <xref:System.Drawing.Color.Transparent%2A>.  
  
## Voir aussi  
 <xref:System.Drawing.Color.FromArgb%2A>   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)   
 [Comment : dessiner des lignes opaques et translucides](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)