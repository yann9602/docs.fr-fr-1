---
title: "H&#233;ritage visuel des Windows Forms | Microsoft Docs"
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
  - "formulaires de base"
  - "héritage de formulaire"
  - "héritage"
  - "héritage, formulaires"
  - "formulaires hérités"
  - "formulaires hérités, Windows Forms"
  - "Windows Forms, héritage"
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# H&#233;ritage visuel des Windows Forms
Vous pouvez à l'occasion avoir besoin qu'un projet appelle un formulaire similaire à un autre que vous avez créé dans un précédent projet.  Vous pouvez aussi vouloir créer un formulaire de base contenant des paramètres tel qu'un arrière\-plan statique ou une présentation particulière des contrôles que vous comptez réutiliser dans un projet, chaque nouvelle itération contenant des modifications par rapport à ce modèle d'origine.  L'héritage de formulaire vous permet de créer un formulaire de base puis d'en hériter et de le modifier en conservant par ailleurs les paramètres du modèle d'origine dont vous avez besoin.  
  
 Vous pouvez créer des formulaires de classe dérivée par programme ou en utilisant le sélecteur d'héritage visuel.  
  
## Dans cette section  
 [Comment : hériter des Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 Explique comment créer des formulaires hérités dans le code.  
  
 [Comment : hériter de formulaires à l'aide de la boîte de dialogue Sélecteur d'héritage](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 Explique comment créer des formulaires hérités à l'aide du Sélecteur d'héritage.  
  
 [Conséquences de la modification de l'aspect d'un formulaire de base](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 Explique comment modifier les contrôles d'un formulaire de base et leurs propriétés.  
  
 [Procédure pas à pas : démonstration de l'héritage visuel](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 Explique comment créer un Windows Form de base et le compiler dans une bibliothèque de classes.  Vous importerez cette bibliothèque de classes dans un autre projet, puis créerez un nouveau formulaire qui héritera du formulaire de base.  
  
 [Comment : utiliser les modificateurs et les propriétés GenerateMember](../../../../docs/framework/winforms/advanced/how-to-use-the-modifiers-and-generatemember-properties.md)  
 Donne des directions pour l'utilisation des propriétés `GenerateMember` et `Modifiers`, qui sont pertinentes lorsque le Concepteur Windows Forms génère une variable membre pour un composant.  
  
## Rubriques connexes  
 [NOT IN BUILD: Inheritance in Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)  
 Explique comment définir des classes Visual Basic servant de base à d'autres classes.  
  
 [classe](../Topic/class%20\(C%23%20Reference\).md)  
 Décrit l'approche des classes dans C\# qui permet l'héritage simple.  
  
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)  
 Répertorie les problèmes courants liés aux gestionnaires d'événements dans les composants hérités.