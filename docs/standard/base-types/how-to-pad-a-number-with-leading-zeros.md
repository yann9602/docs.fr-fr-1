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
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Comment : remplir un nombre avec des zéros non significatifs
Vous pouvez ajouter des zéros non significatifs à un entier en utilisant la [chaîne de format numérique standard](../../../docs/standard/base-types/standard-numeric-format-strings.md) « D » avec un spécificateur de précision. Vous pouvez ajouter des zéros non significatifs aux nombres entiers et à virgule flottante en utilisant une [chaîne de format numérique personnalisée](../../../docs/standard/base-types/custom-numeric-format-strings.md). Cette rubrique montre comment utiliser les deux méthodes pour remplir un nombre avec des zéros non significatifs.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Pour remplir un entier avec des zéros non significatifs dans la limite d'une longueur spécifique  
  
1.  Déterminez le nombre minimal de chiffres que la valeur entière doit afficher. Incluez des chiffres non significatifs dans ce nombre.  
  
2.  Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale.  
  
    -   Pour afficher l’entier en tant que valeur décimale, appelez sa `ToString(String)` (méthode), puis transmettez la chaîne « D*n*» comme valeur de la `format` paramètre, où  *n*  représente la longueur minimale de la chaîne.  
  
    -   Pour afficher l’entier en tant que valeur hexadécimale, appelez sa `ToString(String)` (méthode) et passez la chaîne « X*n*» comme valeur de la `format` paramètre, où  *n*  représente la longueur minimale de la chaîne.  
  
     Vous pouvez également utiliser la chaîne de format dans une méthode, telles que <xref:System.String.Format%2A> ou <xref:System.Console.WriteLine%2A>, qui utilise [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).  
  
 L'exemple suivant met en forme plusieurs valeurs entières avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Pour remplir un entier avec un nombre spécifique de zéros non significatifs  
  
1.  Déterminez le nombre de zéros non significatifs que la valeur entière doit afficher.  
  
2.  Déterminez si vous souhaitez afficher l'entier en tant que valeur décimale ou que valeur hexadécimale. Selon que vous souhaitez le mettre en forme en tant que valeur décimale ou que valeur hexadécimale, vous devez utiliser le spécificateur de format standard « D » ou « X ».  
  
3.  Déterminez la longueur de la chaîne numérique non remplie en appelant la méthode `ToString("D").Length` ou `ToString("X").Length` de la valeur entière.  
  
4.  Ajoutez le nombre de zéros non significatifs à inclure dans la chaîne mise en forme à la longueur de la chaîne numérique non remplie. Cette opération définit la longueur totale de la chaîne remplie.  
  
5.  Appeler l’entier `ToString(String)` (méthode), puis transmettez la chaîne « D*n*» pour les chaînes décimales et « X*n*» pour les chaînes hexadécimales, où  *n*  représente la longueur totale de la chaîne remplie. Vous pouvez également utiliser le « D*n*» ou « X*n*« format de chaîne dans une méthode qui prend en charge la mise en forme composite.  
  
 L'exemple suivant remplit une valeur entière avec cinq zéros non significatifs.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Pour remplir une valeur numérique avec des zéros non significatifs dans la limite d'une longueur spécifique  
  
1.  Déterminez le nombre de chiffres à gauche du séparateur décimal qui doivent apparaître dans la représentation du nombre sous forme de chaîne. Incluez des zéros non significatifs dans ce nombre total de chiffres.  
  
2.  Définissez une chaîne de format numérique personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour représenter le nombre minimal de zéros.  
  
3.  Appelez la méthode `ToString(String)` du nombre et transmettez-lui la chaîne de format personnalisée. Vous pouvez également utiliser la chaîne de format personnalisée avec une méthode qui prend en charge la mise en forme composite.  
  
 L'exemple suivant met en forme plusieurs valeurs numériques avec des zéros non significatifs de manière à ce que la longueur totale du nombre mis en forme soit au moins égale à huit caractères à gauche du séparateur décimal.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Pour remplir une valeur numérique avec un nombre spécifique de zéros non significatifs  
  
1.  Déterminez le nombre de zéros non significatifs que la valeur numérique doit avoir.  
  
2.  Déterminez le nombre de chiffres à gauche du séparateur décimal dans la chaîne numérique non remplie. Pour ce faire :  
  
    1.  Déterminez si la représentation sous forme de chaîne d'un nombre comprend un séparateur décimal.  
  
    2.  Si tel est le cas, déterminez le nombre de caractères à gauche du séparateur décimal.  
  
         ou  
  
         Sinon, déterminez la longueur de la chaîne.  
  
3.  Créez une chaîne de format personnalisée qui utilise l'espace réservé du zéro (« 0 ») pour chaque zéro non significatif à inclure dans la chaîne, ainsi que l'espace réservé du zéro ou l'espace réservé de chiffre (« # ») pour représenter chaque chiffre dans la chaîne par défaut.  
  
4.  Fournissez la chaîne de format personnalisée comme paramètre à la méthode `ToString(String)` du nombre ou à une méthode qui prend en charge la mise en forme composite.  
  
 L'exemple suivant remplit deux valeurs <xref:System.Double> avec cinq zéros non significatifs.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md)
