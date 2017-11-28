---
title: "Paramètres de type générique (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b32db7eb6e7788167e110a91726e9dbfe19f31ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-type-parameters-c-programming-guide"></a>Paramètres de type générique (guide de programmation C#)
Dans une définition de méthode ou un type générique, les paramètres de type représentent un espace réservé pour un type spécifique qu’un client indique quand il instancie une variable du type générique. Une classe générique, telle que `GenericList<T>` répertoriée dans [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md), ne peut pas être utilisée en l’état car il ne s’agit pas vraiment d’un type, mais plutôt d’un modèle pour un type. Pour utiliser `GenericList<T>`, le code client doit déclarer et instancier un type construit en spécifiant un argument de type à l’intérieur de crochets pointus. L’argument de type pour cette classe particulière peut être tout type reconnu par le compilateur. Il est possible de créer un nombre quelconque d’instances de type construit, chacune avec un argument de type différent, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 Dans chacune de ces instances de `GenericList<T>`, chaque occurrence de `T` dans la classe sera substituée au moment de l’exécution avec l’argument de type. Par cette substitution, nous avons créé trois objets distincts de type sécurisé et efficaces à l’aide d’une seule définition de classe. Pour plus d’informations sur la façon dont cette substitution est exécutée par le CLR, consultez [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Indications concernant l’attribution d’un nom aux paramètres de type  
  
-   **Nommez** les paramètres de type générique avec des noms descriptifs, sauf si un nom composé d’une seule lettre est suffisamment évocateur et qu’un nom descriptif n’apporte rien de plus.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Envisagez** l’utilisation de T comme nom de paramètre de type pour les types ayant un paramètre de type d’une seule lettre.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Préfixez** les noms des paramètres de type descriptifs avec « T ».  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Pensez** à indiquer les contraintes placées sur un paramètre de type dans le nom de paramètre. Par exemple, un paramètre limité à `ISession` peut être appelé `TSession`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Génériques](../../../csharp/programming-guide/generics/index.md)  
 [Différences entre les modèles C++ et les génériques C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
