---
title: "Comment : remplir un nombre avec des zéros non significatifs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="4eb63-102">Comment : remplir un nombre avec des zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="4eb63-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="4eb63-103">Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](../../../docs/standard/base-types/standard-numeric-format-strings.md) « D » avec un spécificateur de précision.</span><span class="sxs-lookup"><span data-stu-id="4eb63-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="4eb63-104">Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="4eb63-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="4eb63-105">Cette rubrique montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="4eb63-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4eb63-106">Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="4eb63-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4eb63-107">Déterminez le nombre minimal de chiffres que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="4eb63-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="4eb63-108">Incluez des chiffres non significatifs dans ce nombre.</span><span class="sxs-lookup"><span data-stu-id="4eb63-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="4eb63-109">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4eb63-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="4eb63-110">Pour afficher l’entier en tant que valeur décimale, appelez sa `ToString(String)` (méthode), puis transmettez la chaîne « D*n*» comme valeur de la `format` paramètre, où  *n*  représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4eb63-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="4eb63-111">Pour afficher l’entier en tant que valeur hexadécimale, appelez sa `ToString(String)` (méthode) et passez la chaîne « X*n*» comme valeur de la `format` paramètre, où  *n*  représente la longueur minimale de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4eb63-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="4eb63-112">Vous pouvez également utiliser la chaîne de format dans une méthode, telles que <xref:System.String.Format%2A> ou <xref:System.Console.WriteLine%2A>, qui utilise [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="4eb63-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="4eb63-113">L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.</span><span class="sxs-lookup"><span data-stu-id="4eb63-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4eb63-114">Pour remplir un entier avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="4eb63-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4eb63-115">Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.</span><span class="sxs-lookup"><span data-stu-id="4eb63-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="4eb63-116">Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="4eb63-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="4eb63-117">Selon que vous souhaitez le mettre en forme en tant que valeur décimale ou que valeur hexadécimale, vous devez utiliser le spécificateur de format standard « D » ou « X ».</span><span class="sxs-lookup"><span data-stu-id="4eb63-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="4eb63-118">Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière.</span><span class="sxs-lookup"><span data-stu-id="4eb63-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="4eb63-119">Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie.</span><span class="sxs-lookup"><span data-stu-id="4eb63-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="4eb63-120">Cette opération définit la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="4eb63-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="4eb63-121">Appeler l’entier `ToString(String)` (méthode), puis transmettez la chaîne « D*n*» pour les chaînes décimales et « X*n*» pour les chaînes hexadécimales, où  *n*  représente la longueur totale de la chaîne remplie.</span><span class="sxs-lookup"><span data-stu-id="4eb63-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="4eb63-122">Vous pouvez également utiliser le « D*n*» ou « X*n*« format de chaîne dans une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="4eb63-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4eb63-123">L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="4eb63-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4eb63-124">Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique</span><span class="sxs-lookup"><span data-stu-id="4eb63-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="4eb63-125">Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="4eb63-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="4eb63-126">Incluez des zéros non significatifs dans ce nombre total de chiffres.</span><span class="sxs-lookup"><span data-stu-id="4eb63-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="4eb63-127">Définissez une chaîne de format numérique personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour représenter le nombre minimal de zéros.</span><span class="sxs-lookup"><span data-stu-id="4eb63-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="4eb63-128">Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4eb63-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="4eb63-129">Vous pouvez également utiliser la chaîne de format personnalisée avec une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="4eb63-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4eb63-130">L'exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="4eb63-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4eb63-131">Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs</span><span class="sxs-lookup"><span data-stu-id="4eb63-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="4eb63-132">Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.</span><span class="sxs-lookup"><span data-stu-id="4eb63-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="4eb63-133">Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie.</span><span class="sxs-lookup"><span data-stu-id="4eb63-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="4eb63-134">Pour ce faire :</span><span class="sxs-lookup"><span data-stu-id="4eb63-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="4eb63-135">Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="4eb63-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="4eb63-136">Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.</span><span class="sxs-lookup"><span data-stu-id="4eb63-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="4eb63-137">ou</span><span class="sxs-lookup"><span data-stu-id="4eb63-137">-or-</span></span>  
  
         <span data-ttu-id="4eb63-138">Sinon, déterminez la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4eb63-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="4eb63-139">Créez une chaîne de format personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour chaque zéro non significatif à inclure dans la chaîne, ainsi que l'espace réservé du zéro ou l'espace réservé de chiffre (« # ») pour représenter chaque chiffre dans la chaîne par défaut.</span><span class="sxs-lookup"><span data-stu-id="4eb63-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="4eb63-140">Fournissez la chaîne de format personnalisée comme paramètre à la méthode `ToString(String)` du nombre ou à une méthode qui prend en charge la mise en forme composite.</span><span class="sxs-lookup"><span data-stu-id="4eb63-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="4eb63-141">L'exemple suivant remplit deux valeurs <xref:System.Double> avec cinq zéros non significatifs.</span><span class="sxs-lookup"><span data-stu-id="4eb63-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4eb63-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eb63-142">See Also</span></span>  
 [<span data-ttu-id="4eb63-143">Custom Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="4eb63-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="4eb63-144">Standard Numeric Format Strings</span><span class="sxs-lookup"><span data-stu-id="4eb63-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="4eb63-145">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="4eb63-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
