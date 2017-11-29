---
title: "Types valeur et types référence"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b54945d27d186771e8b5353e753afd74c56d71b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="value-types-and-reference-types"></a>Types valeur et types référence
En Visual Basic, les types de données sont implémentés en fonction de leur classification. Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] des types de données peuvent être classés en fonction du fait qu’une variable d’un type particulier enregistre ses propres données ou un pointeur vers les données. Si elle enregistre ses propres données, il est un *type valeur*; si elle contient un pointeur vers les données ailleurs dans la mémoire, il s’agit d’un *type référence*.  
  
## <a name="value-types"></a>Types valeur  
 Un type de données est un *type valeur* s’il conserve des données au sein de sa propre allocation de mémoire. Types valeur sont les suivantes :  
  
-   Tous les types de données numériques  
  
-   `Boolean`, `Char` et `Date`  
  
-   Toutes les structures, même si leurs membres sont des types référence  
  
-   Énumérations, car leur type sous-jacent est toujours `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, ou`ULong`  
  
 Chaque structure est un type valeur, même s’il contient des membres de type référence. Pour cette raison, types valeur tels que `Char` et `Integer` sont implémentés par les structures du .NET Framework.  
  
 Vous pouvez déclarer un type valeur à l’aide du mot clé réservé, par exemple, `Decimal`. Vous pouvez également utiliser le `New` mot clé à initialiser un type valeur. Cela est particulièrement utile si le type possède un constructeur qui accepte des paramètres. Est un exemple de ce le <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructeur, ce qui génère un nouveau `Decimal` valeur à partir des parties fournis.  
  
## <a name="reference-types"></a>Types référence  
 A *type référence* contient un pointeur vers un autre emplacement de mémoire qui contient les données. Types référence sont les suivantes :  
  
-   `String`  
  
-   Tous les tableaux, même si leurs éléments sont des types valeur  
  
-   Types de classe, tels que<xref:System.Windows.Forms.Form>  
  
-   Délégués  
  
 Une classe est un *type référence*. Pour cette raison, les types référence comme `Object` et `String` sont pris en charge par [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes. Notez que chaque tableau est un type référence, même si ses membres sont des types valeur.  
  
 Étant donné que chaque type référence représente une classe sous-jacente de .NET Framework, vous devez utiliser le [nouvel opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) mot clé lorsque vous l’initialisez. L’instruction suivante initialise un tableau.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>Éléments qui ne sont pas des Types  
 Les éléments de programmation suivants ne sont pas éligibles en tant que types, car vous ne pouvez pas spécifier un d'entre eux en tant que type de données pour un élément déclaré :  
  
-   Espaces de noms  
  
-   Modules  
  
-   Événements  
  
-   Propriétés et procédures  
  
-   Variables, des constantes et des champs  
  
## <a name="working-with-the-object-data-type"></a>Utilisation du Type de données objet  
 Vous pouvez affecter un type référence ou un type valeur à une variable de la `Object` type de données. Une `Object` variable conserve toujours un pointeur vers les données, jamais les données elles-mêmes. Toutefois, si vous assignez un type valeur à une `Object` variable, il se comporte comme si elle contenait ses propres données. Pour plus d’informations, consultez [Type de données d’objet](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Vous pouvez déterminer si une `Object` variable agit comme un type référence ou un type valeur en la passant à la <xref:Microsoft.VisualBasic.Information.IsReference%2A> méthode dans le <xref:Microsoft.VisualBasic.Information> classe de la <xref:Microsoft.VisualBasic?displayProperty=nameWithType> espace de noms. <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>Retourne `True` si le contenu de la `Object` variable représente un type référence.  
  
## <a name="see-also"></a>Voir aussi  
 [Types valeur Nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Structure (instruction)](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Utilisation efficace des types de données](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
