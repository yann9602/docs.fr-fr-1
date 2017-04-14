---
title: "Comment&#160;: d&#233;signer un bouton Windows Forms comme bouton Accepter &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "bouton d'acceptation des Windows Forms"
  - "bouton (contrôle Windows Forms), désigner comme bouton par défaut"
  - "boutons, valeur par défaut sur les Windows Forms"
  - "contrôles Windows Forms, bouton par défaut dans Windows Form"
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;signer un bouton Windows Forms comme bouton Accepter &#224; l&#39;aide du concepteur
Sur tout Windows Form, vous pouvez désigner un contrôle <xref:System.Windows.Forms.Button> comme bouton Accepter \(également appelé bouton par défaut\).  Lorsque l'utilisateur appuie sur la touche ENTRÉE, le bouton par défaut est sélectionné, et cela même si un autre contrôle a le focus  Il existe des exceptions à cette règle : lorsque le contrôle qui a le focus est un autre bouton, auquel cas c'est ce deuxième bouton qui est activé, une zone de texte multiligne ou un contrôle personnalisé qui intercepte la touche ENTRÉE.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour désigner le bouton Accepter  
  
1.  Sélectionnez le formulaire dans lequel se trouve le bouton.  
  
2.  Dans la fenêtre **Propriétés**, définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire en lui affectant le nom du contrôle <xref:System.Windows.Forms.Button>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>   
 [Vue d'ensemble du contrôle Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)