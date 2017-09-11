---
title: "Types de données divers (Visual Basic) | Documents Microsoft"
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: ed7b61a5ec57ff85347f2c257e321ab9ec425274
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a><span data-ttu-id="2164b-102">Types de données divers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2164b-102">Miscellaneous Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="2164b-103">fournit plusieurs types de données qui ne sont pas adaptés pour les nombres ou de caractères.</span><span class="sxs-lookup"><span data-stu-id="2164b-103"> supplies several data types that are not oriented toward numbers or characters.</span></span> <span data-ttu-id="2164b-104">Au lieu de cela, ils traitent des données particulières telles qu’Oui/non valeurs, les valeurs de date/heure et adresses de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2164b-104">Instead, they deal with specialized data such as yes/no values, date/time values, and object addresses.</span></span>  
  
 <span data-ttu-id="2164b-105">Pour un tableau présentant une comparaison côte-à-côte de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] des types de données, consultez [des Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="2164b-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="boolean-type"></a><span data-ttu-id="2164b-106">Type booléen</span><span class="sxs-lookup"><span data-stu-id="2164b-106">Boolean Type</span></span>  
 <span data-ttu-id="2164b-107">Le [Type de données Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) est une valeur non signée qui est interprétée comme `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="2164b-107">The [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) is an unsigned value that is interpreted as either `True` or `False`.</span></span> <span data-ttu-id="2164b-108">Sa largeur de données dépend de la plateforme d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="2164b-108">Its data width depends on the implementing platform.</span></span> <span data-ttu-id="2164b-109">Si une variable peut contenir uniquement les valeurs de deux États tels que true/false, Oui/non ou actif/inactif, déclarez-le en tant que `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="2164b-109">If a variable can contain only two-state values such as true/false, yes/no, or on/off, declare it as `Boolean`.</span></span>  
  
## <a name="date-type"></a><span data-ttu-id="2164b-110">Type de date</span><span class="sxs-lookup"><span data-stu-id="2164b-110">Date Type</span></span>  
 <span data-ttu-id="2164b-111">Le [Type de données Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) est une valeur 64 bits qui conserve des informations de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="2164b-111">The [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) is a 64-bit value that holds both date and time information.</span></span> <span data-ttu-id="2164b-112">Chaque incrément représente 100 nanosecondes du temps écoulé depuis le début (12:00 AM) le 1er janvier de l’année 1 du calendrier grégorien.</span><span class="sxs-lookup"><span data-stu-id="2164b-112">Each increment represents 100 nanoseconds of elapsed time since the beginning (12:00 AM) of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="2164b-113">Si une variable peut contenir une valeur de date, une valeur d’heure ou les deux, déclarez-le en tant que `Date`.</span><span class="sxs-lookup"><span data-stu-id="2164b-113">If a variable can contain a date value, a time value, or both, declare it as `Date`.</span></span>  
  
## <a name="object-type"></a><span data-ttu-id="2164b-114">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="2164b-114">Object Type</span></span>  
 <span data-ttu-id="2164b-115">Le [Type de données d’objet](../../../../visual-basic/language-reference/data-types/object-data-type.md) est une adresse 32 bits qui pointe vers une instance d’objet dans votre application ou une autre application.</span><span class="sxs-lookup"><span data-stu-id="2164b-115">The [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) is a 32-bit address that points to an object instance within your application or in some other application.</span></span> <span data-ttu-id="2164b-116">Une `Object` variable peut faire référence à un objet de votre application reconnaît ou à des données de n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="2164b-116">An `Object` variable can refer to any object your application recognizes, or to data of any data type.</span></span> <span data-ttu-id="2164b-117">Cela inclut les deux *des types valeur*, tel que `Integer`, `Boolean`et des instances de structure, et *types référence*, qui sont des instances d’objets créés à partir de classes telles que `String` et <xref:System.Windows.Forms.Form>et les instances de tableau.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="2164b-117">This includes both *value types*, such as `Integer`, `Boolean`, and structure instances, and *reference types*, which are instances of objects created from classes such as `String` and <xref:System.Windows.Forms.Form>, and array instances.</span></span>  
  
 <span data-ttu-id="2164b-118">Si une variable stocke un pointeur vers une instance d’une classe que vous ne savez pas au moment de la compilation, ou si elle peut pointer vers des données de différents types de données, déclarez-le en tant que `Object`.</span><span class="sxs-lookup"><span data-stu-id="2164b-118">If a variable stores a pointer to an instance of a class that you do not know at compile time, or if it can point to data of various data types, declare it as `Object`.</span></span>  
  
 <span data-ttu-id="2164b-119">L’avantage de le `Object` est de type de données que vous pouvez l’utiliser pour stocker des données de n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="2164b-119">The advantage of the `Object` data type is that you can use it to store data of any data type.</span></span> <span data-ttu-id="2164b-120">L’inconvénient est que vous subissez des opérations supplémentaires qui prennent plus de temps d’exécution et de rendre votre application plus lentes.</span><span class="sxs-lookup"><span data-stu-id="2164b-120">The disadvantage is that you incur extra operations that take more execution time and make your application perform slower.</span></span> <span data-ttu-id="2164b-121">Si vous utilisez un `Object` variable pour les types valeur, vous subissez *boxing* et *unboxing*.</span><span class="sxs-lookup"><span data-stu-id="2164b-121">If you use an `Object` variable for value types, you incur *boxing* and *unboxing*.</span></span> <span data-ttu-id="2164b-122">Si vous l’utilisez pour les types référence, vous subissez *liaison tardive*.</span><span class="sxs-lookup"><span data-stu-id="2164b-122">If you use it for reference types, you incur *late binding*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2164b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2164b-123">See Also</span></span>  
 <span data-ttu-id="2164b-124">[Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="2164b-124">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="2164b-125"> [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="2164b-125"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="2164b-126"> [Types de données numériques](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="2164b-126"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="2164b-127"> [Types de données caractère](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="2164b-127"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="2164b-128"> [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="2164b-128"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="2164b-129"> [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="2164b-129"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
