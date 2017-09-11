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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 34eb32cb6e640d681db6853aaa164d84acca7e4f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="3e9b6-102">Conversion entre des chaînes et d'autres types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e9b6-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="3e9b6-103">Vous pouvez convertir une valeur numérique, `Boolean`, ou la valeur de date/heure un `String`.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="3e9b6-104">Vous pouvez également convertir dans le sens inverse, à partir d’une valeur de chaîne numérique, `Boolean`, ou `Date` , fournie par le contenu de la chaîne peut être interprété comme une valeur valide du type de données de destination.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="3e9b6-105">Si elles ne peuvent pas, une erreur d’exécution se produit.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="3e9b6-106">Les conversions de toutes ces affectations, dans les deux sens, sont des conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="3e9b6-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span><span class="sxs-lookup"><span data-stu-id="3e9b6-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="3e9b6-108">Le <xref:Microsoft.VisualBasic.Strings.Format%2A>et <xref:Microsoft.VisualBasic.Conversion.Val%2A>fonctions fournissent un contrôle supplémentaire sur les conversions entre des chaînes et des nombres.</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A></span><span class="sxs-lookup"><span data-stu-id="3e9b6-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="3e9b6-109">Si vous avez défini une classe ou structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="3e9b6-110">Pour plus d’informations, consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3e9b6-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="3e9b6-111">Conversion de nombres en chaînes</span><span class="sxs-lookup"><span data-stu-id="3e9b6-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="3e9b6-112">Vous pouvez utiliser la `Format` fonction pour convertir un nombre en une chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés mais aussi mettre en forme des symboles tels qu’un symbole monétaire (tel que `$`), des milliers séparateurs ou *symboles de groupement des chiffres* (tels que `,`) et un séparateur décimal (tel que `.`).</span><span class="sxs-lookup"><span data-stu-id="3e9b6-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="3e9b6-113">`Format`utilise automatiquement les symboles appropriés en fonction de la **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="3e9b6-114">Notez que la concaténation (`&`) (opérateur) peut convertir implicitement un nombre en une chaîne, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="3e9b6-115">Conversion de chaînes en nombres</span><span class="sxs-lookup"><span data-stu-id="3e9b6-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="3e9b6-116">Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en un nombre.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="3e9b6-117">`Val`lit la chaîne jusqu'à ce qu’il rencontre un caractère autre qu’un chiffre, un espace, un onglet, un saut de ligne ou un période.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="3e9b6-118">Les séquences « se O » et « se H » altèrent la base du système et arrêter l’analyse.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="3e9b6-119">Jusqu'à ce qu’il s’arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="3e9b6-120">Par exemple, l’instruction suivante renvoie la valeur `141.825`.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="3e9b6-121">Lors de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit une chaîne en une valeur numérique, il utilise le **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration** pour interpréter les milliers séparateur, séparateur décimal et le symbole de devise.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-121">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="3e9b6-122">Cela signifie qu’une conversion peut réussir avec certains paramètres, mais pas une autre.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="3e9b6-123">Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans les paramètres régionaux Français.</span><span class="sxs-lookup"><span data-stu-id="3e9b6-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9b6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e9b6-124">See Also</span></span>  
 <span data-ttu-id="3e9b6-125">[Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-125">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="3e9b6-126"> [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-126"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="3e9b6-127"> [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="3e9b6-128"> [Comment : convertir un objet en un autre Type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-128"> [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md) </span></span>  
<span data-ttu-id="3e9b6-129"> [Conversions de tableaux](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-129"> [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md) </span></span>  
<span data-ttu-id="3e9b6-130"> [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-130"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="3e9b6-131"> [Fonctions de Conversion de type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="3e9b6-131"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="3e9b6-132"> [Introduction aux applications internationales basées sur le .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span><span class="sxs-lookup"><span data-stu-id="3e9b6-132"> [Introduction to International Applications Based on the .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)</span></span>
