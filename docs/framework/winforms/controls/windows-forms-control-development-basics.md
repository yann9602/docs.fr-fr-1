---
title: "Concepts de base du développement de contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf06f4dc0d8c70ae85d5add5a2fee078238d5e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-control-development-basics"></a>Concepts de base du développement de contrôles Windows Forms
Un contrôle Windows Forms est une classe qui dérive directement ou indirectement de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. La liste suivante décrit les scénarios courants pour le développement de contrôles Windows Forms :  
  
-   Combinaison de contrôles existants pour créer un contrôle composite.  
  
     Contrôles composites encapsulent une interface utilisateur qui peut être réutilisée comme un contrôle. Un exemple d’un contrôle composite est un contrôle qui se compose d’une zone de texte et un bouton de réinitialisation. Les concepteurs visuels offrent une prise en charge complète pour la création de contrôles composites. Pour créer un contrôle composite, dérivez de <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. La classe de base <xref:System.Windows.Forms.UserControl> fournit le routage clavier pour les contrôles enfants et permet des contrôles enfants fonctionner en tant que groupe. Pour plus d’informations, consultez l’article [Développement d’un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Extension d’un contrôle existant pour le personnaliser ou pour ajouter des fonctionnalités.  
  
     Un bouton dont la couleur ne peut pas être modifiée et un bouton qui a une propriété supplémentaire qui effectue le suivi du nombre de fois où il a été activé sont des exemples de contrôles étendus. Vous pouvez personnaliser n’importe quel contrôle Windows Forms par dérivation à partir de celui-ci et en substituant ou en ajoutant des propriétés, méthodes et événements.  
  
-   Création d’un contrôle qui n’a pas été combiner ou étendre des contrôles existants.  
  
     Dans ce scénario, dérivez votre contrôle de la classe de base <xref:System.Windows.Forms.Control>. Vous pouvez ajouter ainsi que substituer des propriétés, méthodes et événements de la classe de base. Pour commencer, consultez [Comment : développer un contrôle Windows Forms Simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 La classe de base pour les contrôles Windows Forms, <xref:System.Windows.Forms.Control>, fournit les éléments nécessaires à l’affichage dans les applications Windows côté client. <xref:System.Windows.Forms.Control>fournit un handle de fenêtre, gère le routage des messages et fournit des événements de souris et clavier ainsi que de nombreux autres utilisateur événements d’interface. Il fournit une représentation avancée et possède des propriétés spécifiques à l’affichage visuel, tel que <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>et bien d’autres. En outre, il assure la sécurité, de thread et l’interopérabilité avec les contrôles ActiveX. Étant donné que la majeure partie de l’infrastructure est fournie par la classe de base, il est relativement facile de développer vos propres contrôles Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Développement d’un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Guide pratique pour créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
