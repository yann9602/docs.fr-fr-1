---
title: "Conversion entre des chaînes et d'autres types (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversion entre des chaînes et d'autres types (Visual Basic)
Vous pouvez convertir une valeur numérique, `Boolean`, ou valeur de date/heure un `String`. Vous pouvez également convertir dans le sens inverse, à partir d’une valeur de chaîne en numérique, `Boolean`, ou `Date` — fourni le contenu de la chaîne peut être interprété comme une valeur valide du type de données de destination. Si elles ne peuvent pas, une erreur d’exécution se produit.  
  
 Les conversions de toutes ces affectations, dans les deux sens, sont des conversions restrictives. Vous devez utiliser des mots clés de conversion de type (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, et `CType`). Le <xref:Microsoft.VisualBasic.Strings.Format%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A> fonctions vous permettent de contrôler les conversions entre des chaînes et des nombres.  
  
 Si vous avez défini une classe ou structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure. Pour plus d’informations, consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversion de nombres en chaînes  
 Vous pouvez utiliser la `Format` de fonction pour convertir un nombre en une chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés, mais aussi mettre en forme de symboles comme un symbole monétaire (tel que `$`), des milliers séparateurs ou *groupement des chiffres symboles* (tel que `,`) et un séparateur décimal (tel que `.`). `Format`utilise automatiquement les symboles appropriés en fonction de la **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration**.  
  
 Notez que la concaténation (`&`) opérateur peut convertir implicitement un nombre en une chaîne, comme le montre l’exemple suivant.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversion de chaînes en nombres  
 Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en un nombre. `Val`lit la chaîne jusqu'à ce qu’il rencontre un caractère autre qu’un chiffre, un espace, un onglet, un saut de ligne ou un période. Les séquences « & » et « & H » modifier la base du numéro de système et d’arrêter l’analyse. Jusqu'à ce qu’il s’arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique. Par exemple, l’instruction suivante retourne la valeur `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Lorsque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convertit une chaîne en valeur numérique, il utilise le **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration** pour interpréter les milliers separator, le séparateur décimal, et symbole de devise. Cela signifie qu’une conversion peut réussir avec certains paramètres, mais pas à un autre. Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans tous les paramètres régionaux Français.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Comment : convertir un objet en un autre Type en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Introduction aux applications internationales basées sur le .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
