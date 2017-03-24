---
title: "Propriétés et méthodes (Visual Basic) surchargées | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names, multiple procedures with same
- procedures, mulltiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword, overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6f379f04ca9b75161baf2bf2c33e87f05a9edf97
ms.lasthandoff: 03/13/2017

---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Propriétés et méthodes surchargées (Visual Basic)
La surcharge est la création de plusieurs procédures, constructeurs d’instance ou la propriété dans une classe portant le même nom mais différents types d’arguments.  
  
## <a name="overloading-usage"></a>Utilisation de la surcharge  
 La surcharge est particulièrement utile lorsque votre modèle objet impose l’utilisation de noms identiques pour les procédures qui opèrent sur les différents types de données. Par exemple, une classe qui peut afficher plusieurs types de données différents peut avoir `Display` des procédures qui ressemblent à ceci :  
  
 [!code-vb[VbVbalrOOP&#64;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_1.vb)]  
  
 Sans surcharge, vous devez créer des noms distincts pour chaque procédure, même si celles-ci effectuent la même chose, comme indiqué ci-après :  
  
 [!code-vb[VbVbalrOOP&#65;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_2.vb)]  
  
 La surcharge rend plus facile à utiliser des propriétés ou méthodes, car elle fournit un choix de types de données qui peut être utilisé. Par exemple, surchargées `Display` méthode décrite ci-dessus peut être appelée avec des lignes de code suivantes :  
  
 [!code-vb[VbVbalrOOP&#66;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_3.vb)]  
  
 Au moment de l’exécution [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] spécifier appelle la procédure correcte selon les types de données des paramètres.  
  
## <a name="overloading-rules"></a>Règles de surcharge  
 Vous créez un membre surchargé d’une classe en ajoutant deux ou plusieurs propriétés ou méthodes portant le même nom. À l’exception des membres dérivés surchargés, chaque membre surchargé doit posséder des listes de paramètres différentes, et les éléments suivants ne peut pas être utilisés comme une fonctionnalité de différenciation lors de la surcharge d’une propriété ou une procédure :  
  
-   Modificateurs, tels que `ByVal` ou `ByRef`, qui s’appliquent à un membre, ou des paramètres du membre.  
  
-   Noms des paramètres  
  
-   Types de retour des procédures  
  
 Le `Overloads` mot clé est facultatif lors de la surcharge, mais si une surcharge membre utilise le `Overloads` (mot clé), puis tous les autres membres surchargés portant le même nom doivent également spécifier ce mot clé.  
  
 Les classes dérivées peuvent surcharger les membres hérités avec des membres qui ont des paramètres identiques et les types de paramètre, un processus appelé *l’occultation par le nom et la signature*. Si le `Overloads` mot clé est utilisée lors de l’occultation par le nom et la signature, implémentation de la classe dérivée du membre sera utilisée au lieu de l’implémentation dans la classe de base, et toutes les autres surcharges de ce membre seront disponibles pour les instances de la classe dérivée.  
  
 Si le `Overloads` mot clé est omis lors de la surcharge d’un membre hérité avec un membre qui a des paramètres identiques et types de paramètres, puis la surcharge est appelée *occultation par le nom*. Occultation par le nom remplace l’implémentation héritée d’un membre et rend toutes les autres surcharges indisponibles pour les instances de la classe dérivée et ses descendants.  
  
 Le `Overloads` et `Shadows` modificateurs ne peuvent pas être utilisés avec la même propriété ou méthode.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant crée des méthodes surchargées qui acceptent une `String` ou `Decimal` représentation d’un montant en dollars et la retournent une chaîne comportant la taxe.  
  
##### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Pour utiliser cet exemple pour créer une méthode surchargée  
  
1.  Ouvrez un nouveau projet et ajoutez une classe nommée `TaxClass`.  
  
2.  Ajoutez le code suivant à la classe `TaxClass`.  
  
     [!code-vb[VbVbalrOOP&#67;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_4.vb)]  
  
3.  Ajoutez la procédure suivante à votre formulaire.  
  
     [!code-vb[VbVbalrOOP&#68;](../../../../visual-basic/misc/codesnippet/VisualBasic/overloaded-properties-and-methods_5.vb)]  
  
4.  Ajouter un bouton à votre formulaire et appelez la `ShowTax` procédure à partir de la `Button1_Click` les événements du bouton.  
  
5.  Exécutez le projet et cliquez sur le bouton du formulaire pour tester surchargées `ShowTax` procédure.  
  
 Au moment de l’exécution, le compilateur sélectionne la fonction surchargée adéquate qui correspond aux paramètres utilisés. Lorsque vous cliquez sur le bouton, la méthode surchargée est appelée en premier avec un `Price` paramètre qui est une chaîne et le message « prix est une chaîne. La taxe est $5,12" s’affiche. `TaxAmount`est appelé avec un `Decimal` de valeur pour la deuxième fois et le message, « prix est un nombre décimal. La taxe est $5,12" s’affiche.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Principes fondamentaux de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [Ombres](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)   
 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)   
 [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
