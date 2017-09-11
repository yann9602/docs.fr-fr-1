---
title: "Types de données élémentaires (Visual Basic) | Documents Microsoft"
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
- elementary data types
- data types [Visual Basic], elementary
ms.assetid: dfad6fe9-2da6-49a4-b0b1-2d7ae0283de5
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
ms.openlocfilehash: 6d363fdd7f7f2755aec34dfe82e38d83ba6e56af
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="elementary-data-types-visual-basic"></a><span data-ttu-id="9935e-102">Types de données élémentaires (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9935e-102">Elementary Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="9935e-103">fournit un jeu de types de données prédéfinis, vous pouvez utiliser pour la plupart des éléments de programmation.</span><span class="sxs-lookup"><span data-stu-id="9935e-103"> supplies a set of predefined data types, which you can use for many of your programming elements.</span></span> <span data-ttu-id="9935e-104">Cette section décrit ces types et comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9935e-104">This section describes these types and how to use them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9935e-105">Chaque type de données élémentaire de Visual Basic est prise en charge par une structure ou une classe qui se trouve dans le <xref:System>espace de noms.</xref:System></span><span class="sxs-lookup"><span data-stu-id="9935e-105">Every elementary data type in Visual Basic is supported by a structure or a class that is in the <xref:System> namespace.</span></span> <span data-ttu-id="9935e-106">Le compilateur utilise chaque mot clé type de données en tant qu’alias pour la structure sous-jacente ou de la classe.</span><span class="sxs-lookup"><span data-stu-id="9935e-106">The compiler uses each data type keyword as an alias for the underlying structure or class.</span></span> <span data-ttu-id="9935e-107">Par exemple, déclarer une variable en utilisant le mot réservé `Byte` équivaut à la déclarer en utilisant le nom de structure qualifié <xref:System.Byte?displayProperty=fullName>.</xref:System.Byte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9935e-107">For example, declaring a variable by using the reserved word `Byte` is the same as declaring it by using the fully qualified structure name <xref:System.Byte?displayProperty=fullName>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9935e-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9935e-108">In This Section</span></span>  
 [<span data-ttu-id="9935e-109">Types de données numériques</span><span class="sxs-lookup"><span data-stu-id="9935e-109">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 <span data-ttu-id="9935e-110">Décrit les types numériques intégraux et non intégraux.</span><span class="sxs-lookup"><span data-stu-id="9935e-110">Describes the integral and non-integral numeric types.</span></span>  
  
 [<span data-ttu-id="9935e-111">Types de données caractère</span><span class="sxs-lookup"><span data-stu-id="9935e-111">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 <span data-ttu-id="9935e-112">Décrit la `Char` et `String` types.</span><span class="sxs-lookup"><span data-stu-id="9935e-112">Describes the `Char` and `String` types.</span></span>  
  
 [<span data-ttu-id="9935e-113">Types de données divers</span><span class="sxs-lookup"><span data-stu-id="9935e-113">Miscellaneous Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 <span data-ttu-id="9935e-114">Décrit la `Boolean`, `Date`, et `Object` types.</span><span class="sxs-lookup"><span data-stu-id="9935e-114">Describes the `Boolean`, `Date`, and `Object` types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9935e-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9935e-115">Related Sections</span></span>  
 [<span data-ttu-id="9935e-116">Types de données</span><span class="sxs-lookup"><span data-stu-id="9935e-116">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="9935e-117">Présente le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] types de données et explique comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="9935e-117">Introduces the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="9935e-118">Types de données</span><span class="sxs-lookup"><span data-stu-id="9935e-118">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="9935e-119">Fournit une vue d’ensemble des types de données élémentaires fournis par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="9935e-119">Provides an overview of the elementary data types supplied by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>
