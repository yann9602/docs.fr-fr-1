---
title: "Conversions entre des chaînes et d’autres Types (Visual Basic) | Documents Microsoft"
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
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
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
ms.openlocfilehash: 2d0a5fc7327ecd6339b5021e1b4cb87cc54bd2bc
ms.lasthandoff: 03/13/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversion entre des chaînes et d'autres types (Visual Basic)
Vous pouvez convertir une valeur numérique, `Boolean`, ou la valeur de date/heure un `String`. Vous pouvez également convertir dans le sens inverse, à partir d’une valeur de chaîne numérique, `Boolean`, ou `Date` , fournie par le contenu de la chaîne peut être interprété comme une valeur valide du type de données de destination. Si elles ne peuvent pas, une erreur d’exécution se produit.  
  
 Les conversions de toutes ces affectations, dans les deux sens, sont des conversions restrictives. You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`). Le <xref:Microsoft.VisualBasic.Strings.Format%2A>et <xref:Microsoft.VisualBasic.Conversion.Val%2A>fonctions fournissent un contrôle supplémentaire sur les conversions entre des chaînes et des nombres.</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A>  
  
 Si vous avez défini une classe ou structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure. Pour plus d’informations, consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversion de nombres en chaînes  
 Vous pouvez utiliser la `Format` fonction pour convertir un nombre en une chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés mais aussi mettre en forme des symboles tels qu’un symbole monétaire (tel que `$`), des milliers séparateurs ou *symboles de groupement des chiffres* (tels que `,`) et un séparateur décimal (tel que `.`). `Format`utilise automatiquement les symboles appropriés en fonction de la **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration**.  
  
 Notez que la concaténation (`&`) (opérateur) peut convertir implicitement un nombre en une chaîne, comme le montre l’exemple suivant.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversion de chaînes en nombres  
 Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en un nombre. `Val`lit la chaîne jusqu'à ce qu’il rencontre un caractère autre qu’un chiffre, un espace, un onglet, un saut de ligne ou un période. Les séquences « se O » et « se H » altèrent la base du système et arrêter l’analyse. Jusqu'à ce qu’il s’arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique. Par exemple, l’instruction suivante renvoie la valeur `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Lors de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit une chaîne en une valeur numérique, il utilise le **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration** pour interpréter les milliers séparateur, séparateur décimal et le symbole de devise. Cela signifie qu’une conversion peut réussir avec certains paramètres, mais pas une autre. Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans les paramètres régionaux Français.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Comment : convertir un objet en un autre Type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Conversions de tableaux](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Fonctions de Conversion de type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Introduction aux applications internationales basées sur le .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
