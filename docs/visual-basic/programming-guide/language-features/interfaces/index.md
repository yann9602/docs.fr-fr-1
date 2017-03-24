---
title: "Interfaces (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, interfaces"
  - "interfaces, Visual Basic"
  - "interfaces"
  - "interfaces [Visual Basic]"
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Interfaces (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les *interfaces* définissent les propriétés, méthodes et événements qui peuvent être implémentés par les classes.  Les interfaces vous permettent de définir des fonctionnalités sous forme de petits groupes de propriétés, méthodes et événements étroitement liés. Les risques d'incompatibilité sont ainsi limités, car vous pouvez développer des implémentations avancées pour vos interfaces sans mettre en danger le code existant.  Vous pouvez ajouter de nouvelles fonctionnalités à tout moment en développant des interfaces et implémentations supplémentaires.  
  
 Il existe plusieurs autres raisons qui peuvent vous amener à préférer les interfaces à l'héritage de classes :  
  
-   Les interfaces sont mieux adaptées aux situations dans lesquelles vos applications exigent que de nombreux types d'objet éventuellement sans relation fournissent certaines fonctionnalités.  
  
-   Les interfaces sont plus flexibles que les classes de base, car vous pouvez définir une implémentation unique susceptible d'implémenter plusieurs interfaces.  
  
-   Les interfaces sont plus indiquées dans les cas où vous n'avez pas besoin d'hériter d'une implémentation à partir d'une classe de base.  
  
-   Les interfaces sont utiles quand vous ne pouvez pas utiliser l'héritage de classes.  Par exemple, les structures ne peuvent pas hériter des classes, mais elles peuvent implémenter des interfaces.  
  
## Déclaration des interfaces  
 Les définitions d'interfaces figurent entre les instructions `Interface` et `End Interface`.  À la suite de l'instruction `Interface`, vous pouvez ajouter une instruction `Inherits` facultative qui répertorie une ou plusieurs interfaces héritées.  Les instructions `Inherits` doivent précéder toutes les autres instructions dans la déclaration, à l'exception des commentaires.  Les autres instructions figurant dans la définition de l'interface doivent être `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure` et `Enum`.  Les interfaces ne peuvent pas contenir de code d'implémentation ni d'instructions associées au code d'implémentation, telles que `End Sub` ou `End Property`.  
  
 Dans un espace de noms, les instructions d'interface sont `Friend` par défaut, mais elles peuvent également être déclarées explicitement comme `Public` ou `Friend`.  Les interfaces définies dans des classes, des modules, des interfaces et des structures sont `Public` par défaut, mais elles peuvent également être déclarées explicitement comme `Public`, `Friend`, `Protected` ou `Private`.  
  
> [!NOTE]
>  Le mot clé `Shadows` peut être appliqué à tous les membres d'interface.  Le mot clé `Overloads` peut être appliqué aux instructions `Sub`, `Function` et `Property` déclarées dans une définition d'interface.  En outre, les instructions `Property` peuvent posséder les modificateurs `Default`, `ReadOnly` ou `WriteOnly`.  Aucun autre modificateur \(`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride` ni `Overridable`\) n'est autorisé.  Pour plus d'informations, consultez [Declaration Contexts and Default Access Levels](../../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Par exemple, le code suivant définit une interface avec une fonction, une propriété et un événement.  
  
 [!code-vb[VbVbalrOOP#17](../../../../visual-basic/misc/codesnippet/VisualBasic/index_1.vb)]  
  
## Implémentation des interfaces  
 Le mot réservé [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] `Implements` est utilisé de deux manières.  L'instruction `Implements` signifie qu'une classe ou une structure implémente une interface.  Le mot clé `Implements` signifie qu'un membre de classe ou un membre de structure implémente un membre d'interface spécifique.  
  
### Implements, instruction  
 Si une classe ou une structure implémente une ou plusieurs interfaces, elle doit inclure l'instruction `Implements` immédiatement après l'instruction `Class` ou `Structure`.  L'instruction `Implements` requiert une liste séparée par des virgules des interfaces qui doivent être implémentées par une classe.  La classe ou la structure doit implémenter tous les membres d'interface à l'aide du mot clé `Implements`.  
  
### Implements, mot clé  
 Le mot clé `Implements` requiert une liste séparée par des virgules des membres d'interface qui doivent être implémentés.  En règle générale, un seul membre d'interface est spécifié, mais vous pouvez spécifier plusieurs membres.  La spécification d'un membre d'interface se compose du nom de l'interface \(qui doit être spécifié dans une instruction implements dans la classe\), d'un point et du nom de la fonction membre, de la propriété ou de l'événement à implémenter.  Le nom d'un membre qui implémente un membre d'interface peut utiliser n'importe quel identificateur conforme et n'est pas limité à la convention `InterfaceName_MethodName` utilisée dans les versions antérieures de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 Par exemple, le code suivant montre comment déclarer une sous\-routine nommée `Sub1` qui implémente une méthode d'une interface :  
  
 [!code-vb[VbVbalrOOP#69](../../../../visual-basic/misc/codesnippet/VisualBasic/index_2.vb)]  
  
 Les types de paramètres et les types de retour du membre qui implémente doivent correspondre à la déclaration du membre ou de la propriété d'interface dans l'interface.  La façon la plus répandue d'implémenter un élément d'interface consiste à utiliser un membre portant le même nom que l'interface, comme dans l'exemple précédent.  
  
 Pour déclarer l'implémentation d'une méthode d'interface, vous pouvez utiliser tous les attributs conformes dans les déclarations de méthodes d'instances, y compris `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default` et `Static`.  L'attribut `Shared` n'est pas conforme car il définit une classe à la place d'une méthode d'instance.  
  
 `Implements` permet également d'écrire une méthode unique implémentant plusieurs méthodes définies dans une interface, comme dans l'exemple suivant :  
  
 [!code-vb[VbVbalrOOP#70](../../../../visual-basic/misc/codesnippet/VisualBasic/index_3.vb)]  
  
 Vous pouvez utiliser un membre privé pour implémenter un membre d'interface.  Quand un membre privé implémente un membre d'interface, ce membre devient disponible via l'interface, même s'il n'est pas directement disponible avec les variables objets pour la classe.  
  
### Exemples d'implémentation d'interface  
 Les classes qui implémentent une interface doivent implémenter toutes ses propriétés et méthodes et tous ses événements.  
  
 L'exemple suivant définit deux interfaces.  La seconde interface, `Interface2`, hérite d'`Interface1` et définit une propriété et une méthode supplémentaires.  
  
 [!code-vb[VbVbalrOOP#39](../../../../visual-basic/misc/codesnippet/VisualBasic/index_4.vb)]  
  
 L'exemple suivant implémente `Interface1`, l'interface définie dans l'exemple précédent :  
  
 [!code-vb[VbVbalrOOP#40](../../../../visual-basic/misc/codesnippet/VisualBasic/index_5.vb)]  
  
 Ce dernier exemple implémente `Interface2`, y compris une méthode héritée d'`Interface1` :  
  
 [!code-vb[VbVbalrOOP#41](../../../../visual-basic/misc/codesnippet/VisualBasic/index_6.vb)]  
  
 Vous pouvez implémenter une propriété en lecture seule à l'aide d'une propriété readwrite \(autrement dit, vous n'êtes pas tenu de la déclarer en lecture seule dans la classe d'implémentation\).  L'implémentation d'une interface promet d'implémenter au moins les membres que l'interface déclare, mais vous pouvez offrir davantage de fonctionnalités, comme par exemple permettre l'accès en écriture à votre propriété.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Walkthrough: Creating and Implementing Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)|Fournit une procédure détaillée qui vous guide tout au long du processus de définition et d'implémentation de votre propre interface.|  
|[Variance dans les interfaces génériques](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)|Décrit la covariance et la contravariance dans les interfaces génériques et fournit la liste des interfaces génériques de type variant dans le .NET Framework.|