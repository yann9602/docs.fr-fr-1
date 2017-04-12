---
title: "Création et utilisation de composants en Visual Basic | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9ca4df41897fafc5d7981c85741ae4fa1a8c641f
ms.lasthandoff: 03/13/2017

---
# <a name="creating-and-using-components-in-visual-basic"></a>Création et utilisation de composants en Visual Basic
Un *composant* est une classe qui implémente l’interface <xref:System.ComponentModel.IComponent?displayProperty=fullName> ou qui dérive directement ou indirectement d’une classe implémentant <xref:System.ComponentModel.IComponent>. Un composant [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)] est un objet réutilisable qui peut interagir avec d’autres objets, qui permet de contrôler les ressources externes et qui offre une prise en charge au moment du design.  
  
 Une fonctionnalité importante des composants est leur concevabilité, ce qui signifie qu’une classe qui correspond à un composant peut être utilisée dans l’environnement de développement intégré (IDE) de [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)]. Un composant peut être ajouté à la boîte à outils, faire l’objet d’un glisser-déplacer sur un formulaire et être manipulé sur une aire de conception. Notez que la prise en charge de base au moment du design pour les composants est intégrée au [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)]. Un développeur de composant n’a pas besoin d’effectuer du travail supplémentaire pour tirer parti de la fonctionnalité de base au moment du design.  
  
 Un *contrôle* est similaire à un composant, dans la mesure où tous les deux sont concevables. Toutefois, un contrôle fournit une interface utilisateur, ce qui n’est pas le cas d’un composant. Un contrôle doit dériver de l’une des classes de contrôle de base : <xref:System.Windows.Forms.Control> ou <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Quand créer un composant  
 Si votre classe doit être utilisée sur une aire de conception (telle que le concepteur Windows Forms ou Web Forms), mais qu’elle n’a pas d’interface utilisateur, elle doit être un composant et implémenter <xref:System.ComponentModel.IComponent>, ou dériver d’une classe qui implémente directement ou indirectement <xref:System.ComponentModel.IComponent>.  
  
 Les classes <xref:System.ComponentModel.Component> et <xref:System.ComponentModel.MarshalByValueComponent> constituent des implémentations de base de l’interface <xref:System.ComponentModel.IComponent>. La principale différence entre ces classes est que la classe <xref:System.ComponentModel.Component> est marshalée par référence, tandis que la classe <xref:System.ComponentModel.IComponent> est marshalée par valeur. La liste suivante fournit des indications générales relatives aux implémenteurs.  
  
-   Si votre composant doit être marshalé par référence, dérivez de <xref:System.ComponentModel.Component>.  
  
-   Si votre composant doit être marshalé par valeur, dérivez de <xref:System.ComponentModel.MarshalByValueComponent>.  
  
-   Si votre composant ne peut pas dériver de l’une des implémentations de base en raison d’un héritage unique, implémentez <xref:System.ComponentModel.IComponent>.  
  
 Pour plus d’informations sur la prise en charge au moment du design, consultez [Attributs en mode design pour les composants](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3) et [Extension de la prise en charge au moment du design](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
## <a name="component-classes"></a>Classes de composant  
 L’espace de noms <xref:System.ComponentModel> fournit des classes qui sont utilisées pour implémenter le comportement au moment de l’exécution et au moment du design des composants et des contrôles. Cet espace de noms inclut les classes et les interfaces de base servant à l’implémentation des attributs et des convertisseurs de type, à la liaison à des sources de données et à la gestion des licences des composants.  
  
 Les classes de composant principales sont les suivantes :  
  
-   <xref:System.ComponentModel.Component>. Implémentation de base pour l’interface <xref:System.ComponentModel.IComponent>. Cette classe permet le partage d’objets entre applications.  
  
-   <xref:System.ComponentModel.MarshalByValueComponent>. Implémentation de base pour l’interface <xref:System.ComponentModel.IComponent>.  
  
-   <xref:System.ComponentModel.Container>. Implémentation de base pour l’interface <xref:System.ComponentModel.IContainer>. Cette classe encapsule zéro, un ou plusieurs composants.  
  
 Les classes utilisées pour la gestion des licences des composants sont, entre autres, les suivantes :  
  
-   <xref:System.ComponentModel.License>. Classe de base abstraite pour toutes les licences. Une licence est accordée à une instance spécifique d’un composant.  
  
-   <xref:System.ComponentModel.LicenseManager>. Fournit des propriétés et des méthodes permettant d’ajouter une licence à un composant et de gérer un <xref:System.ComponentModel.LicenseProvider>.  
  
-   <xref:System.ComponentModel.LicenseProvider>. Classe de base abstraite pour l’implémentation d’un fournisseur de licences.  
  
-   <xref:System.ComponentModel.LicenseProviderAttribute>. Spécifie la classe <xref:System.ComponentModel.LicenseProvider> à utiliser avec une classe.  
  
 Classes couramment utilisées pour la description et la persistance des composants.  
  
-   <xref:System.ComponentModel.TypeDescriptor>. Fournit des informations relatives aux caractéristiques d’un composant, telles que ses attributs, ses propriétés et ses événements.  
  
-   <xref:System.ComponentModel.EventDescriptor>. Fournit des informations sur un événement.  
  
-   <xref:System.ComponentModel.PropertyDescriptor>. Fournit des informations sur une propriété.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Comparaison entre classe, composant et contrôle](http://msdn.microsoft.com/library/db8b842e-44d9-40cc-a0f8-70fd189632c3)  
 Définit les concepts de *composant* et de *contrôle*, et décrit les différences entre eux et les classes.  
  
 [Création de composants](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 Documentation de présentation des composants.  
  
 [Procédures pas à pas de la création de composants](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 Liens vers des rubriques fournissant des instructions étape par étape pour la programmation de composants.  
  
 [Classes de composant](http://msdn.microsoft.com/library/ce2e5647-e673-4c2b-8125-ffebbd9d71bc)  
 Explique comment une classe devient un composant, comment exposer les fonctionnalités des composants, comment contrôler l’accès aux composants et comment contrôler la création des instances de composants.  
  
 [Dépannage de la création de contrôles et de composants](http://msdn.microsoft.com/library/e9c8c099-2271-4737-882f-50f336c7a55e)  
 Explique comment résoudre certains problèmes courants.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : accéder à la prise en charge au moment du design dans les Windows Forms](http://msdn.microsoft.com/library/a84f8579-1f47-41b9-ba37-69030b0aff09)   
 [Comment : étendre l’apparence et le comportement des contrôles en mode design](http://msdn.microsoft.com/library/68f85054-2253-47f5-a4f2-3f1ac8c9f27b)   
 [Comment : effectuer une initialisation personnalisée pour les contrôles en mode design](http://msdn.microsoft.com/library/914eaa03-092f-4556-9160-b8a2a40641d9)
