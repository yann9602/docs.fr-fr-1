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
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="1ef1a-102">Conversion entre des chaînes et d'autres types (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ef1a-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="1ef1a-103">Vous pouvez convertir une valeur numérique, `Boolean`, ou valeur de date/heure un `String`.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="1ef1a-104">Vous pouvez également convertir dans le sens inverse, à partir d’une valeur de chaîne en numérique, `Boolean`, ou `Date` — fourni le contenu de la chaîne peut être interprété comme une valeur valide du type de données de destination.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="1ef1a-105">Si elles ne peuvent pas, une erreur d’exécution se produit.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="1ef1a-106">Les conversions de toutes ces affectations, dans les deux sens, sont des conversions restrictives.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="1ef1a-107">Vous devez utiliser des mots clés de conversion de type (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, et `CType`).</span><span class="sxs-lookup"><span data-stu-id="1ef1a-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="1ef1a-108">Le <xref:Microsoft.VisualBasic.Strings.Format%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A> fonctions vous permettent de contrôler les conversions entre des chaînes et des nombres.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="1ef1a-109">Si vous avez défini une classe ou structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="1ef1a-110">Pour plus d’informations, consultez [Comment : définir un opérateur de Conversion](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1ef1a-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="1ef1a-111">Conversion de nombres en chaînes</span><span class="sxs-lookup"><span data-stu-id="1ef1a-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="1ef1a-112">Vous pouvez utiliser la `Format` de fonction pour convertir un nombre en une chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés, mais aussi mettre en forme de symboles comme un symbole monétaire (tel que `$`), des milliers séparateurs ou *groupement des chiffres symboles* (tel que `,`) et un séparateur décimal (tel que `.`).</span><span class="sxs-lookup"><span data-stu-id="1ef1a-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="1ef1a-113">`Format`utilise automatiquement les symboles appropriés en fonction de la **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="1ef1a-114">Notez que la concaténation (`&`) opérateur peut convertir implicitement un nombre en une chaîne, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="1ef1a-115">Conversion de chaînes en nombres</span><span class="sxs-lookup"><span data-stu-id="1ef1a-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="1ef1a-116">Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en un nombre.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="1ef1a-117">`Val`lit la chaîne jusqu'à ce qu’il rencontre un caractère autre qu’un chiffre, un espace, un onglet, un saut de ligne ou un période.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="1ef1a-118">Les séquences « & » et « & H » modifier la base du numéro de système et d’arrêter l’analyse.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="1ef1a-119">Jusqu'à ce qu’il s’arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="1ef1a-120">Par exemple, l’instruction suivante retourne la valeur `141.825`.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="1ef1a-121">Lorsque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] convertit une chaîne en valeur numérique, il utilise le **Options régionales** paramètres spécifiés dans les fenêtres **le panneau de configuration** pour interpréter les milliers separator, le séparateur décimal, et symbole de devise.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-121">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="1ef1a-122">Cela signifie qu’une conversion peut réussir avec certains paramètres, mais pas à un autre.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="1ef1a-123">Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans tous les paramètres régionaux Français.</span><span class="sxs-lookup"><span data-stu-id="1ef1a-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef1a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ef1a-124">See Also</span></span>  
 [<span data-ttu-id="1ef1a-125">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ef1a-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="1ef1a-126">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="1ef1a-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="1ef1a-127">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="1ef1a-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="1ef1a-128">Comment : convertir un objet en un autre Type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ef1a-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="1ef1a-129">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="1ef1a-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="1ef1a-130">Types de données</span><span class="sxs-lookup"><span data-stu-id="1ef1a-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="1ef1a-131">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="1ef1a-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="1ef1a-132">Introduction aux applications internationales basées sur le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1ef1a-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
