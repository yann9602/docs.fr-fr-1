---
title: "Comment&#160;: cr&#233;er des contr&#244;les pour des Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), créer"
  - "contrôles personnalisés (Windows Forms), créer"
  - "UserControl (classe), Windows Forms"
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er des contr&#244;les pour des Windows Forms
Un contrôle représente un lien graphique entre l'utilisateur et le programme.  Un contrôle peut fournir ou traiter des données, accepter des données entrées par l'utilisateur, répondre à des événements ou exécuter diverses fonctions mettant en relation l'utilisateur et l'application.  Un contrôle est essentiellement un composant doté d'une interface graphique ; il peut donc exécuter n'importe quelle fonction exécutée par un composant, mais aussi offrir une interaction avec l'utilisateur.  Les contrôles sont créés pour remplir certaines fonctions spécifiques et leur création n'est ni plus ni moins qu'une autre tâche de programmation.  Gardez cela présent à l'esprit en prenant connaissance de la procédure suivante qui constitue une vue d'ensemble du processus de création de contrôles.  Des liens vous renvoient à des informations supplémentaires sur certaines étapes de la procédure.  
  
> [!NOTE]
>  Si vous souhaitez créer un contrôle personnalisé à utiliser sur les Web Forms, consultez [Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md).  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un contrôle  
  
1.  Définissez la tâche que le contrôle doit accomplir et le rôle qu'il est appelé à jouer dans votre application.  Les facteurs à prendre en compte sont les suivants :  
  
    -   De quel type d'interface graphique avez\-vous besoin ?  
  
    -   Quelles interactions avec l'utilisateur ce contrôle gérera\-t\-il ?  
  
    -   Les fonctionnalités dont vous avez besoin sont\-elles fournies par des contrôles existant déjà ?  
  
    -   Pouvez\-vous obtenir les fonctionnalités dont vous avez besoin en combinant plusieurs contrôles Windows Forms ?  
  
2.  Si vous avez besoin d'un modèle objet pour votre contrôle, déterminez la façon dont les fonctionnalités seront distribuées à l'intérieur de ce modèle et répartissez\-les entre le contrôle et les éventuels sous\-objets.  Un modèle objet peut s'avérer utile si vous prévoyez de créer un contrôle complexe ou si vous souhaitez incorporer plusieurs fonctionnalités.  
  
3.  Déterminez le type du contrôle \(par exemple, contrôle utilisateur, contrôle personnalisé ou contrôle Windows Forms hérité\) répondant à vos besoins.  Pour plus d'informations, consultez [Recommandations relatives au type du contrôle](../../../../docs/framework/winforms/controls/control-type-recommendations.md) et [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Présentez les fonctionnalités sous forme de propriétés, de méthodes et d'événements du contrôle et de ses sous\-objets ou structures secondaires et assignez les niveaux d'accès appropriés \(par exemple, public, protégé, etc.\).  
  
5.  Si vous avez besoin de peinture personnalisée pour votre contrôle, ajoutez à ce dernier le code requis.  Pour plus d'informations, consultez [Peinture et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Si votre contrôle hérite de <xref:System.Windows.Forms.UserControl>, vous pouvez tester son comportement à l'exécution en générant le projet de contrôle et en l'exécutant dans le **conteneur de test UserControl**.  Pour plus d'informations, consultez [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Vous pouvez également tester et déboguer votre contrôle en créant un nouveau projet, tel qu'une application Windows, et en le plaçant dans un conteneur.  Ce processus est montré dans le cadre de [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Chaque fois que vous créez une fonctionnalité, ajoutez des options à votre projet test afin de pouvoir tester la nouvelle fonctionnalité.  
  
9. Répétez la procédure en affinant le design.  
  
10. Empaquetez le contrôle et déployez\-le.  Pour plus d'informations, consultez [Déploiement d'applications, de services et de composants](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [Comment : hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [Comment : hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [Comment : hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [Comment : tester le comportement d'un UserControl au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)