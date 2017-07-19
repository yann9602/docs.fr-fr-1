---
title: "Proc&#233;dure pas &#224; pas&#160;: interrogation de relations (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure pas &#224; pas&#160;: interrogation de relations (C#)
Cette procédure pas à pas explique comment utiliser des *associations* [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour représenter les relations de clé étrangère dans la base de données.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual C\#.  
  
## Composants requis  
 Vous devez avoir terminé [Procédure pas à pas : requête et modèle objet simples \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).  Cette procédure pas à pas est basée sur cette dernière, y compris la présence du fichier northwnd.mdf dans c:\\linqtest5.  
  
## Vue d'ensemble  
 Cette procédure pas à pas se compose de trois tâches principales :  
  
-   Ajout d'une classe d'entité pour représenter la table Orders dans l'exemple de base de données Northwind.  
  
-   Ajout d'annotations à la classe `Customer` pour améliorer la relation entre les classes `Customer` et `Order`.  
  
-   Création et exécution d'une requête pour tenter d'obtenir des informations `Order` en utilisant la classe `Customer`.  
  
## Mappage de relations entre des tables  
 Une fois la définition de classe `Customer` terminée, créez la définition de classe d'entité `Order` qui inclut le code suivant indiquant que `Order.Customer` est une clé étrangère de `Customer.CustomerID`.  
  
#### Pour ajouter la classe d'entité Order  
  
-   Tapez ou collez le code suivant après la classe `Customer` :  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## Annotation de la classe Customer  
 Dans cette étape, annotez la classe `Customer` pour indiquer sa relation avec la classe `Order`.  Cet ajout n'est pas strictement nécessaire étant donné que la définition de la relation dans chacune des directions est suffisante pour créer le lien.  Cependant, l'ajout de cette annotation vous permet de naviguer facilement parmi les objets dans chacune des directions.  
  
#### Pour annoter la classe Customer  
  
-   Tapez ou collez le code suivant dans la classe `Customer` :  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## Création et exécution d'une requête dans la relation entre les classes Order et Customer  
 Vous pouvez désormais accéder aux objets `Order` directement à partir des objets `Customer` ou inversement.  Vous n'avez pas besoin d'une *jointure* explicite entre les clients et les commandes.  
  
#### Pour accéder aux objets Order à l'aide d'objets Customer  
  
1.  Modifiez la méthode `Main` en tapant ou en collant le code suivant dans la méthode :  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Appuyez sur F5 pour déboguer l'application.  
  
    > [!NOTE]
    >  Vous pouvez supprimer le code SQL dans la fenêtre de console en supprimant `db.Log = Console.Out;`.  
  
3.  Appuyez sur Entrée dans la fenêtre de console pour arrêter le débogage.  
  
## Création d'une vue fortement typée de votre base de données  
 Il est beaucoup plus facile de démarrer avec une vue fortement typée de votre base de données.  En effectuant un typage fort de l'objet <xref:System.Data.Linq.DataContext>, vous n'avez pas besoin d'effectuer des appels à <xref:System.Data.Linq.DataContext.GetTable%2A>.  Vous pouvez utiliser des tables fortement typées dans toutes vos requêtes lorsque vous utilisez l'objet <xref:System.Data.Linq.DataContext> fortement typé.  
  
 Dans les étapes suivantes, vous créerez `Customers` comme table fortement typée qui mappe à la table Customers dans la base de données.  
  
#### Pour effectuer un typage fort de l'objet DataContext  
  
1.  Ajoutez le code suivant au\-dessus de la déclaration de classe `Customer`.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Modifiez la méthode `Main` pour utiliser le <xref:System.Data.Linq.DataContext> fortement typé comme suit :  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Appuyez sur F5 pour déboguer l'application.  
  
     La sortie de la fenêtre de console est :  
  
     `ID=WHITC`  
  
4.  Appuyez sur Entrée dans la fenêtre de console pour arrêter le débogage.  
  
## Étapes suivantes  
 La procédure pas à pas suivante \([Procédure pas à pas : manipulation de données \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)\) explique comment manipuler des données.  Cette procédure pas à pas ne requiert pas d'enregistrer les deux procédures pas à pas de cette série que vous avez déjà terminées.  
  
## Voir aussi  
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)