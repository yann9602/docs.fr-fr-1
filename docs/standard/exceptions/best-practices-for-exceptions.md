---
title: "Meilleures pratiques pour les exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, meilleures pratiques"
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# Meilleures pratiques pour les exceptions
Une application bien conçue gère les exceptions et les erreurs pour empêcher les incidents d'applications.  Cet article présente les meilleures pratiques pour la gestion et la création des exceptions.  
  
## Gestion des exceptions  
 La liste suivante contient des recommandations générales pour la gestion des exceptions dans votre application.  
  
-   Utilisez le code de gestion des exceptions \(blocs `try`\/`catch`\) correctement.  Vous pouvez également vérifier par programmation la présence d'une condition qui risque probablement de se produire sans le recours à la gestion des exceptions.  
  
     **Vérifications par programmation**.  L'exemple suivant utilise une instruction `if` pour déterminer si une connexion est fermée.  Si ce n'est pas le cas, l'exemple ferme la connexion au lieu de lever une exception.  
  
     [!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
     [!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
     [!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  
  
     **Gestion des exceptions**.  L'exemple suivant utilise un bloc `try`\/`catch` pour activer la connexion et lever une exception si la connexion n'est pas fermée.  
  
     [!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
     [!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
     [!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  
  
     La méthode que vous choisissez dépend de la fréquence à laquelle l'événement se produit.  
  
    -   Utilisez la gestion des exceptions si l'événement ne se produit pas très souvent, c'est\-à\-dire, si l'événement est véritablement exceptionnel et indique une erreur \(telle qu'une fin de fichier inattendue\).  Lorsque vous utilisez la gestion des exceptions, la quantité de code exécutée en situation normale est moindre.  
  
    -   Utilisez la méthode par programmation pour rechercher les erreurs si l'événement se produit régulièrement et peut être considéré comme faisant partie de l'exécution normale.  Lorsque vous recherchez des erreurs par programmation, davantage de code est exécuté si une exception se produit.  
  
-   Utilisez des blocs `try`\/`catch` autour du code susceptible de générer une exception, et utilisez un bloc `finally` pour nettoyer les ressources, au besoin.  Ainsi, l'instruction `try` génère l'exception, l'instruction `catch` la gère et l'instruction `finally` ferme ou libère les ressources qu'une exception se produise ou non.  
  
-   Dans les blocs `catch`, veillez à toujours classer les exceptions de la plus spécifique à la moins spécifique.  Cette technique permet de gérer l'exception spécifique avant qu'elle ne passe à un bloc `catch` plus général.  
  
## Création et levée d'exceptions  
 La liste suivante contient des recommandations pour la création de vos propres exceptions et lorsqu'elles doivent être levées.  Pour plus d'informations, voir [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md).  
  
-   Créez des classes de façon qu'une exception ne soit jamais levée en usage normal.  Par exemple, une classe <xref:System.IO.FileStream> fournit des méthodes qui permettent de déterminer si la fin du fichier a été atteinte.  Vous évitez ainsi l'exception qui est levée si vous dépassez la fin du fichier pendant la lecture.  L'exemple suivant montre comment lire le fichier jusqu'à la fin.  
  
     [!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
     [!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
     [!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  
  
-   Levez des exceptions au lieu de retourner un code d'erreur ou HRESULT.  
  
-   Retourne null pour les cas d'erreur très répandus au lieu de lever une exception.  Un cas d'erreur très répandu peut être considéré comme un flux de contrôle normal.  En retournant null dans ces cas\-là, vous réduisez l'impact sur les performances d'une application.  
  
-   Dans la plupart des cas, utilisez les types d'exception .NET Framework prédéfinis.  N'introduisez une nouvelle classe d'exception que quand aucune classe d'exception prédéfinie ne s'applique.  
  
-   Levez une exception <xref:System.InvalidOperationException> si un appel de jeu de propriétés ou de méthode n'est pas approprié étant donné l'état actuel de l'objet.  
  
-   Levez une exception <xref:System.ArgumentException> ou une classe dérivée de <xref:System.ArgumentException> si des paramètres incorrects sont passés.  
  
-   Pour la plupart des applications, dérivez des exceptions personnalisées à partir de la classe <xref:System.Exception>.  La dérivation de la classe <xref:System.ApplicationException> n'apporte pas beaucoup d'avantages.  
  
-   Terminez les noms de classes d'exception par le mot « Exception ».  Par exemple :  
  
     [!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
     [!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
     [!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  
  
-   En C\# et C\+\+, utilisez au moins les trois constructeurs communs lors de la création de vos propres classes d'exception : le constructeur par défaut, un constructeur qui prend un message de type chaîne, et un constructeur qui prend un message de type chaîne et une exception interne.  Pour obtenir un exemple, consultez [Comment : créer des exceptions définies par l'utilisateur](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md).  
  
    1.  <xref:System.Exception.%23ctor>, qui utilise les valeurs par défaut.  
  
    2.  <xref:System.Exception.%23ctor%28System.String%29>, qui accepte un message de type chaîne.  
  
    3.  <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, qui accepte un message de type chaîne et une exception interne.  
  
-   Lors de la création d'exceptions définies par l'utilisateur, vous devez vous assurer que les métadonnées des exceptions sont disponibles pour le code qui s'exécute à distance, y compris lorsque des exceptions se produisent à travers des domaines d'application.  Par exemple, supposons que le domaine d'application A crée le domaine d'application B, lequel exécute le code qui lève une exception.  Pour que le domaine d'application A intercepte et gère correctement l'exception, il doit pouvoir trouver l'assembly qui contient l'exception levée par le domaine d'application B.  Si le domaine d'application B lève une exception qui est contenue dans un assembly sous sa base d'application, mais pas sous la base d'application du domaine d'application A, ce dernier ne peut pas trouver l'exception et le Common Language Runtime lève une exception <xref:System.IO.FileNotFoundException>.  Pour éviter cette situation, vous pouvez déployer l'assembly qui contient les informations sur les exceptions de deux façons :  
  
    -   Placez l'assembly dans une base d'application commune partagée par les deux domaines d'application.  
  
         ou  
  
    -   Si les domaines ne partagent pas une base d'application commune, signez l'assembly qui contient les informations sur les exceptions à l'aide d'un nom fort et déployez l'assembly dans le Global Assembly Cache.  
  
-   Insérez une chaîne de description localisée dans chaque exception.  Le message d'erreur que l'utilisateur voit est dérivé non pas de la classe d'exceptions mais de la chaîne de description de l'exception qui a été levée.  
  
-   Créez des messages d'erreur corrects du point de vue de la syntaxe, y compris la ponctuation de fin.  Chaque phrase de la chaîne de description d'une exception doit se terminer par un point.  Par exemple, « Dépassement de la table du journal. » doit être une chaîne de description appropriée.  
  
-   Fournissez des propriétés <xref:System.Exception> pour l'accès par programmation.  Fournissez des propriétés supplémentaires \(autres que la chaîne de description\) pour une exception uniquement s'il existe un scénario par programmation dans lequel les informations supplémentaires sont utiles.  Par exemple, la classe <xref:System.IO.FileNotFoundException> fournit la propriété <xref:System.IO.FileNotFoundException.FileName%2A>.  
  
-   La trace de la pile commence à l'instruction où l'exception est levée et se termine à l'instruction `catch` qui intercepte l'exception.  N'oubliez pas ce fait au moment de déterminer l'endroit auquel vous devez placer une instruction `throw`.  
  
-   Utilisez des méthodes de générateur d'exceptions.  Il est fréquent qu'une classe lève la même exception à partir de différents endroits de son implémentation.  Pour éviter un excès de code, utilisez des méthodes d'assistance qui créent une exception et la retournent.  Par exemple :  
  
     [!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
     [!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
     [!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
     Dans les autres cas, utilisez le constructeur d'exception pour générer l'exception.  Cette approche est plus appropriée pour les classes d'exceptions globales, telles que <xref:System.ArgumentException>.  
  
-   Supprimez les résultats intermédiaires lorsque vous levez une exception.  Les appelants doivent supposer qu'il n'y a aucun effet secondaire quand une exception est levée à partir d'une méthode.  
  
## Voir aussi  
 [Exceptions](../../../docs/standard/exceptions/index.md)