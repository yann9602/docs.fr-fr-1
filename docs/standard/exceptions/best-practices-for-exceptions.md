---
title: Meilleures pratiques pour les exceptions
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
- cpp
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87f9287c3714416ee5d6b63f3c9db311bb97b131
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2017
---
# <a name="best-practices-for-exceptions"></a>Bonnes pratiques pour les exceptions

Une application bien conçue gère les exceptions et les erreurs pour empêcher les incidents d'applications. Cette section présente les bonnes pratiques pour la gestion et la création des exceptions.

## <a name="use-trycatchfinally-blocks"></a>Utiliser des blocs try/catch/finally

Utilisez des blocs `try`/`catch`/`finally` autour du code susceptible de générer une exception. 

Dans les blocs `catch`, veillez à toujours classer les exceptions de la plus spécifique à la moins spécifique.

Utilisez un bloc `finally` pour nettoyer les ressources, que la récupération soit possible ou non.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Gérer les conditions courantes sans lever d’exception

En ce qui concerne les conditions susceptibles de se produire, mais pouvant déclencher une exception, gérez-les de façon à éviter l’exception. Par exemple, si vous essayez de fermer une connexion déjà fermée, vous obtenez une exception `InvalidOperationException`. Vous pouvez l’éviter avec une instruction `if` qui permet de vérifier l’état de la connexion avant d’essayer de la fermer.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Si vous ne vérifiez pas l’état de la connexion avant de la fermer, vous pouvez intercepter l’exception `InvalidOperationException`.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Le choix de la méthode dépend de la fréquence à laquelle l’événement doit se produire.

- Utilisez la gestion des exceptions si l'événement ne se produit pas très souvent, c'est-à-dire, si l'événement est véritablement exceptionnel et indique une erreur (telle qu'une fin de fichier inattendue). Lorsque vous utilisez la gestion des exceptions, la quantité de code exécutée en situation normale est moindre.

- Recherchez les conditions d’erreur dans le code si l’événement se produit régulièrement et peut être considéré comme faisant partie de l’exécution normale. Quand vous recherchez les conditions d’erreur courantes, vous exécutez moins de code, car vous évitez les exceptions.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Concevoir des classes pour éviter les exceptions

Une classe peut fournir des méthodes ou propriétés qui vous permettent d’éviter d’effectuer un appel susceptible de déclencher une exception. Par exemple, une classe <xref:System.IO.FileStream> fournit des méthodes qui permettent de déterminer si la fin du fichier a été atteinte. Ces méthodes peuvent servir à éviter l’exception qui est levée si vous dépassez la fin du fichier pendant la lecture. L’exemple suivant montre comment lire un fichier jusqu’à la fin sans lever d’exception.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Un autre moyen d’éviter les exceptions est de retourner Null pour les cas d’erreur très répandus au lieu de lever une exception. Un cas d'erreur très répandu peut être considéré comme un flux de contrôle normal. En retournant null dans ces cas-là, vous réduisez l'impact sur les performances d'une application.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Lever des exceptions au lieu de retourner un code d’erreur

Les exceptions font en sorte que les échecs ne passent pas inaperçus parce que l’appel du code n’a pas vérifié le code de retour. 

## <a name="use-the-predefined-net-exception-types"></a>Utiliser les types d’exception .NET prédéfinis

N'introduisez une nouvelle classe d'exception que quand aucune classe d'exception prédéfinie ne s'applique. Par exemple :

- Levez une exception <xref:System.InvalidOperationException> si un appel de jeu de propriétés ou de méthode n'est pas approprié étant donné l'état actuel de l'objet.

- Levez une exception <xref:System.ArgumentException> ou l’une des classes prédéfinies qui dérivent de <xref:System.ArgumentException> si des paramètres non valides sont passés.

## <a name="end-exception-class-names-with-the-word-exception"></a>Terminer les noms de classes d’exception par le mot `Exception`

Quand une exception personnalisée est nécessaire, nommez-la de manière appropriée et dérivez-la de la classe <xref:System.Exception>. Exemple :

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Inclure trois constructeurs dans des classes d’exception personnalisées

Utilisez au moins les trois constructeurs communs pendant la création de vos propres classes d’exception : le constructeur par défaut, un constructeur qui prend un message de type chaîne et un constructeur qui prend un message de type chaîne et une exception interne.

* <xref:System.Exception.%23ctor>, qui utilise les valeurs par défaut.
  
* <xref:System.Exception.%23ctor%28System.String%29>, qui accepte un message de type chaîne.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, qui accepte un message de type chaîne et une exception interne.  
  
Pour obtenir un exemple, consultez [Guide pratique : créer des exceptions définies par l’utilisateur](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Vérifier que les données d’exception sont disponibles quand le code s’exécute à distance

Quand vous créez des exceptions définies par l’utilisateur, vous devez vérifier que les métadonnées des exceptions sont disponibles pour le code qui s’exécute à distance. 

Par exemple, sur des implémentations .NET qui prennent en charge les domaines d’application, les exceptions peuvent se produire entre les domaines d’application. Supposons que le domaine d’application A crée le domaine d’application B, lequel exécute du code qui lève une exception. Pour que le domaine d’application A intercepte et gère l’exception correctement, il doit pouvoir trouver l’assembly qui contient l’exception levée par le domaine d’application B. Si le domaine d’application B lève une exception qui est contenue dans un assembly sous sa base d’application, mais pas sous la base d’application du domaine d’application A, le domaine d’application A ne peut pas trouver l’exception et le Common Language Runtime lève une exception <xref:System.IO.FileNotFoundException>. Pour éviter cette situation, vous pouvez déployer l'assembly qui contient les informations sur les exceptions de deux façons :

- Placez l'assembly dans une base d'application commune partagée par les deux domaines d'application.

    \- ou -

- Si les domaines ne partagent pas une base d'application commune, signez l'assembly qui contient les informations sur les exceptions à l'aide d'un nom fort et déployez l'assembly dans le Global Assembly Cache.

## <a name="include-a-localized-description-string-in-every-exception"></a>Inclure une chaîne de description localisée dans chaque exception

Le message d’erreur que l’utilisateur voit est dérivé de la chaîne de description de l’exception qui a été levée et non du nom de la classe d’exception.

## <a name="use-grammatically-correct-error-messages"></a>Utiliser des messages d’erreur grammaticalement corrects

Écrivez des phrases claires et insérez une ponctuation finale. Chaque phrase de la chaîne de description d'une exception doit se terminer par un point. Par exemple, « la table du journal a débordé. » est une chaîne de description appropriée.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Dans les exceptions personnalisées, fournir des propriétés supplémentaires si nécessaire

Fournissez des propriétés supplémentaires (autres que la chaîne de description) pour une exception uniquement s'il existe un scénario par programmation dans lequel les informations supplémentaires sont utiles. Par exemple, la classe <xref:System.IO.FileNotFoundException> fournit la propriété <xref:System.IO.FileNotFoundException.FileName>.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Placer des instructions throw pour que la trace de la pile soit utile

La trace de la pile commence à l'instruction où l'exception est levée et se termine à l'instruction `catch` qui intercepte l'exception.

## <a name="use-exception-builder-methods"></a>Utiliser des méthodes de générateur d’exceptions

Il est fréquent qu'une classe lève la même exception à partir de différents endroits de son implémentation. Pour éviter un excès de code, utilisez des méthodes d'assistance qui créent une exception et la retournent. Exemple :

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
Dans certains cas, il est plus approprié d’utiliser le constructeur de l’exception pour générer l’exception. Un exemple est une classe d’exception global comme <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Nettoyer les résultats intermédiaires quand vous levez une exception

Les appelants doivent supposer qu'il n'y a aucun effet secondaire quand une exception est levée à partir d'une méthode. Par exemple, si vous avez du code qui transfère de l’argent en le retirant d’un compte pour le déposer dans un autre, et qu’une exception est levée pendant l’exécution du transfert, vous ne voulez pas que le retrait reste en vigueur.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Pour gérer cette situation, vous pouvez intercepter toutes les exceptions levées par la transaction de dépôt et annuler le retrait.

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

Cet exemple illustre l’utilisation de `throw` pour lever de nouveau l’exception d’origine, ce qui peut permettre aux appelants de voir plus facilement la véritable cause du problème sans avoir à examiner la propriété <xref:System.Exception.InnerException>. Vous pouvez aussi lever une nouvelle exception et inclure l’exception d’origine comme exception interne :

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Voir aussi  
[Exceptions](index.md)
