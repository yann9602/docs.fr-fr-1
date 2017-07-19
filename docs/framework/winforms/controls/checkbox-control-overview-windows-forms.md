---
title: "Vue d&#39;ensemble du contr&#244;le CheckBox (Windows Forms) | Microsoft Docs"
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
  - "CheckBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles dépendants, cases à cocher"
  - "cases à cocher, à propos des cases à cocher"
  - "CheckBox (contrôle Windows Forms), à propos du contrôle CheckBox"
  - "liaison de données, contrôles CheckBox"
  - "contrôles liés aux données, cases à cocher"
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Vue d&#39;ensemble du contr&#244;le CheckBox (Windows Forms)
Le contrôle <xref:System.Windows.Forms.CheckBox> Windows Forms indique si une condition est active ou inactive.  Il est couramment utilisé pour présenter à l'utilisateur des alternatives de type Oui\/Non ou Vrai\/Faux.  Vous pouvez utiliser les contrôles CheckBox en groupes pour afficher plusieurs options parmi lesquelles l'utilisateur peut en sélectionner une ou plusieurs.  
  
 Le contrôle CheckBox \(case à cocher\) est similaire au contrôle RadioButton \(case d'option\), car comme lui il indique une sélection effectuée par l'utilisateur.  Toutefois, dans un groupe de cases d'option, l'utilisateur ne peut sélectionner qu'une seule option à la fois.  Dans un groupe de contrôles CheckBox, en revanche, il est possible d'activer autant de cases à cocher que souhaité.  
  
 Une case à cocher peut être reliée à des éléments de la base de données à l'aide d'une simple liaison de données.  Plusieurs cases à cocher peuvent être regroupées à l'aide du contrôle <xref:System.Windows.Forms.GroupBox>.  Cette particularité s'avère utile pour des questions d'apparence, mais aussi de design d'interface utilisateur, dans la mesure où les contrôles groupés peuvent être déplacés ensemble dans le Concepteur de formulaires.  Pour plus d'informations, consultez [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md) et [GroupBox, contrôle](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).  
  
 Le contrôle <xref:System.Windows.Forms.CheckBox> possède deux propriétés importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> et <xref:System.Windows.Forms.CheckBox.CheckState%2A>.  La propriété <xref:System.Windows.Forms.CheckBox.Checked%2A> retourne la valeur `true` ou `false`.  La propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A> retourne <xref:System.Windows.Forms.CheckState> ou <xref:System.Windows.Forms.CheckState> ; ou, si la propriété <xref:System.Windows.Forms.CheckBox.ThreeState%2A> a la valeur `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut retourner également <xref:System.Windows.Forms.CheckState>.  Dans l'état indéterminé, la zone est affichée avec une apparence estompée pour indiquer que l'option n'est pas disponible.  
  
## Voir aussi  
 <xref:System.Windows.Forms.CheckBox>   
 [Comment : définir des options avec les contrôles CheckBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [Comment : répondre à un clic du contrôle CheckBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox, contrôle](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)