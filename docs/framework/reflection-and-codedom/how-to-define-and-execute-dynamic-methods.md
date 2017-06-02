---
title: "Comment&#160;: d&#233;finir et ex&#233;cuter des m&#233;thodes dynamiques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthodes dynamiques"
  - "émission de réflexion, méthodes dynamiques"
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;finir et ex&#233;cuter des m&#233;thodes dynamiques
Les procédures suivantes montrent comment définir et exécuter une méthode dynamique simple et une méthode dynamique liée à une instance d'une classe.  Pour plus d'informations sur les méthodes dynamiques, consultez la classe <xref:System.Reflection.Emit.DynamicMethod> et [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/fr-fr/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### Pour définir et exécuter une méthode dynamique  
  
1.  Déclarez un type délégué pour exécuter la méthode.  Envisagez d'utiliser un délégué générique pour réduire le nombre de types délégués que vous devez déclarer.  Le code suivant déclare deux types délégués qui peuvent être utilisés pour la méthode `SquareIt`, et l'un d'eux est générique.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Créez un tableau qui spécifie les types de paramètre pour la méthode dynamique.  Dans cet exemple, comme le seul paramètre est un type `int` \(`Integer` en Visual Basic\), le tableau ne possède qu'un seul élément.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Créez un <xref:System.Reflection.Emit.DynamicMethod>.  Dans cet exemple, la méthode est appelée `SquareIt`.  
  
    > [!NOTE]
    >  Il n'est pas nécessaire de donner des noms aux méthodes dynamiques et elles ne peuvent pas être appelées par leur nom.  Plusieurs méthodes dynamiques peuvent avoir le même nom.  Toutefois, le nom apparaît dans les piles des appels et peut être utile pour le débogage.  
  
     Le type de la valeur de retour est spécifié en tant que `long`.  La méthode est associée au module qui contient la classe `Example`, laquelle comprend l'exemple de code.  Il est possible de spécifier n'importe quel module chargé.  La méthode dynamique agit comme une méthode `static` \(`Shared` en Visual Basic\) de niveau module.  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Émettez le corps de la méthode.  Dans cet exemple, un objet <xref:System.Reflection.Emit.ILGenerator> est utilisé pour émettre le code en langage MSIL \(Microsoft Intermediate Language\).  Il est également possible d'utiliser un objet <xref:System.Reflection.Emit.DynamicILInfo> conjointement à des générateurs de code non managé pour émettre le corps de la méthode de l'objet <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Le code MSIL de cet exemple charge l'argument, un nombre de type `int`, sur la pile, le convertit en type `long`, duplique le nombre de type `long` et multiplie les deux nombres.  Le carré obtenu est laissé sur la pile et la méthode n'a plus qu'à le retourner.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Créez une instance du délégué \(déclaré dans l'étape 1\) qui représente la méthode dynamique en appelant la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>.  La création du délégué achève la méthode et toute tentative supplémentaire de modification de la méthode, par exemple l'ajout de code MSIL, est ignorée.  Le code suivant crée le délégué et l'appelle, à l'aide d'un délégué générique.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### Pour définir et exécuter une méthode dynamique liée à un objet  
  
1.  Déclarez un type délégué pour exécuter la méthode.  Envisagez d'utiliser un délégué générique pour réduire le nombre de types délégués que vous devez déclarer.  Le code suivant déclare un type délégué générique qui peut être utilisé pour exécuter n'importe quelle méthode avec un seul paramètre et une valeur de retour ou une méthode avec deux paramètres et une valeur de retour si le délégué est lié à un objet.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Créez un tableau qui spécifie les types de paramètre pour la méthode dynamique.  Si le délégué qui représente la méthode doit être lié à un objet, le premier paramètre doit correspondre au type auquel le délégué est lié.  Cet exemple comporte deux paramètres, de type `Example` et de type `int` \(`Integer` en Visual Basic\).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Créez un <xref:System.Reflection.Emit.DynamicMethod>.  Dans cet exemple, la méthode n'a pas de nom.  Le type de la valeur de retour est spécifié en tant que `int` \(`Integer` en Visual Basic\).  La méthode a accès aux membres privés et protégés de la classe `Example`.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Émettez le corps de la méthode.  Dans cet exemple, un objet <xref:System.Reflection.Emit.ILGenerator> est utilisé pour émettre le code en langage MSIL \(Microsoft Intermediate Language\).  Il est également possible d'utiliser un objet <xref:System.Reflection.Emit.DynamicILInfo> conjointement à des générateurs de code non managé pour émettre le corps de la méthode de l'objet <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Le code MSIL de cet exemple charge le premier argument, qui est une instance de la classe `Example` et l'utilise pour charger la valeur d'un champ d'instance privée de type `int`.  Le deuxième argument est chargé, et les deux nombres sont multipliés.  Si le résultat est supérieur à `int`, la valeur est tronquée et les bits les plus significatifs sont ignorés.  La méthode est retournée, avec la valeur de retour sur la pile.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Créez une instance du délégué \(déclaré dans l'étape 1\) qui représente la méthode dynamique en appelant la surcharge de la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29>.  La création du délégué achève la méthode et toute tentative supplémentaire de modification de la méthode, par exemple l'ajout de code MSIL, est ignorée.  
  
    > [!NOTE]
    >  Vous pouvez appeler plusieurs fois la méthode <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> pour créer des délégués liés à d'autres instances du type cible.  
  
     Le code suivant lie la méthode à une nouvelle instance de la classe `Example` dont le champ de test privé a la valeur 42.  En d'autres termes, chaque fois que le délégué est appelé, la même instance de `Example` est passée au premier paramètre de la méthode.  
  
     Le délégué `OneParameter` est utilisé dans la mesure où le premier paramètre de la méthode reçoit toujours l'instance de `Example`.  Lors de l'appel du délégué, seul le deuxième paramètre est nécessaire.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## Exemple  
 L'exemple de code suivant montre une méthode dynamique simple et une méthode dynamique liée à une instance d'une classe.  
  
 La méthode dynamique simple prend un argument, un entier 32 bits, et retourne le carré 64 bits de cet entier.  Un délégué générique est utilisé pour appeler la méthode.  
  
 La deuxième méthode dynamique possède deux paramètres, de type `Example` et de type `int` \(`Integer` en Visual Basic\).  Une fois la méthode dynamique créée, elle est liée à une instance de `Example`, à l'aide d'un délégué générique qui possède un argument de type `int`.  Le délégué n'a pas d'argument de type `Example`, car le premier paramètre de la méthode reçoit toujours l'instance liée de `Example`.  Lors de l'appel du délégué, seul l'argument `int` est fourni.  Cette méthode dynamique accède à un champ privé de la classe `Example` et retourne le produit du champ privé et de l'argument `int`.  
  
 L'exemple de code définit des délégués qui peuvent être utilisés pour exécuter les méthodes.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## Compilation du code  
  
-   Le code contient les instructions `using` C\# \(`Imports` en Visual Basic\) nécessaires à la compilation.  
  
-   Aucune référence d'assembly supplémentaire n'est requise.  
  
-   Compilez le code sur la ligne de commande à l'aide de csc.exe, vbc.exe ou cl.exe.  Pour compiler le code dans Visual Studio , placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 <xref:System.Reflection.Emit.DynamicMethod>   
 [Using Reflection Emit](http://msdn.microsoft.com/fr-fr/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/fr-fr/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)