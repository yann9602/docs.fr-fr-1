---
title: "Création et levée d'exceptions (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
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
ms.openlocfilehash: 5f49b0911aa94480988987f209bc73d187451620
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Création et levée d'exceptions (Guide de programmation C#)
Les exceptions sont utilisées pour indiquer qu’une erreur s’est produite pendant l’exécution du programme. Les objets d’exception qui décrivent une erreur sont créés, puis *levés* avec le mot clé [throw](../../../csharp/language-reference/keywords/throw.md). Le runtime recherche ensuite le gestionnaire d’exceptions le plus compatible.  
  
 Les programmeurs doivent lever des exceptions quand une ou plusieurs des conditions suivantes sont vérifiées :  
  
-   La méthode ne peut pas remplir sa fonction définie.  
  
     Par exemple, si un paramètre d’une méthode a une valeur non valide :  
  
     [!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Un appel inapproprié à un objet est effectué en fonction de l’état de l’objet.  
  
     Une tentative d’écriture dans un fichier en lecture seule en est un exemple. Dans les cas où l’état d’un objet n’autorise pas une opération, levez une instance d’<xref:System.InvalidOperationException> ou un objet basé sur une dérivation de cette classe. Voici un exemple d’une méthode qui lève un objet <xref:System.InvalidOperationException> :  
  
     [!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Quand un argument d’une méthode provoque une exception.  
  
     Dans ce cas, l’exception d’origine doit être interceptée et une instance d’<xref:System.ArgumentException> doit être créée. L’exception d’origine doit être passée au constructeur d’<xref:System.ArgumentException> comme paramètre <xref:System.Exception.InnerException%2A> :  
  
     [!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Les exceptions contiennent une propriété nommée <xref:System.Exception.StackTrace%2A>. Cette chaîne contient le nom des méthodes sur la pile des appels actuelle, avec le nom de fichier et le numéro de ligne où l’exception a été levée pour chaque méthode. Un objet <xref:System.Exception.StackTrace%2A> est créé automatiquement par le CLR (Common Language Runtime) à partir du point de l’instruction `throw`, de sorte que les exceptions doivent être levées à partir du point où la trace de la pile doit commencer.  
  
 Toutes les exceptions contiennent une propriété nommée <xref:System.Exception.Message%2A>. Cette chaîne doit être définie pour expliquer la raison de l’exception. Notez que les informations sensibles du point de vue de la sécurité ne doivent pas être placées dans le texte du message. Outre <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contient une propriété nommée <xref:System.ArgumentException.ParamName%2A> dont la valeur doit être le nom de l’argument qui a provoqué la levée de l’exception. Dans le cas d’une méthode setter de propriété, <xref:System.ArgumentException.ParamName%2A> doit être défini sur `value`.  
  
 Les membres de méthodes publiques et protégées doivent lever des exceptions dès qu’ils ne peuvent pas remplir leurs fonctions habituelles. La classe d’exception qui est levée doit être l’exception la plus spécifique disponible qui répond aux conditions d’erreur. Ces exceptions doivent être documentées dans le cadre de la fonctionnalité de la classe. De plus, les classes dérivées ou les mises à jour de la classe d’origine doivent conserver le même comportement afin d’assurer la compatibilité descendante.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Pratiques à éviter lors de la levée d’exceptions  
 La liste suivante identifie les pratiques à éviter lors de la levée d’exceptions :  
  
-   Les exceptions ne doivent pas être utilisées pour changer le flux d’un programme dans le cadre d’une exécution ordinaire. Elles doivent être utilisées uniquement pour signaler et gérer les conditions d’erreur.  
  
-   Les exceptions ne doivent pas être retournées comme valeur de retour ou paramètre au lieu d’être levées.  
  
-   Ne levez pas intentionnellement <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName> ni <xref:System.IndexOutOfRangeException?displayProperty=fullName> à partir de votre propre code source.  
  
-   Ne créez pas d’exceptions qui peuvent être levées en mode Debug mais pas en mode Release. Pour identifier des erreurs d’exécution pendant la phase de développement, utilisez plutôt Debug Assert.  
  
## <a name="defining-exception-classes"></a>Définition de classes d’exceptions  
 Les programmes peuvent lever une classe d’exceptions prédéfinie dans l’espace de noms <xref:System> (sauf dans les endroits préalablement signalés) ou créer leurs propres classes d’exceptions en les dérivant d’<xref:System.Exception>. Les classes dérivées doivent définir au moins trois constructeurs : un constructeur par défaut, un qui définit la propriété du message et un qui définit à la fois la propriété <xref:System.Exception.Message%2A> et la propriété <xref:System.Exception.InnerException%2A>. Le quatrième constructeur est utilisé pour sérialiser l’exception. Les nouvelles classes d’exception doivent être sérialisables. Exemple :  
  
 [!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Les nouvelles propriétés doivent être ajoutées à la classe d’exceptions uniquement quand les données qu’elles fournissent sont utiles à la résolution de l’exception. Si de nouvelles propriétés sont ajoutées à la classe d’exceptions dérivée, la méthode `ToString()` doit être substituée pour retourner les informations ajoutées.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)   
 [Hiérarchie des exceptions](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)

