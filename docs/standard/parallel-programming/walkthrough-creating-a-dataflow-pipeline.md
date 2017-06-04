---
title: "Walkthrough: Creating a Dataflow Pipeline | Microsoft Docs"
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
  - "dataflow pipelines, creating with TPL"
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, creating dataflow pipeline"
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Walkthrough: Creating a Dataflow Pipeline
Bien que vous puissiez utiliser les méthodes <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=fullName>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=fullName> et <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=fullName> pour recevoir des messages des blocs sources, vous pouvez également connecter des blocs de messages pour former un *pipeline de flux de données*.  Un pipeline de flux de données est une série de composants, ou de *blocs de flux de données*, qui effectuent chacun une tâche spécifique qui contribue à un plus grand objectif.  Chaque bloc de flux de données d'un pipeline de flux de données effectue un travail lorsqu'il reçoit un message d'un autre bloc de flux de données.  Ce processus s'apparente à une chaîne de montage en construction automobile.  Comme chaque véhicule passe via la ligne de montage, un poste assemble le châssis, le suivant installe le moteur, et ainsi de suite.  Étant donné qu'une ligne d'assemblage permet à plusieurs véhicules d'être assemblés en même temps, cela fournit une productivité supérieure à l'assemblage un par un des véhicules.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL \(espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=fullName>\) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
 Ce document montre un pipeline de flux de données qui télécharge le livre *L'Illiade d'Homère* à partir d'un site web et recherche dans le texte les mots dont l'inversion des caractères permet d'obtenir un autre mot.  La formation du pipeline de flux de données dans ce document comprend les étapes suivantes :  
  
1.  Créez des blocs de flux de données qui participent au pipeline.  
  
2.  Connectez chaque bloc de flux de données au bloc suivant dans le pipeline.  Chaque bloc reçoit comme entrée la sortie du bloc précédent du pipeline.  
  
3.  Pour chaque bloc de flux de données, créez une tâche de continuation qui définit le bloc suivant à l'état arrêté après que le bloc précédent ait terminé.  
  
4.  Publiez les données au début du pipeline.  
  
5.  Marquez le début du pipeline comme terminé.  
  
6.  Attendez que le pipeline termine tous les travaux.  
  
## Composants requis  
 Lisez [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de commencer cette procédure pas à pas.  
  
## Création d'une application console  
 Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], créez un projet d'application console [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].  Ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
 Vous pouvez également créer un fichier et le nommer `ReverseWords.cs` \(`ReverseWords.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), puis exécuter la commande suivante dans une fenêtre d'invite de commandes Visual Studio pour compiler le projet.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe \/r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 Ajoutez le code suivant à votre projet pour créer l'application de base.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## Création des blocs de flux de données  
 Ajoutez le code suivant à la méthode `Main` pour créer des blocs de flux de données qui participent au pipeline.  Le tableau suivant résume le rôle de chaque membre du pipeline.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Télécharge le texte du livre depuis le Web.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Sépare le texte du livre dans un tableau de mots.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Supprime les mots courts du tableau de mots, classe les mots obtenus par ordre alphabétique, et supprime les doublons.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Recherche tous les mots dans la collection filtrée de tableau de mots dont le changement se produit également dans le tableau de mots.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Affiche les mots et les mots inversés correspondants dans la console.|  
  
 Bien que vous puissiez combiner plusieurs étapes de cet exemple dans le pipeline de flux de données en une étape, l'exemple illustre le concept de composition de plusieurs tâches distinctes de flux de données pour effectuer une plus grande tâche.  L'exemple utilise <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour permettre à chaque membre du pipeline d'exécuter une opération sur les données d'entrée et d'envoyer les résultats à l'étape suivante dans le pipeline.  Le membre `findReversedWords` du pipeline est un objet <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> car il génère des sorties multiples indépendantes pour chaque entrée.  La queue du pipeline, `printReversedWords`, est un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> car elle exécute une action sur son entrée, et ne produit aucun résultat.  
  
## Formation du pipeline  
 Ajoutez le code suivant pour adapter chaque bloc au bloc suivant dans le pipeline.  
  
 Lorsque vous appelez la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> pour adapter un bloc source de flux de données à un bloc cible de flux de données, le bloc source de flux de données se propage au bloc cible lorsque les données sont disponibles.  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## Création des tâches d'exécution  
 Ajoutez le code suivant pour permettre à chaque bloc de flux de données d'effectuer une mesure finale une fois qu'il a traité les données.  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 Pour propager l'exécution via le pipeline, chaque tâche d'exécution définit le bloc de flux de données suivant sur l'état arrêté.  Par exemple, lorsque le début du pipeline est défini sur l'état achevé, il traite tous les messages restants de mise en mémoire tampon, puis exécute la tâche d'exécution, qui définit le deuxième membre du pipeline sur l'état achevé.  Le deuxième membre du pipeline traite ensuite tous les messages restants de mise en mémoire tampon, puis effectue la tâche d'exécution, qui définit le troisième membre du pipeline sur l'état achevé.  Ce processus se poursuit jusqu'à ce que tous les membres du pipeline se terminent.  Cet exemple utilise le mot clé `delegate` \(`Function` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) pour définir les tâches de continuation.  
  
## Publication des données du pipeline  
 Ajoutez le code suivant pour publier l'URL du livre de *l'Iliade d'Homère* au début du pipeline de flux de données.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Cet exemple utilise <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=fullName> pour envoyer des données de façon synchrone au début du pipeline.  Utilisez la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=fullName> lorsque vous devez envoyer de manière asynchrone des données à un nœud de flux de données.  
  
## Fermeture de l'activité du pipeline  
 Ajoutez le code suivant pour indiquer que le début du pipeline est terminé.  Le début du pipeline exécute la tâche de continuation lorsqu'il a traité tous les messages de mise en mémoire tampon.  Cette tâche de continuation propage l'état achevé via le pipeline.  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Cet exemple envoie une URL via le pipeline de flux de données à traiter.  Si vous devez envoyer plusieurs entrées par un pipeline, appelez la méthode <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=fullName> après avoir soumis toutes les entrées.  Vous pouvez omettre cette étape si votre application n'a pas de points bien définis à partir desquels les données ne sont plus disponibles ou si l'application n'a pas à attendre que le pipeline se termine.  
  
## Attente de la fermeture du pipeline  
 Ajoutez le code suivant pour attendre que le pipeline se termine.  Étant donné que cet exemple utilise des tâches de continuation pour envoyer l'exécution via le pipeline, l'opération d'agrégation est terminée lorsque la fin du pipeline se termine.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Vous pouvez attendre la fin de flux de données de tous les threads ou de plusieurs threads simultanément.  
  
## Exemple complet  
 L'exemple suivant présente le code complet pour cette visite.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## Étapes suivantes  
 Cet exemple envoie une URL à traiter via le pipeline de flux de données.  Si vous devez envoyer plusieurs valeurs d'entrée via le pipeline, vous pouvez introduire un forme de parallélisme dans votre application similaire à la façon dont des parties peuvent parcourir une fabrique d'automobiles.  Lorsque le premier membre du pipeline envoie son résultat au deuxième membre, il peut traiter un autre élément en parallèle alors que le deuxième membre traite le premier résultat.  
  
 Le parallélisme qui est effectué à l'aide de pipelines de flux de données s'appelle *le parallélisme de granularité grossière* parce qu'il comprend généralement moins de tâches, mais plus grosses.  Vous pouvez également utiliser *le parallélisme de granularité fine* de plus petites tâches de courte durée dans un pipeline de flux de données.  Dans cet exemple, le membre `findReversedWords` du pipeline utilise la méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> pour traiter plusieurs éléments dans la liste des travaux en parallèle.  L'utilisation du parallélisme de granularité fine dans un pipeline de granularité grossière peut améliorer le débit global.  
  
 Vous pouvez également adapter un bloc de flux de données source à plusieurs blocs cibles pour créer *un réseau de flux de données*.  La version surchargée de la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> accepte un objet <xref:System.Predicate%601> qui définit si le bloc cible reçoit les messages en fonction de sa valeur.  La plupart des types de bloc de flux de données qui agissent comme sources envoient des messages à toutes les blocs cibles connectés, dans l'ordre dans lequel ils ont été connectés, jusqu'à ce que l'un des blocs reçoive ce message.  En utilisant ce mécanisme de filtrage, vous pouvez créer des systèmes de blocs de flux de données connectés qui dirigent certaines données via un seul tracé et d'autres données via un autre tracé.  Pour obtenir un exemple qui utilise le filtrage afin de créer un réseau de flux de données, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)