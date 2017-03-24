---
title: "Comment : utiliser une classe générique (Visual Basic) | Documents Microsoft"
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
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters, data type
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eeb55be1c368e9ca80ab94de814a5e2ba9bc9f1f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Comment : utiliser une classe générique (Visual Basic)
Une classe qui accepte des *paramètres de type* est appelée *classe générique*. Si vous utilisez une classe générique, vous pouvez générer une *classe construite* à partir de celle-ci en fournissant un *argument de type* pour chacun de ces paramètres. Vous pouvez ensuite déclarer une variable du type classe construite, et vous pouvez créer une instance de la classe construite et l’assigner à cette variable.  
  
 En plus des classes, vous pouvez définir et utiliser des structures, interfaces, procédures et délégués génériques.  
  
 La procédure suivante prend une classe générique définie dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] et crée une instance à partir d’elle.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Pour utiliser une classe qui prend un paramètre de type  
  
1.  Au début de votre fichier source, incluez un [Imports, instruction (.NET Namespace et Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer le <xref:System.Collections.Generic?displayProperty=fullName>espace de noms.</xref:System.Collections.Generic?displayProperty=fullName> Cela vous permet de faire référence à la <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>classe sans devoir qualifier pleinement pour la différencier des autres classes de file d’attente telles que <xref:System.Collections.Queue?displayProperty=fullName>.</xref:System.Collections.Queue?displayProperty=fullName> </xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
2.  Créez l’objet de façon normale, mais ajoutez `(Of` `type``)` juste après le nom de la classe.  
  
     L’exemple suivant utilise la même classe (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) pour créer deux objets de file d’attente qui contiennent des éléments de différents types de données.</xref:System.Collections.Generic.Queue%601?displayProperty=fullName> Il ajoute des éléments à la fin de chaque file d’attente, puis supprime et affiche les éléments du début de chaque file d’attente.  
  
     [!code-vb[VbVbalrDataTypes&#9;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Comment : définir une classe qui peut fournir des fonctionnalités identiques pour différents types de données](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
