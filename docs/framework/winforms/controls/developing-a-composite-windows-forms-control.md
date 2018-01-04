---
title: "Développement d'un contrôle Windows Forms composite"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b98ba10e1c865417b9e844c4d5c31334f763e1b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="developing-a-composite-windows-forms-control"></a>Développement d'un contrôle Windows Forms composite
Vous pouvez développer un contrôle Windows Forms composite en combinant d'autres contrôles Windows Forms. Contrôles composites qui dérivent <xref:System.Web.UI.UserControl> sont appelés contrôles utilisateur. La classe de base, <xref:System.Windows.Forms.UserControl>, fournit le routage clavier pour les contrôles enfants, ce qui permet de garantir que les contrôles enfants peuvent recevoir le focus. Pour obtenir un exemple d’un contrôle utilisateur, consultez la <xref:System.Windows.Forms.UserControl> sample dans [Comment : appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
 Le Concepteur Windows Forms dans [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] fournit une prise en charge enrichie au moment du design pour la création de contrôles utilisateur.  
  
-   [Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [Procédure pas à pas : héritage d’un contrôle Windows Forms à l’aide de Visual C#](http://msdn.microsoft.com/en-us/09476da0-8d4c-4a4c-b969-649519dfb438))  
  
-   [Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [Guide pratique pour hériter de contrôles Windows Forms existants](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [Guide pratique pour hériter de la classe du contrôle](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [Guide pratique pour tester le comportement d'un UserControl au moment de l'exécution](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [Comment : hériter de la classe UserControl](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [Guide pratique pour créer des contrôles pour des Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [Guide pratique pour créer des contrôles composites](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [Procédure pas à pas : création d’un contrôle composite à l’aide de Visual C#](http://msdn.microsoft.com/en-us/f88481a8-c746-4a36-9479-374ce5f2e91f))  
  
-   [Procédure pas à pas : héritage à partir d’un contrôle Windows Forms à l’aide de Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [Guide pratique pour créer un contrôle Windows Forms qui bénéficie des fonctionnalités au moment du design](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [Comment : créer un contrôle Windows Forms qui bénéficie des fonctionnalités au moment du design](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour appliquer des attributs dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
