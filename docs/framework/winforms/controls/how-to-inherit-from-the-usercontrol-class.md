---
title: "Comment&#160;: h&#233;riter de la classe UserControl | Microsoft Docs"
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
  - "contrôles composites, créer"
  - "héritage, contrôles personnalisés Windows Forms"
  - "contrôles utilisateur (Windows Forms), créer"
  - "UserControl (classe), hériter de"
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: h&#233;riter de la classe UserControl
Si vous souhaitez combiner les fonctionnalités d'une ou de plusieurs contrôles Windows Forms, vous pouvez créer un *contrôle utilisateur*.  Les contrôles utilisateur allient le développement rapide de contrôle aux fonctionnalités standard des Windows Forms et à la polyvalence des propriétés et des méthodes personnalisées.  Lorsque vous commencez à créer un contrôle utilisateur, vous voyez apparaître un concepteur dans lequel vous pouvez disposer des contrôles Windows Forms standard.  Ces contrôles conservent toutes leurs fonctionnalités inhérentes, aussi bien que l'apparence et le comportement \(apparence et convivialité\) de contrôles standard.  Une fois que ces contrôles sont construits dans le contrôle utilisateur, toutefois, ils ne sont plus disponibles à vous à travers le code.  Le contrôle utilisateur effectue sa propre peinture et gère également toutes les fonctionnalités élémentaires associées aux contrôles.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un contrôle utilisateur  
  
1.  Créez un projet **Bibliothèque de contrôles Windows**.  
  
     Un projet est créé avec un contrôle utilisateur vide.  
  
2.  Faites glisser des contrôles à partir de l'onglet **Windows Forms** de la **Boîte à outils** jusqu'à votre concepteur.  
  
3.  Modifiez la position et l'apparence de ces contrôles en fonction de la façon dont vous voulez les voir apparaître dans le contrôle utilisateur final.  Si vous voulez que les contrôles constitutifs du contrôle utilisateur soient accessibles aux développeurs, déclarez\-les comme publics ou exposez sélectivement leurs propriétés.  Pour plus d'informations, consultez [Comment : exposer les propriétés des contrôles constitutifs](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Implémentez les éventuelles méthodes ou propriétés personnalisées que votre contrôle contiendra.  
  
5.  Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## Voir aussi  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [Comment : hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [Comment : hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [Comment : créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)