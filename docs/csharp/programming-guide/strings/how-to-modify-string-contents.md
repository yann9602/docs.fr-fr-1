---
title: "Guide pratique pour modifier du contenu de chaîne (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 114b6fdabd235d7e57947e77b672352e28aff11e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>Guide pratique pour modifier du contenu de chaîne (Guide de programmation C#)
Étant donné que les chaînes sont *immuables*, il n’est pas possible (sans utiliser du code unsafe) de modifier la valeur d’un objet string après sa création. Toutefois, il existe de nombreuses façons de modifier la valeur d’une chaîne et de stocker le résultat dans un nouvel objet string. La classe <xref:System.String?displayProperty=fullName> fournit des méthodes qui fonctionnent sur une chaîne d’entrée et retournent un nouvel objet string. Dans de nombreux cas, vous pouvez affecter le nouvel objet à la variable qui contenait la chaîne d’origine. La classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> fournit des méthodes supplémentaires qui fonctionnent d’une manière similaire. La classe <xref:System.Text.StringBuilder?displayProperty=fullName> fournit une mémoire tampon de caractères que vous pouvez modifier « sur place ». Vous appelez la méthode <xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> pour créer un objet string qui contient le contenu actuel de la mémoire tampon.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant indique différentes façons de remplacer ou de supprimer des sous-chaînes dans une chaîne spécifiée.  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>Exemple  
 Pour accéder aux caractères individuels d’une chaîne en utilisant la notation de tableau, vous pouvez utiliser l’objet <xref:System.Text.StringBuilder>, qui surcharge l’opérateur `[]` pour permettre d’accéder à sa mémoire tampon de caractères interne. Vous pouvez également convertir la chaîne en un tableau de caractères en utilisant la méthode <xref:System.String.ToCharArray%2A>. L’exemple suivant utilise `ToCharArray` pour créer le tableau. Certains éléments de ce tableau sont ensuite modifiés. Un constructeur String prenant un tableau de caractères comme paramètres d’entrée est ensuite appelé pour créer une chaîne.  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant est fourni pour les très rares cas où vous voulez modifier une chaîne sur place en utilisant du code unsafe, en procédant d’une façon similaire aux tableaux de caractères de style C. Il indique comment accéder aux différents caractères « sur place » en utilisant le mot clé fixed. Il montre également un effet secondaire possible des opérations risquées effectuées sur les chaînes, lié à la façon dont le compilateur C# stocke (intègre) les chaînes en interne. En général, il est préférable de ne pas utiliser cette technique, sauf en cas d’absolue nécessité.  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)

