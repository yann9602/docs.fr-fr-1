---
title: "Développement de contrôles Windows Forms au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9910aa1849ed9288eca7003408c0afc39c641dbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Développement de contrôles Windows Forms au moment du design
Pour les auteurs de contrôles, le .NET Framework fournit une multitude de technologies de création de contrôles. Les auteurs ne sont plus contraints de concevoir des contrôles composites qui agissent en tant que collection de contrôles préexistants. À travers l’héritage, vous pouvez créer vos propres contrôles à partir de contrôles composites ou de contrôles Windows Forms préexistants. Vous pouvez également concevoir vos propres contrôles qui implémentent un dessin personnalisé. Ces options permettent une grande souplesse dans la conception et les fonctionnalités de l’interface visuelle. Pour tirer parti de ces fonctionnalités, vous devez bien connaître les concepts de la programmation orientée objet.  
  
> [!NOTE]
>  Il n’est pas nécessaire de disposer d’une bonne compréhension de l’héritage, mais il peut s’avérer utile pour faire référence à [fondamentaux de l’héritage (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Si vous voulez créer des contrôle personnalisés à utiliser sur des Web Forms, consultez [Développement de contrôles serveur ASP.NET personnalisés](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure pas à pas : création d’un contrôle composite à l’aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Montre comment créer un contrôle composite simple dans Visual Basic.  
  
 [Procédure pas à pas : création d’un contrôle composite à l’aide de Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Montre comment créer un contrôle composite simple dans C#.  
  
 [Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans Visual Basic.  
  
 [Procédure pas à pas : héritage d’un contrôle Windows Forms à l’aide de Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans C#.  
  
 [Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Montre comment utiliser la fonctionnalité de balise active sur les contrôles Windows Forms.  
  
 [Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Montre comment utiliser le <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribut pour sérialiser une collection.  
  
 [Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Montre comment déboguer le comportement au moment du design de votre contrôle personnalisé.  
  
 [Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Montre comment intégrer étroitement un contrôle composite dans l’environnement de conception.  
  
 [Guide pratique pour créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Fournit une vue d’ensemble des considérations pour l’implémentation d’un contrôle Windows Forms.  
  
 [Guide pratique pour créer des contrôles composites](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Montre comment créer un contrôle en héritant d’un contrôle composite.  
  
 [Guide pratique pour hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Fournit une vue d’ensemble de la procédure de création d’un contrôle composite.  
  
 [Guide pratique pour hériter de contrôles Windows Forms existants](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Montre comment créer un contrôle étendu en héritant de la <xref:System.Windows.Forms.Button> classe de contrôle.  
  
 [Guide pratique pour hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Fournit une vue d’ensemble de la création d’un contrôle étendu.  
  
 [Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Montre comment utiliser le <xref:System.Windows.Forms.Control.Dock%2A> propriété pour aligner votre contrôle sur le bord du formulaire qu’il occupe.  
  
 [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Montre la procédure d’installation de votre contrôle afin qu’il apparaisse dans la boîte de dialogue **Personnaliser la boîte à outils**.  
  
 [Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Montre comment utiliser le <xref:System.Drawing.ToolboxBitmapAttribute> pour afficher une icône en regard de votre contrôle personnalisé dans le **boîte à outils**.  
  
 [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Montre comment utiliser le **conteneur de test UserControl** pour tester le comportement d’un contrôle composite.  
  
 [Erreurs au moment du design dans le Concepteur Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Microsoft Visual Studio en cas d’échec du chargement du Concepteur Windows Forms.  
  
 [Dépannage de la création de contrôles et de composants](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Montre comment diagnostiquer et résoudre les problèmes courants qui peuvent se produire quand vous créez un composant ou un contrôle personnalisé.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 Explique comment créer vos propres contrôles personnalisés avec le .NET Framework.  
  
 [Indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Présente le common language runtime, qui est conçu pour simplifier la création et l’utilisation des composants. Un aspect important de cette simplification est l’interopérabilité améliorée entre les composants écrits à l’aide de différents langages de programmation. La Common Language Specification (CLS) permet de créer des outils et composants fonctionnant avec plusieurs langages de programmation.  
  
 [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Décrit comment activer l’affichage de votre composant ou de votre contrôle dans la boîte de dialogue **Personnaliser la boîte à outils**.
