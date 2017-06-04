---
title: "TPL and Traditional .NET Framework Asynchronous Programming | Microsoft Docs"
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
  - "tasks, with other asynchronous models"
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# TPL and Traditional .NET Framework Asynchronous Programming
Le .NET Framework fournit les deux modèles standard suivants pour l'exécution d'opérations asynchrones liées aux E\/S et orientées calculs :  
  
-   Le modèle de programmation asynchrone, dans lequel les opérations asynchrones sont représentées par une paire de méthodes Begin\/End telles que <xref:System.IO.FileStream.BeginRead%2A?displayProperty=fullName> et <xref:System.IO.Stream.EndRead%2A?displayProperty=fullName>.  
  
-   Le modèle asynchrone basé sur des événements, dans lequel les opérations asynchrones sont représentées par une paire méthode\/événement et nommées *NomOpération*Async et *NomOpération*Completed, par exemple, <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=fullName> et <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=fullName>.  \(Le modèle asynchrone basé sur des événements a été introduit avec le .NET Framework version 2.0\).  
  
 La bibliothèque parallèle de tâches peut être utilisée de plusieurs façons conjointement à l'un ou l'autre des modèles asynchrones.  Vous pouvez exposer à la fois les opérations de modèle de programmation asynchrone et de modèle asynchrone basé sur des événements en tant que Tâches aux consommateurs de la bibliothèque, ou bien exposer les modèles de programmation asynchrone et utiliser des objets Task pour les implémenter en interne.  Dans les deux scénarios, en utilisant des objets Task, vous pouvez simplifier le code et bénéficier des fonctionnalités utiles suivantes :  
  
-   Enregistrer des rappels sous la forme de continuations de tâches, à tout moment après le lancement de la tâche.  
  
-   Coordonner plusieurs opérations qui s'exécutent en réponse à une méthode `Begin_`, à l'aide des méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> et <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A>, ou des méthodes <xref:System.Threading.Tasks.Task.WaitAll%2A> ou <xref:System.Threading.Tasks.Task.WaitAny%2A>.  
  
-   Encapsuler des opérations asynchrones liées aux E\/S et orientées calcul dans le même objet Task.  
  
-   Surveiller l'état de l'objet Task.  
  
-   Marshaler le statut d'une opération sur un objet Task à l'aide de <xref:System.Threading.Tasks.TaskCompletionSource%601>.  
  
## Encapsulation d'opérations de modèle de programmation asynchrone dans une tâche  
 Les classes <xref:System.Threading.Tasks.TaskFactory?displayProperty=fullName> et <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=fullName> fournissent plusieurs surcharges des méthodes <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=fullName> qui vous permettent d'encapsuler une paire de méthodes de modèle de programmation asynchrone Begin\/End dans une instance <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.  Les différentes surcharges s'adaptent à toutes les paires de méthode Begin\/End possédant de zéro à trois paramètres d'entrée.  
  
 Pour les paires ayant des méthodes `End` qui retournent une valeur \(`Function` en Visual Basic\), utilisez les méthodes de <xref:System.Threading.Tasks.TaskFactory%601> qui créent un <xref:System.Threading.Tasks.Task%601>.  Pour les méthodes `End` qui retournent void \(`Sub` en Visual Basic\), utilisez les méthodes de <xref:System.Threading.Tasks.TaskFactory> qui créent un <xref:System.Threading.Tasks.Task>.  
  
 Pour les rares cas dans lesquels la méthode `Begin` a plus de trois paramètres ou contient les paramètres `ref` ou `out`, les surcharges `FromAsync` supplémentaires qui encapsulent uniquement la méthode `End` sont fournies.  
  
 L'exemple suivant montre la signature de la surcharge `FromAsync` qui correspond aux méthodes <xref:System.IO.FileStream.BeginRead%2A?displayProperty=fullName> et <xref:System.IO.FileStream.EndRead%2A?displayProperty=fullName>.  Cette surcharge prend trois paramètres d'entrée, comme suit.  
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
 Le premier paramètre est un délégué <xref:System.Func%606> qui correspond à la signature de la méthode <xref:System.IO.FileStream.BeginRead%2A?displayProperty=fullName>.  Le deuxième paramètre est un délégué <xref:System.Func%602> qui prend un <xref:System.IAsyncResult> et retourne un `TResult`.  Étant donné que <xref:System.IO.FileStream.EndRead%2A> retourne un entier, le compilateur déduit le type de `TResult` en tant que <xref:System.Int32> et le type de la tâche en tant que <xref:System.Threading.Tasks.Task>.  Les quatre derniers paramètres sont identiques à ceux de la méthode <xref:System.IO.FileStream.BeginRead%2A?displayProperty=fullName> :  
  
-   Tampon dans lequel stocker les données de fichiers.  
  
-   Dans le tampon, offset à partir duquel commencer l'écriture des données.  
  
-   Quantité maximale de données à lire dans le fichier.  
  
-   Objet facultatif qui stocke les données d'état définies par l'utilisateur à passer au rappel.  
  
### Utilisation de ContinueWith pour les fonctionnalités de rappel  
 Si vous devez accéder aux données d'un fichier, et non juste au nombre d'octets, la méthode <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> n'est pas suffisante.  Utilisez plutôt <xref:System.Threading.Tasks.Task>, dont la propriété `Result` contient les données de fichier.  Pour cela, ajoutez une continuation à la tâche d'origine.  La continuation exécute le travail généralement effectué par le délégué <xref:System.AsyncCallback>.  Elle est appelée quand l'antécédent est terminé et que le tampon de données est rempli.  \(L'objet <xref:System.IO.FileStream> doit être fermé avant le retour.\)  
  
 L'exemple suivant montre comment retourner un <xref:System.Threading.Tasks.Task> qui encapsule la paire BeginRead\/EndRead de la classe <xref:System.IO.FileStream>.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 La méthode peut ensuite être appelée, comme suit.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### Fourniture de données d'état personnalisées  
 Dans les opérations <xref:System.IAsyncResult> typiques, si votre délégué <xref:System.AsyncCallback> a besoin de certaines données d'état personnalisées, vous devez les passer via le dernier paramètre de la méthode `Begin`, afin que les données puissent être empaquetées dans l'objet <xref:System.IAsyncResult> qui est finalement passé à la méthode de rappel.  Cela n'est en général pas obligatoire quand les méthodes `FromAsync` sont utilisées.  Si les données personnalisées sont connues de la continuation, elles peuvent être capturées directement dans le délégué de continuation.  L'exemple suivant ressemble au précédent, mais au lieu d'examiner la propriété `Result` de la tâche antérieure, la continuation examine les données d'état personnalisées directement accessibles au délégué utilisateur de la continuation.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### Synchronisation de plusieurs tâches FromAsync  
 Les méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> et <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> statiques offrent une flexibilité supplémentaire en cas d'utilisation avec les méthodes `FromAsync`.  L'exemple suivant montre comment initialiser plusieurs opérations d'E\/S asynchrones et attendre qu'elles soient toutes terminées avant d'exécuter la continuation.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### Tâches FromAsync pour la méthode End uniquement  
 Pour les rares cas dans lesquels la méthode `Begin` nécessite plus de trois paramètres d'entrée, ou a des paramètres `ref` ou `out`, vous pouvez utiliser les surcharges `FromAsync`, par exemple, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=fullName>, qui représentent uniquement la méthode `End`.  Ces méthodes peuvent également être utilisées pour tous les scénarios dans lesquels vous est passé un <xref:System.IAsyncResult> que vous voulez encapsuler dans une tâche.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### Lancement et annulation de tâches FromAsync  
 La tâche retournée par une méthode `FromAsync` a l'état WaitingForActivation et sera lancée à un moment donné par le système après la création de la tâche.  Si vous essayez d'appeler Start pour une telle tâche, une exception sera levée.  
  
 Vous ne pouvez pas annuler une tâche `FromAsync`, car les API .NET Framework sous\-jacentes ne prennent actuellement pas en charge l'annulation d'opérations d'E\/S réseau ou de fichier en cours.  Vous pouvez ajouter des fonctionnalités d'annulation à une méthode qui encapsule un appel `FromAsync`, mais vous pouvez répondre uniquement à l'annulation avant que `FromAsync` soit appelé ou terminé \(par exemple, dans une tâche de continuation\).  
  
 Certaines classes prenant en charge le modèle asynchrone basé sur des événements, comme <xref:System.Net.WebClient>, prennent en charge l'annulation et vous pouvez intégrer ces fonctionnalités d'annulation native à l'aide de jetons d'annulation.  
  
## Exposition d'opérations complexes de modèle asynchrone basé sur des événements en tant que tâches  
 La bibliothèque parallèle de tâches ne fournit pas de méthodes conçues spécifiquement pour encapsuler une opération asynchrone basée sur des événements de la même façon que la famille `FromAsync` de méthodes encapsule le modèle <xref:System.IAsyncResult>.  Toutefois, la bibliothèque parallèle de tâches fournit la classe <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=fullName>, qui peut être utilisée pour représenter tout ensemble d'opérations arbitraire tel qu'un <xref:System.Threading.Tasks.Task%601>.  Les opérations peuvent être synchrones ou asynchrones et peuvent être liées aux E\/S ou orientées calcul, ou les deux.  
  
 L'exemple suivant montre comment utiliser un <xref:System.Threading.Tasks.TaskCompletionSource%601> pour exposer un ensemble d'opérations <xref:System.Net.WebClient> asynchrones à du code client en tant que <xref:System.Threading.Tasks.Task%601> de base.  Cette méthode vous permet d'entrer un tableau d'URL web et un terme ou nom à rechercher, puis retourne le nombre d'occurrences de ce terme ou nom sur chaque site.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Pour obtenir un exemple plus complet, incluant la gestion des exceptions et indiquant comment appeler la méthode depuis le code client, consultez [How to: Wrap EAP Patterns in a Task](../../../docs/standard/parallel-programming/how-to-wrap-eap-patterns-in-a-task.md).  
  
 Souvenez\-vous que toute tâche créée par un <xref:System.Threading.Tasks.TaskCompletionSource%601> sera lancée par ce TaskCompletionSource et que le code utilisateur ne doit donc pas appeler la méthode Start dans cette tâche.  
  
## Implémentation du modèle de programmation asynchrone à l'aide de tâches  
 Dans certains scénarios, il peut être souhaitable d'exposer directement le modèle <xref:System.IAsyncResult> à l'aide de paires de méthodes Begin\/End dans une API.  Vous pouvez, par exemple, maintenir la cohérence avec les API existantes ou posséder des outils automatisés qui nécessitent ce modèle.  Dans de tels cas, vous pouvez utiliser des tâches pour simplifier l'implémentation en interne du modèle de programmation asynchrone.  
  
 L'exemple suivant montre comment utiliser des tâches pour implémenter une paire de méthodes de modèle de programmation asynchrone Begin\/End pour une méthode orientée calcul de longue durée.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## Utilisation de l'exemple de code StreamExtensions  
 Le fichier Streamextensions.cs, dans [Exemples de programmation parallèle avec .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=165717) sur le site web MSDN, contient plusieurs implémentations de référence qui utilisent des objets Task pour les opérations d'E\/S réseau ou de fichier asynchrones.  
  
## Voir aussi  
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)