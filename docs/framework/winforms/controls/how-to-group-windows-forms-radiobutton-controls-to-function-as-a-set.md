---
title: "Comment&#160;: grouper des contr&#244;les RadioButton Windows Forms en un ensemble fonctionnant ind&#233;pendamment | Microsoft Docs"
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
  - "contrôles (Windows Forms), regroupement"
  - "cases d'option, regroupement"
  - "RadioButton (contrôle Windows Forms), regroupement"
  - "contrôles Windows Forms, regroupement"
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: grouper des contr&#244;les RadioButton Windows Forms en un ensemble fonctionnant ind&#233;pendamment
Les contrôles <xref:System.Windows.Forms.RadioButton> Windows Forms permettent de proposer à l'utilisateur un choix entre plusieurs options, parmi lesquelles une seule peut être assignée à une procédure ou à un objet.  Par exemple, un groupe de contrôles <xref:System.Windows.Forms.RadioButton> peut afficher une liste de services de messagerie rapides, parmi lesquels un seul sera utilisé.  Par conséquent, il n'est possible de sélectionner qu'un seul contrôle <xref:System.Windows.Forms.RadioButton> à la fois, même s'il fait partie d'un groupe fonctionnel.  
  
 Pour regrouper des cases d'option, il suffit de les faire glisser jusqu'à un conteneur qui peut être un contrôle <xref:System.Windows.Forms.Panel> ou <xref:System.Windows.Forms.GroupBox>, ou encore un formulaire.  Toutes les cases d'option qui sont ajoutées directement à un formulaire constituent alors un seul et même groupe.  Pour ajouter des groupes distincts, placez\-les à l'intérieur de panneaux ou de zones de groupe.  Pour plus d'informations sur les panneaux ou zones de groupe, consultez [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) ou [Vue d'ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).  
  
### Pour regrouper des contrôles RadioButton et constituer un ensemble fonctionnant indépendamment des autres ensembles  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> depuis l'onglet **Windows Forms** de la **Boîte à outils** jusqu'au formulaire.  
  
2.  Dessinez des contrôles <xref:System.Windows.Forms.RadioButton> dans le contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.RadioButton>   
 [Vue d'ensemble du contrôle RadioButton](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [RadioButton, contrôle](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)