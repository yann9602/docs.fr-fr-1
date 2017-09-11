---
title: "Types de données (Visual Basic) caractère | Documents Microsoft"
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
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
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
ms.openlocfilehash: 3407f614d5898f4fccf04e0363ec31669661b60a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="04d22-102">Types de données caractères (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04d22-102">Character Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="04d22-103">Fournit des *types de données caractère* afin de traiter les caractères affichables et imprimables.</span><span class="sxs-lookup"><span data-stu-id="04d22-103"> provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="04d22-104">Bien que les deux types reconnaissent les caractères Unicode, `Char` contient un caractère, tandis que `String` contient un nombre indéfini de caractères.</span><span class="sxs-lookup"><span data-stu-id="04d22-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="04d22-105">Pour un tableau présentant une comparaison côte-à-côte de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] des types de données, consultez [des Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="04d22-105">For a table that displays a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="04d22-106">Char (Type)</span><span class="sxs-lookup"><span data-stu-id="04d22-106">Char Type</span></span>  
 <span data-ttu-id="04d22-107">Le `Char` type de données est un caractère de Unicode sur deux octets (16 bits) unique.</span><span class="sxs-lookup"><span data-stu-id="04d22-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="04d22-108">Si une variable stocke toujours exactement un caractère, déclarez-le en tant que `Char`.</span><span class="sxs-lookup"><span data-stu-id="04d22-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="04d22-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="04d22-109">For example:</span></span>  
  
 <span data-ttu-id="04d22-110">[!code-vb[VbVbalrCharTypes n °&1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d22-110">[!code-vb[VbVbalrCharTypes#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="04d22-111">Chaque valeur possible dans une `Char` ou `String` variable est une *point de code*, ou code de caractère dans le jeu de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="04d22-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="04d22-112">Les caractères Unicode incluent le jeu de caractères ASCII base, divers autres lettres de l’alphabet, les accents, les symboles monétaires, fractions, les signes diacritiques et symboles mathématiques et techniques.</span><span class="sxs-lookup"><span data-stu-id="04d22-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04d22-113">Jeu de caractères Unicode réserve les points de code D800 à DFFF (55 296 à 55 551 décimal) pour *paires de substitution*, qui requièrent deux valeurs de 16 bits pour représenter un seul point de code.</span><span class="sxs-lookup"><span data-stu-id="04d22-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="04d22-114">A `Char` variable ne peut pas contenir une paire de substitution et un `String` utilise deux positions pour contenir une telle paire.</span><span class="sxs-lookup"><span data-stu-id="04d22-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="04d22-115">Pour plus d’informations, consultez [Type de données Char](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="04d22-115">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="04d22-116">Type de chaîne</span><span class="sxs-lookup"><span data-stu-id="04d22-116">String Type</span></span>  
 <span data-ttu-id="04d22-117">Le `String` type de données est une séquence de zéro ou plusieurs caractères Unicode à deux octets (16 bits).</span><span class="sxs-lookup"><span data-stu-id="04d22-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="04d22-118">Si une variable peut contenir un nombre indéfini de caractères, déclarez-le en tant que `String`.</span><span class="sxs-lookup"><span data-stu-id="04d22-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="04d22-119">Exemple :</span><span class="sxs-lookup"><span data-stu-id="04d22-119">For example:</span></span>  
  
 <span data-ttu-id="04d22-120">[!code-vb[VbVbalrCharTypes n °&2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d22-120">[!code-vb[VbVbalrCharTypes#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="04d22-121">Pour plus d’informations, consultez [Type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="04d22-121">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d22-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04d22-122">See Also</span></span>  
 <span data-ttu-id="04d22-123">[Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-123">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="04d22-124"> [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-124"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="04d22-125"> [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-125"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="04d22-126"> [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-126"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="04d22-127"> [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-127"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="04d22-128"> [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="04d22-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="04d22-129"> [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="04d22-129"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span>
