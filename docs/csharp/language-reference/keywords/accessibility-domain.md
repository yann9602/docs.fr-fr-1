---
title: "Domaine d'accessibilité (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a>Domaine d'accessibilité (référence C#)
Le domaine d’accessibilité d’un membre indique dans quelles sections du programme un membre peut être référencé. Si le membre est imbriqué dans un autre type, son domaine d’accessibilité est déterminé à la fois par le [niveau d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) du membre et par le domaine d’accessibilité du type conteneur immédiat.  
  
 Le domaine d’accessibilité d’un type de niveau supérieur est au moins le texte du programme du projet dans lequel il est déclaré. Cela signifie que le domaine inclut tous les fichiers sources de ce projet. Le domaine d’accessibilité d’un type imbriqué est au moins le texte de programme du type dans lequel il est déclaré. Autrement dit, le domaine est le corps du type, qui inclut tous les types imbriqués. Le domaine d’accessibilité d’un type imbriqué ne dépasse jamais celui du type conteneur. Ces concepts sont illustrés dans l’exemple suivant.  
  
## <a name="example"></a>Exemple  
 Cet exemple comporte un type de niveau supérieur, `T1`, et deux classes imbriquées, `M1` et `M2`. Les classes contiennent des champs qui ont des accessibilités déclarées différentes. Dans la méthode `Main`, un commentaire suit chaque instruction pour indiquer le domaine d’accessibilité de chaque membre. Notez que les instructions qui tentent de référencer les membres inaccessibles sont commentées. Si vous voulez examiner les erreurs du compilateur causées par une référence à un membre inaccessible, supprimez les commentaires un à un.  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
