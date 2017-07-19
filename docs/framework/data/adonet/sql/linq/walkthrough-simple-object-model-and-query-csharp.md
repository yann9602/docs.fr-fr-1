---
title: "Proc&#233;dure pas &#224; pas&#160;: requ&#234;te et mod&#232;le objet simples (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure pas &#224; pas&#160;: requ&#234;te et mod&#232;le objet simples (C#)
Cette procédure pas à pas propose un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de bout en bout essentiel qui présente peu de difficultés. Vous allez créer une classe d'entité qui modélise la table Customers dans l'exemple de base de données Northwind.  Vous créerez ensuite une requête simple pour répertorier les clients localisés à Londres.  
  
 Cette procédure pas à pas est orientée code en termes de conception pour permettre l'affichage des concepts [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  En temps normal, vous utilisez le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour créer votre modèle objet.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C\#.  
  
## Composants requis  
  
-   Les fichiers sont stockés dans un dossier dédié, c:\\linqtest5.  Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
-   Cette procédure pas à pas requiert l'exemple de base de données Northwind.  Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.  Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  Après avoir téléchargé la base de données, copiez le fichier dans le dossier c:\\linqtest5.  
  
## Vue d'ensemble  
 Cette procédure pas à pas se compose de six tâches principales :  
  
-   Création d'une solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Mappage d'une classe à une table de base de données.  
  
-   Désignation de propriétés sur la classe pour représenter des colonnes de base de données.  
  
-   Spécification de la connexion à la base de données Northwind.  
  
-   Création d'une requête simple à exécuter sur la base de données.  
  
-   Exécution de la requête et observation des résultats.  
  
## Création d'une solution LINQ to SQL  
 Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
#### Pour créer une solution LINQ to SQL  
  
1.  Dans le menu **Fichier** de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans le volet **Types de projets** de la boîte de dialogue **Nouveau projet**, cliquez sur **Visual C\#**.  
  
3.  Dans le volet **Modèles**, cliquez sur **Application console**.  
  
4.  Dans la zone **Nom**, tapez LinqConsoleApp.  
  
5.  Dans la zone **Emplacement**, vérifiez où vous souhaitez stocker vos fichiers projet.  
  
6.  Cliquez sur **OK**.  
  
## Ajout de références et de directives LINQ  
 Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.  Si System.Data.Linq n'est pas répertorié comme une référence dans votre projet \(développez le nœud **Références** dans l'**Explorateur de solutions**\), ajoutez\-le comme indiqué dans les étapes suivantes.  
  
#### Pour ajouter System.Data.Linq  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur **.NET**, sur l'assembly System.Data.Linq, puis sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
3.  Ajoutez les directives suivantes en haut de **Program.cs** :  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## Mappage d'une classe à une table de base de données  
 Au cours de cette étape, vous allez créer une classe et la mapper à une table de base de données.  Ce type de classe est appelé *classe d'entité*.  Notez que le mappage s'effectue simplement en ajoutant l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.  La propriété <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> spécifie le nom de la table dans la base de données.  
  
#### Pour créer une classe d'entité et la mapper à une table de base de données  
  
-   Tapez ou collez le code suivant dans Program.cs juste au\-dessus de la déclaration de classe `Program` :  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## Désignation de propriétés sur la classe pour représenter des colonnes de base de données  
 Au cours de cette étape, vous allez effectuer plusieurs tâches.  
  
-   Utilisez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour désigner les propriétés `CustomerID` et `City` sur la classe d'entité comme représentant des colonnes de la table de base de données.  
  
-   Désignez la propriété `CustomerID` comme représentant une colonne de clé primaire dans la base de données.  
  
-   Désignez les champs `_CustomerID` et `_City` pour le stockage privé.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut ensuite stocker et récupérer directement des valeurs, au lieu d'utiliser des accesseurs publics qui peuvent inclure la logique métier.  
  
#### Pour représenter les caractéristiques de deux colonnes de base de données  
  
-   Tapez ou collez le code suivant dans Program.cs à l'intérieur des accolades pour la classe `Customer`.  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## Spécification de la connexion à la base de données Northwind  
 Au cours de cette étape, vous allez utiliser un objet <xref:System.Data.Linq.DataContext> pour établir une connexion entre vos structures de données basées sur du code et la base de données elle\-même.  Le <xref:System.Data.Linq.DataContext> est le canal principal par le biais duquel vous récupérez des objets de la base de données et soumettez des modifications.  
  
 Déclarez également un `Table<Customer>` comme jouant le rôle de table typée logique pour vos requêtes sur la table Customers dans la base de données.  La création et l'exécution de ces requêtes s'effectueront dans des étapes ultérieures.  
  
#### Pour spécifier la connexion de base de données  
  
-   Tapez ou collez le code suivant dans la méthode `Main` :  
  
     Notez que le fichier `northwnd.mdf` est censé se trouver dans le dossier linqtest5.  Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## Création d'une requête simple  
 Au cours de cette étape, vous allez créer une requête pour rechercher les clients localisés à Londres dans la table Customers de la base de données.  Le code de requête de cette étape décrit simplement la requête.  Il ne l'exécute pas.  Cette approche est connue sous le nom d'*exécution différée*.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md).  
  
 Vous produirez également une sortie de journal pour afficher les commandes SQL générées par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  Cette fonction d'enregistrement \(qui utilise <xref:System.Data.Linq.DataContext.Log%2A>\) est utile pour le débogage et pour déterminer que les commandes envoyées à la base de données représentent précisément votre requête.  
  
#### Pour créer une requête simple  
  
-   Tapez ou collez le code suivant dans la méthode `Main` après la déclaration `Table<Customer>` :  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## Exécution de la requête  
 Dans cette étape, vous allez exécuter la requête.  Les expressions de requête créées au cours des étapes précédentes ne sont pas évaluées tant que les résultats ne sont pas nécessaires.  Lorsque vous commencez l'itération `foreach`, une commande SQL est exécutée sur la base de données et les objets sont matérialisés.  
  
#### Pour exécuter la requête  
  
1.  Tapez ou collez le code suivant à la fin de la méthode `Main` \(après la description de la requête\).  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  Appuyez sur F5 pour déboguer l'application.  
  
    > [!NOTE]
    >  Si votre application génère une erreur d'exécution, consultez la section Dépannage de la rubrique [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
     Les résultats de la requête dans la fenêtre de console doivent apparaître comme suit :  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  Appuyez sur Entrée dans la fenêtre de console pour fermer l'application.  
  
## Étapes suivantes  
 La rubrique [Procédure pas à pas : interrogation de relations \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) est la suite de cette procédure pas à pas.  La procédure pas à pas Interrogation de relations montre comment [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] peut interroger des tables, comme les *jointures* dans une base de données relationnelle.  
  
 Si vous souhaitez suivre la procédure pas à pas Interrogation de relations, pensez à enregistrer la solution de la procédure que vous venez d'exécuter car elle est indispensable.  
  
## Voir aussi  
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)