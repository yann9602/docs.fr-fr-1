---
title: "Creating and Using Components in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "components [Visual Basic]"
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Creating and Using Components in Visual Basic
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Un *composant* est une classe qui implémente l'interface <xref:System.ComponentModel.IComponent?displayProperty=fullName> ou qui dérive directement ou indirectement d'une classe qui implémente <xref:System.ComponentModel.IComponent>.  Un composant du [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] est un objet réutilisable qui peut interagir avec d'autres objets, permet de contrôler les ressources externes et offre une prise en charge au moment du design.  
  
 Une fonctionnalité importante des composants est leur concevabilité, ce qui signifie qu'une classe qui correspond à un composant peut être utilisée dans l'environnement de développement intégré \(IDE, Integrated Development Environment\) [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)].  Un composant peut être ajouté à la Boîte à outils, faire l'objet d'un glisser\-déplacer sur un formulaire et être manipulé sur une aire de conception.  Notez que la prise en charge de base au moment du design pour les composants est intégrée au [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] ; un développeur de composant ne doit effectuer aucun travail supplémentaire pour tirer parti de la fonctionnalité de base au moment du design.  
  
 Un *contrôle* est similaire à un composant, dans la mesure où tous les deux sont concevables.  Toutefois, un contrôle fournit une interface utilisateur, ce qui n'est pas le cas d'un composant.  Un contrôle doit dériver de l'une des classes de contrôle de base : <xref:System.Windows.Forms.Control> ou <xref:System.Web.UI.Control>.  
  
## Moment de création d'un composant  
 Si votre classe doit être utilisée sur une aire de conception \(telle que le concepteur Windows Forms ou Web Forms\), et qu'elle n'a pas d'interface, elle doit être un composant et implémenter <xref:System.ComponentModel.IComponent> ou dériver d'une classe qui implémente directement ou indirectement <xref:System.ComponentModel.IComponent>.  
  
 Les classes <xref:System.ComponentModel.Component> et <xref:System.ComponentModel.MarshalByValueComponent> constituent des implémentations de base de l'interface <xref:System.ComponentModel.IComponent>.  La différence principale entre ces classes est que la classe <xref:System.ComponentModel.Component> est marshalée par référence, tandis que la classe <xref:System.ComponentModel.IComponent> est marshalée par valeur.  La liste suivante fournit des indications générales pour les implémenteurs.  
  
-   Si votre composant doit être marshalé par référence, dérivez de <xref:System.ComponentModel.Component>.  
  
-   Si votre composant doit être marshalé par valeur, dérivez de <xref:System.ComponentModel.MarshalByValueComponent>.  
  
-   Si votre composant ne peut pas dériver de l'une des implémentations de base en raison d'un héritage unique, implémentez <xref:System.ComponentModel.IComponent>.  
  
 Pour plus d'informations sur la prise en charge au moment du design, consultez [Design\-Time Attributes for Components](../Topic/Design-Time%20Attributes%20for%20Components.md) et [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
## Classes de composant  
 L'espace de noms <xref:System.ComponentModel> fournit des classes qui sont utilisées pour implémenter le comportement au moment de l'exécution et au moment du design des composants et des contrôles.  Cet espace de noms inclut les classes de base et les interfaces pour l'implémentation des attributs et des convertisseurs de type, pour la liaison à des sources de données et pour la licence des composants.  
  
 Les principales classes de composant sont les suivantes :  
  
-   <xref:System.ComponentModel.Component>.  Implémentation de base pour l'interface <xref:System.ComponentModel.IComponent>.  Cette classe permet le partage d'objets entre applications.  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>.  Implémentation de base pour l'interface <xref:System.ComponentModel.IComponent>.  
  
-   <xref:System.ComponentModel.Container>.  Implémentation de base pour l'interface <xref:System.ComponentModel.IContainer>.  Cette classe encapsule aucun ou plusieurs composants.  
  
 Les classes utilisées pour la licence des composants sont entre autres les suivantes :  
  
-   <xref:System.ComponentModel.License>.  Classe de base abstraite pour toutes les licences.  Une licence est accordée à une instance spécifique d'un composant.  
  
-   <xref:System.ComponentModel.LicenseManager>.  Fournit des propriétés et des méthodes permettant d'ajouter une licence à un composant et de gérer un <xref:System.ComponentModel.LicenseProvider>.  
  
-   <xref:System.ComponentModel.LicenseProvider>.  Classe de base abstraite pour l'implémentation d'un fournisseur de licences.  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>.  Spécifie la classe <xref:System.ComponentModel.LicenseProvider> à utiliser avec une classe.  
  
 Classes fréquemment utilisées pour la description et la persistance des composants.  
  
-   <xref:System.ComponentModel.TypeDescriptor>.  Fournit des informations relatives aux caractéristiques d'un composant telles que ses attributs, ses propriétés et ses événements.  
  
-   <xref:System.ComponentModel.EventDescriptor>.  Fournit des informations sur un événement.  
  
-   <xref:System.ComponentModel.PropertyDescriptor>.  Fournit des informations sur une propriété.  
  
## Rubriques connexes  
 [Class vs. Component vs. Control](../Topic/Class%20vs.%20Component%20vs.%20Control.md)  
 Définit le *composant* et le *contrôle* et décrit les différences entre eux et les classes.  
  
 [Component Authoring](../Topic/Component%20Authoring.md)  
 Documentation pour la mise en route des composants.  
  
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)  
 Propose des liens vers des rubriques fournissant des instructions étape par étape sur la programmation de composants.  
  
 [Component Classes](../Topic/Component%20Classes.md)  
 Explique comment une classe devient un composant, comment exposer les fonctionnalités des composants et comment contrôler l'accès aux composants ainsi que la création des instances de composants.  
  
 [Dépannage de la création de contrôles et de composants](../Topic/Troubleshooting%20Control%20and%20Component%20Authoring.md)  
 Explique comment résoudre certains problèmes courants.  
  
## Voir aussi  
 [How to: Access Design\-Time Support in Windows Forms](../Topic/How%20to:%20Access%20Design-Time%20Support%20in%20Windows%20Forms.md)   
 [How to: Extend the Appearance and Behavior of Controls in Design Mode](../Topic/How%20to:%20Extend%20the%20Appearance%20and%20Behavior%20of%20Controls%20in%20Design%20Mode.md)   
 [How to: Perform Custom Initialization for Controls in Design Mode](../Topic/How%20to:%20Perform%20Custom%20Initialization%20for%20Controls%20in%20Design%20Mode.md)