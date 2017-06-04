---
title: "Comment&#160;: cr&#233;er des contr&#244;les composites | Microsoft Docs"
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
  - "contrôles utilisateur (Windows Forms), créer"
  - "contrôles utilisateur (Windows Forms), hériter de"
  - "UserControl (classe), créer des contrôles composites"
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er des contr&#244;les composites
Les contrôles composites peuvent être utilisés de multiples façons.  Vous pouvez les créer dans un projet d'application bureautique Windows et les utiliser seulement dans les formulaires de ce projet.  Vous pouvez également les créer dans un projet Bibliothèque de contrôles Windows, compiler le projet pour créer un assembly et utiliser les contrôles dans d'autres projets.  Vous pouvez même hériter d'eux et utiliser l'héritage visuel pour les personnaliser rapidement en fonction de vos besoins spécifiques.  
  
> [!NOTE]
>  Si vous souhaitez créer un contrôle composite à utiliser sur les Web Forms, consultez [Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md).  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un contrôle composite  
  
1.  Ouvrez un nouveau projet **Application Windows** appelé `DemoControlHost`.  
  
2.  Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, donnez au fichier de classe \(fichier .vb ou .cs\) le nom que vous souhaitez attribuer au contrôle composite.  
  
4.  Cliquez sur le bouton **Ajouter** pour créer le fichier de classe pour le contrôle composite.  
  
5.  Ajoutez à la surface du contrôle composite des contrôles provenant de la **Boîte à outils**.  
  
6.  Insérez du code dans des procédures événementielles afin de gérer les événements déclenchés par le contrôle composite ou par les contrôles le constituant.  
  
7.  Fermez le concepteur pour le contrôle composite et enregistrez le fichier lorsque vous y êtes invité.  
  
8.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
     Le projet doit être généré pour que les contrôles personnalisés apparaissent dans la **Boîte à outils**.  
  
9. Utilisez l'onglet **DemoControlHost** de la **Boîte à outils** pour ajouter des instances de votre contrôle à `Form1`.  
  
### Pour créer une bibliothèque de classes de contrôle  
  
1.  Ouvrez un nouveau projet **Bibliothèque de contrôles Windows**.  
  
     Par défaut, le projet contient un contrôle composite.  
  
2.  Ajoutez des contrôles et du code en suivant la procédure décrite ci\-dessus.  
  
3.  Sélectionnez un contrôle dont vous ne voulez pas modifier les classes qui héritent et définissez sa propriété **Modifiers** en lui donnant la valeur **Private**.  
  
4.  Générez la DLL.  
  
### Pour hériter d'un contrôle composite issu d'une bibliothèque de classes de contrôle  
  
1.  Dans le menu **Fichier**, pointez sur **Ajouter**, puis sélectionnez **Nouveau projet** pour ajouter un nouveau projet **Application Windows** à la solution.  
  
2.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Références** pour le nouveau projet et sélectionnez **Ajouter la référence** pour ouvrir la boîte de dialogue **Ajouter la référence**.  
  
3.  Sélectionnez l'onglet **Projets** et double\-cliquez sur votre projet de bibliothèque de contrôles.  
  
4.  Dans le menu **Générer**, cliquez sur **Générer la solution**.  
  
5.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet de bibliothèque de contrôles et sélectionnez **Ajouter un nouvel élément** dans le menu contextuel.  
  
6.  Sélectionnez le modèle **Contrôle utilisateur hérité** dans la boîte de dialogue **Ajouter un nouvel élément**.  
  
7.  Dans la boîte de dialogue **Sélecteur d'héritage**, double\-cliquez sur le contrôle dont vous voulez hériter.  
  
     Un nouveau contrôle est ajouté au projet.  
  
8.  Ouvrez le Concepteur visuel pour le nouveau contrôle et ajoutez les contrôles constitutifs requis.  
  
     Vous pouvez voir les contrôles constitutifs hérités du contrôle composite de votre DLL et modifier les propriétés de ceux dont la propriété **Modifiers** a la valeur **Public**.  Vous ne pouvez pas modifier les propriétés d'un contrôle dont la propriété **Modifiers** a la valeur **Private**.  
  
## Voir aussi  
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C\#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [Procédure pas à pas : héritage d'un contrôle Windows Forms à l'aide de Visual C\#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)   
 [Recommandations relatives au type du contrôle](../../../../docs/framework/winforms/controls/control-type-recommendations.md)   
 [Comment : créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)