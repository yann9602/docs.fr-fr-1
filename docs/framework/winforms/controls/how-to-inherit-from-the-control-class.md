---
title: "Comment&#160;: h&#233;riter de la classe du contr&#244;le | Microsoft Docs"
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
  - "Control (classe), hériter de"
  - "contrôles personnalisés (Windows Forms), créer"
  - "contrôles personnalisés (Windows Forms), héritage"
  - "héritage, contrôles personnalisés Windows Forms"
  - "OnPaint (méthode Windows Forms)"
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: h&#233;riter de la classe du contr&#244;le
Si vous souhaitez créer un contrôle entièrement personnalisé à utiliser sur un Windows Form, vous devez hériter de la classe <xref:System.Windows.Forms.Control>.  Si le fait d'hériter de la classe <xref:System.Windows.Forms.Control> requiert que vous exécutiez plus d'organisation et d'implémentation, il vous fournit également la plus grande plage d'options.  Lorsque vous héritez de la classe <xref:System.Windows.Forms.Control>, vous héritez des fonctionnalités élémentaires qui permettent à un contrôle d'opérer.  Les fonctionnalités de la classe <xref:System.Windows.Forms.Control> gèrent les données entrées par l'utilisateur au moyen du clavier et de la souris, définissent les limites et la taille des contrôles, offrent un handle de fenêtre et prennent en charge la gestion des messages et la sécurité.  Ils n'intègrent ni peinture, ici le rendu réel de l'interface graphique du contrôle, ni fonctionnalités spécifiques d'interaction avec l'utilisateur.  Vous devez fournir toutes ces caractéristiques par du code personnalisé.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un contrôle personnalisé  
  
1.  Créez un projet **Application Windows** ou **Bibliothèque de contrôles Windows**.  
  
2.  Dans le menu **Projet**, choisissez **Ajouter une classe**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.  
  
     Un nouveau contrôle personnalisé est alors ajouté à votre projet.  
  
4.  Appuyez sur F7 pour ouvrir l'**éditeur de code** pour votre contrôle personnalisé.  
  
5.  Recherchez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> qui doit être vide à l'exception d'un appel à la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base.  
  
6.  Modifiez le code pour y insérer la peinture personnalisée que vous avez choisie pour votre contrôle.  
  
     Pour plus d'informations sur l'écriture de code pour restituer des graphiques pour les contrôles, consultez [Peinture et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
7.  Implémentez les méthodes ou propriétés personnalisées que votre contrôle doit contenir.  
  
8.  Enregistrez et testez le contrôle.  
  
## Voir aussi  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [Comment : hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [Comment : hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [Comment : créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)