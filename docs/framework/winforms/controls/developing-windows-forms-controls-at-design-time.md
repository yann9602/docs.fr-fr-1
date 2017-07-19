---
title: "D&#233;veloppement de contr&#244;les Windows Forms au moment du design | Microsoft Docs"
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
  - "Contrôles Windows Forms"
  - "Contrôles Windows Forms, création"
  - "contrôles (Windows Forms)"
  - "contrôles (Windows Forms), créer"
  - "contrôles utilisateur (Windows Forms)"
  - "contrôles personnalisés (Windows Forms)"
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# D&#233;veloppement de contr&#244;les Windows Forms au moment du design
Les auteurs de contrôle, le .NET Framework fournit une multitude de technologies de création de contrôles. Les auteurs ne sont plus contraints de concevoir des contrôles composites qui agissent en tant que collection de contrôles préexistants. Par héritage, vous pouvez créer vos propres contrôles de contrôles composites ou de contrôles Windows Forms préexistants. Vous pouvez également concevoir vos propres contrôles qui implémentent la peinture personnalisée. Ces options permettent une grande souplesse pour la conception et les fonctionnalités de l’interface visuelle. Pour tirer parti de ces fonctionnalités, vous devez connaître avec les concepts de programmation orientée objet.  
  
> [!NOTE]
>  Il n’est pas nécessaire de disposer d’une connaissance approfondie de l’héritage, mais il peut s’avérer utile pour faire référence à [NOT IN BUILD : l’héritage dans Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c).  
  
 Si vous souhaitez créer des contrôles personnalisés à utiliser sur les Web Forms, consultez [développement de contrôles de serveur ASP.NET personnalisé](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : Création d’un contrôle Composite avec Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Montre comment créer un contrôle composite simple dans Visual Basic.  
  
 [Procédure pas à pas : Création d’un contrôle Composite avec Visual c#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Montre comment créer un contrôle composite simple en c#.  
  
 [Procédure pas à pas : Héritage d’un contrôle Windows Forms avec Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans Visual Basic.  
  
 [Procédure pas à pas : Héritage d’un contrôle Windows Forms avec Visual c#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans c#.  
  
 [Procédure pas à pas : Exécution de tâches courantes à l’aide de balises actives sur Windows Forms des contrôles](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Montre comment utiliser la fonctionnalité de balise active sur les contrôles Windows Forms.  
  
 [Procédure pas à pas : Sérialisation des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Montre comment utiliser le <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=fullName> attribut pour sérialiser une collection.  
  
 [Procédure pas à pas : Débogage Windows Forms personnalisés des contrôles au moment du Design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Montre comment déboguer le comportement au moment du design d’un contrôle Windows Forms.  
  
 [Procédure pas à pas : Création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du Design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Montre comment intégrer étroitement un contrôle composite dans l’environnement de conception.  
  
 [Comment : créer des contrôles pour Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Fournit une vue d’ensemble des considérations d’implémentation d’un contrôle Windows Forms.  
  
 [Comment : créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Montre comment créer un contrôle en héritant d’un contrôle composite.  
  
 [Comment : hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Fournit une vue d’ensemble de la procédure de création d’un contrôle composite.  
  
 [Comment : hériter Windows existants des contrôles de formulaires](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Montre comment créer un contrôle étendu en héritant de la <xref:System.Windows.Forms.Button> classe de contrôle.  
  
 [Comment : hériter de la classe de contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Fournit une vue d’ensemble de la création d’un contrôle étendu.  
  
 [Comment : aligner un contrôle sur les bords des formulaires au moment du Design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Montre comment utiliser le <xref:System.Windows.Forms.Control.Dock%2A> propriété pour aligner votre contrôle sur le bord du formulaire qu’il occupe.  
  
 [Comment : afficher un contrôle dans la boîte de dialogue éléments de boîte à outils choisir](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Indique la procédure d’installation de votre contrôle afin qu’il apparaisse dans le **personnaliser la boîte à outils** boîte de dialogue.  
  
 [Comment : fournir une Bitmap de boîte à outils pour un contrôle](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Montre comment utiliser le <xref:System.Drawing.ToolboxBitmapAttribute> pour afficher une icône en regard de votre contrôle personnalisé dans le **boîte à outils**.  
  
 [Comment : tester le comportement d’exécution d’un UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Montre comment utiliser le **conteneur de Test UserControl** pour tester le comportement d’un contrôle composite.  
  
 [Erreurs au moment du design dans le Concepteur Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Explique la signification et l’utilisation de la liste d’erreurs au moment du Design qui apparaît dans Microsoft Visual Studio lorsque le Concepteur Windows Forms ne parvient pas à charger.  
  
 [Résolution des problèmes de contrôle et de création de composants](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Indique comment diagnostiquer et résoudre les problèmes courants qui peuvent se produire lorsque vous créez un composant personnalisé ou un contrôle.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Control?displayProperty=fullName>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Développement Windows Forms personnalisés avec le .NET Framework, les contrôles](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 Explique comment créer vos propres contrôles personnalisés avec le .NET Framework.  
  
 [Indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Présente le common language runtime, qui est conçu pour simplifier la création et l’utilisation des composants. Un aspect important de cette simplification est amélioré l’interopérabilité entre les composants écrits à l’aide de différents langages de programmation. Le Common Language Specification (CLS) permet de créer des outils et composants fonctionnant avec plusieurs langages de programmation.  
  
 [Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Décrit comment activer votre composant ou contrôle à afficher dans le **personnaliser la boîte à outils** boîte de dialogue.