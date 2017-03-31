---
title: "Utilisation du type dynamic (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
caps.latest.revision: 30
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f9ee1f0cae90120692fa4f41d2f432551281ab6d
ms.lasthandoff: 03/13/2017

---
# <a name="using-type-dynamic-c-programming-guide"></a>Utilisation du type dynamic (Guide de programmation C#)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] introduit un nouveau type, appelé `dynamic`. Il s’agit d’un type statique ; toutefois, un objet de type `dynamic` ignore la vérification des types statiques. Dans la plupart des cas, il fonctionne comme s’il était de type `object`. Au moment de la compilation, un élément de type `dynamic` est supposé prendre en charge n’importe quelle opération. Par conséquent, vous n’avez pas besoin de vous demander si l’objet obtient sa valeur d’une API COM, d’un langage dynamique tel qu’IronPython, du modèle DOM (Document Object Model) HTML, de la réflexion ou d’une autre partie du programme. Toutefois, si le code n’est pas valide, des erreurs sont détectées au moment de l’exécution.  
  
 Par exemple, si la méthode d’instance `exampleMethod1` du code suivant ne comporte qu’un seul paramètre, le compilateur reconnaît que le premier appel à la méthode, `ec.exampleMethod1(10, 4)`, n’est pas valide car il contient deux arguments. Cet appel entraîne une erreur du compilateur. Le deuxième appel à la méthode, `dynamic_ec.exampleMethod1(10, 4)`, n’est pas vérifié par le compilateur, car le type de `dynamic_ec` est `dynamic`. Par conséquent, aucune erreur de compilateur n’est signalée. Toutefois, l’erreur ne passe pas indéfiniment inaperçue. Elle est détectée au moment de l’exécution et provoque une exception runtime.  
  
 [!code-cs[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-cs[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 Dans ces exemples, le rôle du compilateur consiste à regrouper les informations relatives à l’opération que chaque instruction propose d’exécuter sur l’objet ou l’expression de type `dynamic`. Au moment de l’exécution, les informations stockées sont examinées, et toute instruction non valide provoque une exception runtime.  
  
 Le résultat de la plupart des opérations dynamiques est lui-même de type `dynamic`. Par exemple, si vous placez le pointeur de la souris sur `testSum` dans l’exemple suivant, IntelliSense affiche le type **(variable locale) dynamic testSum**.  
  
 [!code-cs[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 Les opérations dont le résultat n’est pas de type `dynamic` incluent les conversions du type `dynamic` en un autre type, ainsi que les appels de constructeur qui incluent des arguments de type `dynamic`. Par exemple, le type de `testInstance` dans la déclaration suivante est `ExampleClass`, et non pas `dynamic`.  
  
 [!code-cs[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 Des exemples de conversion sont présentés dans la section suivante, "Conversions".  
  
## <a name="conversions"></a>Conversions  
 Les conversions entre des objets dynamiques et d’autres types sont faciles à exécuter. Les développeurs peuvent ainsi passer du comportement dynamique au comportement non dynamique, et vice versa.  
  
 Tout objet peut être converti implicitement en type dynamique, comme illustré dans les exemples suivants.  
  
 [!code-cs[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 Inversement, une conversion implicite peut être appliquée de façon dynamique à toute expression de type `dynamic`.  
  
 [!code-cs[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>Résolution de surcharge avec des arguments de type dynamique  
 La résolution de surcharge a lieu au moment de l’exécution, et non pas au moment de la compilation, si un ou plusieurs arguments d’un appel de méthode sont de type `dynamic`, ou si le récepteur de l’appel de méthode est de type `dynamic`. Dans l’exemple suivant, si la seule méthode `exampleMethod2` accessible est définie pour accepter un argument de chaîne, l’envoi de `d1` en tant qu’argument n’entraîne pas d’erreur du compilateur, mais provoque une exception runtime. La résolution de surcharge échoue au moment de l’exécution car le type de `d1` est `int`, et `exampleMethod2` exige une chaîne.  
  
 [!code-cs[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Dynamic Language Runtime  
 Le composant Dynamic Language Runtime (DLR) est une nouvelle API de [!INCLUDE[net_v40_short](../../../csharp/programming-guide/types/includes/net_v40_short_md.md)]. Il fournit l’infrastructure qui prend en charge le type `dynamic` en C#, ainsi que l’implémentation des langages de programmation dynamique tels qu’IronPython et IronRuby. Pour plus d’informations sur le DLR, consultez [Vue d’ensemble du Dynamic Language Runtime](http://msdn.microsoft.com/library/f769a271-8aff-4bea-bfab-6160217ce23d).  
  
## <a name="com-interop"></a>COM Interop  
 [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] inclut plusieurs fonctionnalités qui améliorent l’interopérabilité avec les API COM telles que les API Office Automation. L’utilisation du type `dynamic` et des [arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) fait partie des améliorations offertes.  
  
 De nombreuses méthodes COM autorisent une variation des types d’arguments et du type de retour en désignant les types comme `object`. Cela a nécessité un cast explicite des valeurs pour la coordination avec les variables fortement typées en C#. Si vous effectuez la compilation à l’aide de l’option [/link (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/link-compiler-option.md), l’introduction du type `dynamic` vous permet de traiter les occurrences d’`object` dans les signatures COM comme si elles étaient de type `dynamic`, vous évitant ainsi une grande partie des opérations de cast. Par exemple, les instructions suivantes permettent de comparer la façon dont vous accédez à une cellule d’une feuille de calcul Microsoft Office Excel avec le type `dynamic` et sans le type `dynamic`.  
  
 [!code-cs[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-cs[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|Décrit l’utilisation du mot clé `dynamic`.|  
|[Vue d’ensemble du Dynamic Language Runtime](http://msdn.microsoft.com/library/f769a271-8aff-4bea-bfab-6160217ce23d)|Fournit une vue d’ensemble du DLR, qui est un environnement d’exécution ajoutant au Common Language Runtime (CLR) un ensemble de services pour les langages dynamiques.|  
|[Procédure pas à pas : création et utilisation d’objets dynamiques](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|Fournit des instructions pas à pas pour la création d’un objet dynamique personnalisé et pour la création d’un projet qui accède à une bibliothèque `IronPython`.|  
|[Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|Montre comment créer un projet qui utilise les arguments nommés et facultatifs, le type `dynamic` et d’autres améliorations qui simplifient l’accès aux objets d’API Office.|
