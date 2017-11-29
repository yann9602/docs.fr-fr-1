---
title: "Comment : modifier du contenu de chaîne (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Comment : modifier du contenu de chaîne (Guide de programmation C#)
Étant donné que les chaînes sont *immuables*, il n’est pas possible (sans utiliser du code unsafe) de modifier la valeur d’un objet string après sa création. Toutefois, il existe de nombreuses façons de modifier la valeur d’une chaîne et de stocker le résultat dans un nouvel objet string. La classe <xref:System.String?displayProperty=nameWithType> fournit des méthodes qui fonctionnent sur une chaîne d’entrée et retournent un nouvel objet string. Dans de nombreux cas, vous pouvez affecter le nouvel objet à la variable qui contenait la chaîne d’origine. La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> fournit des méthodes supplémentaires qui fonctionnent d’une manière similaire. La classe <xref:System.Text.StringBuilder?displayProperty=nameWithType> fournit une mémoire tampon de caractères que vous pouvez modifier « sur place ». Vous appelez la méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> pour créer un objet string qui contient le contenu actuel de la mémoire tampon.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant indique différentes façons de remplacer ou de supprimer des sous-chaînes dans une chaîne spécifiée.  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Exemple  
 Pour accéder aux caractères individuels d’une chaîne en utilisant la notation de tableau, vous pouvez utiliser l’objet <xref:System.Text.StringBuilder>, qui surcharge l’opérateur `[]` pour permettre d’accéder à sa mémoire tampon de caractères interne. Vous pouvez également convertir la chaîne en un tableau de caractères en utilisant la méthode <xref:System.String.ToCharArray%2A>. L’exemple suivant utilise `ToCharArray` pour créer le tableau. Certains éléments de ce tableau sont ensuite modifiés. Un constructeur String prenant un tableau de caractères comme paramètres d’entrée est ensuite appelé pour créer une chaîne.  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant est fourni pour les très rares cas où vous voulez modifier une chaîne sur place en utilisant du code unsafe, en procédant d’une façon similaire aux tableaux de caractères de style C. Il indique comment accéder aux différents caractères « sur place » en utilisant le mot clé fixed. Il montre également un effet secondaire possible des opérations risquées effectuées sur les chaînes, lié à la façon dont le compilateur C# stocke (intègre) les chaînes en interne. En général, il est préférable de ne pas utiliser cette technique, sauf en cas d’absolue nécessité.  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)
