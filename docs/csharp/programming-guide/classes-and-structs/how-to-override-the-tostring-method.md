---
title: "Guide pratique pour substituer la méthode ToString (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 2dde281d439a07d7736949294772a57e926eb587
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Guide pratique pour substituer la méthode ToString (Guide de programmation C#)
Chaque classe ou struct en C# hérite implicitement de la classe <xref:System.Object>. Ainsi, chaque objet en C# obtient la méthode <xref:System.Object.ToString%2A>, qui retourne une représentation sous forme de chaîne de cet objet. Par exemple, toutes les variables de type `int` ont une méthode `ToString`, ce qui leur permet de retourner leur contenu sous forme de chaîne :  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 Quand vous créez une classe ou un struct personnalisé, vous devez substituer la méthode <xref:System.Object.ToString%2A> pour fournir des informations sur votre type au code client.  
  
 Pour plus d’informations sur l’utilisation de chaînes de format et d’autres types de mise en forme personnalisée avec la méthode `ToString`, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Quand vous choisissez les informations à fournir par l’intermédiaire de cette méthode, déterminez si votre classe ou struct sera utilisé par du code non fiable. Veillez à ne pas fournir d’informations susceptibles d’être exploitées par du code malveillant.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Pour substituer la méthode ToString dans votre classe ou struct  
  
1.  Déclarez une méthode `ToString` avec les modificateurs et le type de retour suivants :  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Implémentez la méthode pour qu’elle retourne une chaîne.  
  
     L’exemple suivant retourne le nom de la classe en plus des données propres à une instance particulière de la classe.  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Vous pouvez tester la méthode `ToString` comme illustré dans l’exemple de code suivant :  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IFormattable>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [string](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [Mise en forme des types](../../../standard/base-types/formatting-types.md)
