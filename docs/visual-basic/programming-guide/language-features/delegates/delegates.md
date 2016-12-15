---
title: "Delegates (Visual Basic) | Microsoft Docs"
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
  - "delegates [Visual Basic]"
  - "Visual Basic code, delegates"
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegates (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les délégués sont des objets qui font référence aux méthodes.  Ils sont parfois décrits comme des *pointeurs fonction de type sécurisé* car ils sont comparables aux pointeurs fonction utilisés dans d'autres langages de programmation.  Mais contrairement aux pointeurs de fonction, les délégués [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sont un type référence basé sur la classe <xref:System.Delegate?displayProperty=fullName>.  Les délégués peuvent faire référence à des méthodes partagées \(méthodes qui peuvent être appelées sans une instance spécifique d'une classe\) et à des méthodes d'instance.  
  
## Délégués et événements  
 Les délégués sont utiles lorsque vous avez besoin d'un intermédiaire entre une procédure appelante et la procédure appelée.  Vous pouvez, par exemple, souhaiter un objet qui déclenche des événements pour pouvoir appeler différents gestionnaires d'événements dans des circonstances différentes.  Malheureusement, l'objet qui déclenche les événements ne peut pas savoir par avance quel gestionnaire d'événements gère un événement spécifique.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous laisse associer dynamiquement les gestionnaires d'événements aux événements en créant automatiquement un délégué lorsque vous utilisez l'instruction `AddHandler`.  Au moment de l'exécution, le délégué transmet les appels au gestionnaire d'événements approprié.  
  
 Bien que vous puissiez créer vos propres délégués, c'est [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qui se charge le plus souvent de créer le délégué et de gérer tous les détails à votre place.  Par exemple, une instruction `Event` définit implicitement une classe déléguée appelée `<EventName>EventHandler` en tant que classe imbriquée de la classe contenant l'instruction `Event`, ce avec la même signature que l'événement.  L'instruction `AddressOf` crée implicitement une instance d'un délégué qui fait référence à une procédure spécifique.  Les deux lignes de code suivantes sont équivalentes.  Sur la première ligne, vous pouvez voir la création explicite d'une instance d'`Eventhandler`, avec une référence à la méthode `Button1_Click` envoyée comme argument.  La deuxième ligne offre un moyen plus pratique d'effectuer la même opération.  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]  
  
 Vous pouvez utiliser la méthode abrégée de création de délégués à chaque fois que le compilateur peut déterminer le type du délégué en fonction du contexte.  
  
## Déclaration d'événements utilisant un type délégué existant  
 Dans certaines situations, vous pouvez choisir de déclarer un événement pour utiliser un type délégué existant comme son délégué sous\-jacent.  La syntaxe ci\-dessous vous indique comment procéder :  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]  
  
 Cela peut vous être utile lorsque vous voulez router plusieurs événements vers le même gestionnaire.  
  
## Variables et paramètres de délégués  
 Vous pouvez utiliser des délégués pour d'autres tâches non liées à des événements, telles que le modèle de thread libre, ou avec les procédures qui doivent appeler différentes versions de fonctions au moment de l'exécution.  
  
 Supposons, par exemple, que vous ayez une application de gestion de petites annonces contenant une zone de liste affichant les noms de voitures.  Les annonces sont triées par titre, lequel correspond normalement à la marque de la voiture.  Un problème peut néanmoins se poser lorsque, pour certaines voitures, la marque est précédée de l'année de mise en circulation.  Ce cas représente un vrai problème, car la fonctionnalité de tri intégrée de la zone de liste base son tri sur les codes de caractères ; elle commence donc par trier en tête de liste toutes les annonces dont l'intitulé commence par des dates pour ensuite traiter les annonces dont l'intitulé commence par la marque.  
  
 Pour résoudre ce problème, vous pouvez créer une procédure de tri dans une classe qui utilise le tri alphabétique standard dans la plupart des zones de liste, mais qui est capable, au moment de l'exécution, de passer à la procédure de tri personnalisée définie pour les petites annonces concernant les voitures.  Pour ce faire, vous faites appel à des délégués pour passer la procédure de tri personnalisée à la classe de tri au moment de l'exécution.  
  
## Expressions AddressOf et lambda  
 Chaque classe déléguée définit un constructeur auquel les caractéristiques d'une méthode objet sont passées.  Un argument à un constructeur délégué doit correspondre à une référence à une méthode ou à une expression lambda.  
  
 Pour spécifier une référence à une méthode, utilisez la syntaxe suivante :  
  
 `AddressOf` \[`expression`.\]`methodName`  
  
 Le type de l'`expression` au moment de la compilation doit correspondre au nom d'une classe ou d'une interface qui contient une méthode avec le nom spécifié dont la signature correspond à celle de la classe déléguée.  La méthode `methodName` peut être soit une méthode partagée, soit une méthode d'instance.  `methodName` n'est pas facultatif, même si vous créez un délégué pour la méthode par défaut de la classe.  
  
 Pour spécifier une expression lambda, utilisez la syntaxe suivante :  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 L'exemple suivant affiche à la fois des expressions lambda et des expressions `AddressOf` utilisées pour spécifier la référence pour un délégué.  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]  
  
 La signature de la fonction doit correspondre à celle du type délégué.  Pour plus d'informations sur les expressions lambda, consultez [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  Pour obtenir plus d'exemples d'expressions lambda et d'assignations `AddressOf` aux délégués, consultez [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|Fournit un exemple qui montre comment associer une méthode à un délégué, puis comment appeler cette méthode par le biais du délégué.|  
|[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|Illustre comment utiliser des délégués pour passer d'une procédure à une autre.|  
|[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|Décrit la façon dont vous pouvez assigner des sous\-routines et des fonctions aux délégués ou aux gestionnaires même lorsque leurs signatures ne sont pas identiques.|  
|[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)|Fournit une vue d'ensemble des événements dans Visual Basic.|