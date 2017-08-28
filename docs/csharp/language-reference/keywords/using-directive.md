---
title: "using, directive (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
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
ms.openlocfilehash: 1129efd8a1c4058a9648eab61f98cdcef7e9f2f7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-directive-c-reference"></a>using, directive (référence C#)
La directive `using` a trois utilisations :  
  
-   Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Pour vous permettre d’accéder aux membres statiques d’un type sans devoir qualifier l’accès avec le nom du type. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Pour plus d’informations, consultez la [directive using static](using-static.md).

-   Pour créer un alias pour un espace de noms ou un type. Cela s’appelle une *directive using alias*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 Le mot clé `using` est également utilisé pour créer des *instructions using<xref:System.IDisposable>, qui garantissent que les objets*  tels que les fichiers et les polices sont gérés correctement. Pour plus d’informations, consultez [Instruction using](../../../csharp/language-reference/keywords/using-statement.md).  
  
## <a name="using-static-type"></a>Utilisation du type static  
 Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a>Remarques  
 La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.  
  
 Créez un alias `using` pour faciliter la qualification d'un identificateur pour un espace de noms ou un type. Le côté droit d'une directive d'alias using doit toujours être un type complet quelles que soient les directives using placées avant.  
  
 Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms. Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.  
  
 Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système. Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code. Pour obtenir la liste des espaces de noms définis par le système, consultez la [bibliothèque de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195).  
  
 Pour obtenir des exemples de référencement de méthodes dans d’autres assemblys, consultez [Création et utilisation des DLL C#](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="example-1"></a>Exemple 1  
  
 L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :  
  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit. Par exemple, vous ne pouvez pas créer un alias using pour un List\<T>, mais vous pouvez en créer un pour un List\<int>.  
  
## <a name="example-2"></a>Exemple 2  
  
 L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :  
  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Utilisation d’espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [using, instruction](../../../csharp/language-reference/keywords/using-statement.md)

