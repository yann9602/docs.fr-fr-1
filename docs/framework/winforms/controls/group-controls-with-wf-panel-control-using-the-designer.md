---
title: "Comment&#160;: grouper les contr&#244;les avec le contr&#244;le Panel Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "Panel (contrôle Windows Forms), regrouper les contrôles"
  - "contrôles Windows Forms, regroupement"
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: grouper les contr&#244;les avec le contr&#244;le Panel Windows Forms &#224; l&#39;aide du concepteur
Les contrôles <xref:System.Windows.Forms.Panel> Windows Forms permettent de regrouper d'autres contrôles.  Il existe trois raisons de regrouper des contrôles.  Regroupement visuel d'éléments connexes en vue de fournir une interface plus claire à l'utilisateur ; regroupement de programmation, des cases d'option par exemple ; enfin, au moment du design, déplacement de plusieurs contrôles comme une même entité.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un groupe de contrôles  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Panel> de l'onglet **Windows Forms** de la boîte à outils jusqu'à un formulaire.  
  
2.  Ajoutez d'autres contrôles au contrôle Panel en les dessinant à l'intérieur du contrôle.  
  
     Si vous voulez inclure dans le contrôle Panel des contrôles existants, sélectionnez\-les tous, coupez\-les dans le Presse\-papiers, sélectionnez le contrôle <xref:System.Windows.Forms.Panel> et collez\-les dans le contrôle Panel.  Vous pouvez aussi les faire glisser.  
  
3.  \(Facultatif\) Si vous voulez ajouter une bordure à un contrôle panel, définissez sa propriété <xref:System.Windows.Forms.BorderStyle>.  Vous disposez de trois options : <xref:System.Windows.Forms.BorderStyle>, <xref:System.Windows.Forms.BorderStyle> et <xref:System.Windows.Forms.BorderStyle>.  
  
## Voir aussi  
 [Panel, contrôle](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)   
 [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [Comment : définir l'arrière\-plan d'un contrôle Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)