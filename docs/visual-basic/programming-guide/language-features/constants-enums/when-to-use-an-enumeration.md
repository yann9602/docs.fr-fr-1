---
title: "Quand utiliser une énumération (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quand utiliser une énumération (Visual Basic)
Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées. Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs. Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des jeux de constantes à utiliser avec des variables et des propriétés.  
  
## <a name="when-to-use-an-enumeration"></a>Quand utiliser une énumération  
 Chaque fois qu’une procédure accepte un ensemble limité de variables, envisagez d’utiliser une énumération. Les énumérations rendent le code plus clair et plus lisible, particulièrement lorsque des noms explicites sont utilisés.  
  
 Avantages de l’utilisation des énumérations :  
  
-   Réduit les erreurs provoquées par transposer ou numéros d’erreur de frappe.  
  
-   Rend faciles à modifier les valeurs dans le futur.  
  
-   Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs lisibilité il.  
  
-   Garantit la compatibilité ascendante. Avec des énumérations, votre code est moins susceptible d’échouer si à l’avenir une personne modifie les valeurs correspondant aux noms de membre.  
  
## <a name="naming-enumerations"></a>Énumérations d’affectation de noms  
 Utilisez une convention d’affectation de noms pour les membres de l’énumération. Lorsque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencés contiennent le même nom. Utilisez un préfixe unique qui identifie les valeurs à partir de votre application ou composant.  
  
 Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération ou bien utiliser la `Imports` instruction. Pour plus d’informations, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Énumérations prédéfinies  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]fournit plusieurs énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult`, pour faciliter votre code. Pour obtenir la liste de ces consultez [constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Guide pratique : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Énumérations et qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Guide pratique : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum (instruction)](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)
