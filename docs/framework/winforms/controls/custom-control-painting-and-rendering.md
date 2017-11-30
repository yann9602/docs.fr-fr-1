---
title: "Peinture et rendu personnalisés des contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: babf3d235f4cca61ad6d0e5fdc4e6b6146c7d060
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="custom-control-painting-and-rendering"></a>Peinture et rendu personnalisés des contrôles
La peinture personnalisée des contrôles est une des nombreuses tâches compliquées facilitées par le .NET Framework. Lorsque vous créez un contrôle personnalisé, vous disposez de nombreuses options d’apparence de graphique de votre contrôle. Si vous êtes en train de créer un contrôle qui hérite de la `Control`, vous devez fournir le code qui permet à votre contrôle afficher sa représentation sous forme graphique. Si vous créez un contrôle utilisateur en héritant de la `UserControl`, ou sur l’un des contrôles Windows Forms, vous pouvez substituer la représentation graphique standard et fournir votre propre code graphique. Si vous souhaitez fournir un rendu personnalisé pour les contrôles constitutifs d’un `UserControl` vous êtes en train de créer, vos options sont plus limitées, mais toujours autorisant un large éventail de possibilités de graphiques pour vos applications et de contrôles.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Rendu d'un contrôle Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Montre comment programmer la logique qui affiche un contrôle.  
  
 [Contrôles dessinés par l’utilisateur](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Donne une vue d’ensemble des étapes impliquées dans l’écriture et la substitution de code de rendu de votre contrôle.  
  
 [Contrôles constitutifs](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Décrit comment implémenter le code de rendu personnalisé pour les contrôles constitutifs dans vos contrôles utilisateur et les formulaires.  
  
 [Guide pratique pour rendre votre contrôle invisible au moment de l'exécution](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Montre comment utiliser le <xref:System.Windows.Forms.Control.Visible%2A> propriété à masquer et afficher un contrôle.  
  
 [Guide pratique pour affecter un arrière-plan transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Montre comment utiliser la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour créer une couleur d’arrière-plan qui est opaque, transparente ou partiellement transparente.  
  
 [Rendu des contrôles avec les styles visuels](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Montre comment restituer les contrôles à l’aide de styles visuels dans les systèmes d’exploitation qui les prennent en charge.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.Control>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.UserControl>  
 Décrit cette classe et propose des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Décrit cette méthode.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour créer des objets graphiques pour le dessin](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Introduit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionnalités graphiques à partir d’un point de vue et donne de liens Visual Studio pour plus d’informations.  
  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Décrit les types de contrôles personnalisés, que vous pouvez créer.
