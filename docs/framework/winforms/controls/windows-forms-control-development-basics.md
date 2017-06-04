---
title: "Concepts de base du d&#233;veloppement de contr&#244;les Windows Forms | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), types de dérivation"
  - "concepts de programmation, contrôles Windows Forms"
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Concepts de base du d&#233;veloppement de contr&#244;les Windows Forms
Un contrôle Windows Forms est une classe qui dérive directement ou indirectement de <xref:System.Windows.Forms.Control?displayProperty=fullName>.  La liste suivante décrit les scénarios courants de développement de contrôles Windows Forms :  
  
-   Combinaison de contrôles existants pour créer un contrôle composite.  
  
     Les contrôles composites encapsulent une interface utilisateur qui peut être réutilisée comme contrôle.  Citons comme exemple de contrôle composite un contrôle constitué d'une zone de texte et d'un bouton de réinitialisation.  Les concepteurs visuels offrent une prise en charge étendue de la création de contrôles composites.  Pour créer un contrôle composite, dérivez de <xref:System.Windows.Forms.UserControl?displayProperty=fullName>.  La classe de base <xref:System.Windows.Forms.UserControl> fournit le routage clavier pour les contrôles enfants et permet à ces derniers de fonctionner en tant que groupe.  Pour plus d'informations, consultez [Développement d'un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Extension d'un contrôle existant pour le personnaliser ou lui ajouter des fonctionnalités.  
  
     Citons comme exemples de contrôles étendus un bouton dont la couleur ne peut pas être modifiée et un bouton possédant une propriété supplémentaire qui effectue le suivi du nombre de clics.  Vous pouvez personnaliser un contrôle Windows Forms en le dérivant et en substituant ou en ajoutant des propriétés, des méthodes et des événements.  
  
-   Création d'un contrôle qui ne combine ou n'étend pas de contrôles existants.  
  
     Dans ce scénario, dérivez votre contrôle de la classe de base <xref:System.Windows.Forms.Control>.  Vous pouvez ajouter ainsi que substituer des propriétés, méthodes et événements de la classe de base.  Pour commencer, consultez [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 La classe de base des contrôles Windows Forms, <xref:System.Windows.Forms.Control>, fournit les fondations nécessaires à l'affichage dans les applications Windows côté client.  <xref:System.Windows.Forms.Control> fournit un handle de fenêtre, gère le routage des messages et fournit des événements de souris et de clavier ainsi que de nombreux autres événements d'interface utilisateur.  Il fournit une représentation avancée et possède des propriétés spécifiques à l'affichage visuel, telles que <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A> et bien d'autres.  En outre, il assure la sécurité, la prise en charge des threads et l'interopérabilité avec les contrôles ActiveX.  Comme une grande partie de l'infrastructure est fournie par la classe de base, il est relativement aisé de développer vos propres contrôles Windows Forms.  
  
## Voir aussi  
 [Comment : développer un contrôle Windows Forms simple](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)   
 [Développement d'un contrôle Windows Forms composite](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)   
 [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)   
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)