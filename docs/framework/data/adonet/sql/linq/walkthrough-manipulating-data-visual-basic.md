---
title: "Proc&#233;dure pas &#224; pas&#160;: manipulation de donn&#233;es (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure pas &#224; pas&#160;: manipulation de donn&#233;es (Visual Basic)
Cette procédure pas à pas fournit un scénario [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] complet essentiel pour l'ajout, la modification et la suppression de données dans une base de données.  Vous utiliserez une copie de l'exemple de base de données Northwind pour ajouter un client, modifier le nom d'un client et supprimer une commande.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.  
  
## Composants requis  
 Elle requiert les éléments suivants :  
  
-   Les fichiers sont stockés dans un dossier dédié, c:\\linqtest2.  Vous devez créer ce dossier avant de commencer la procédure pas à pas.  
  
-   Exemple de base de données Northwind.  
  
     Si cette base de données n'est pas disponible sur votre ordinateur de développement, vous pouvez la télécharger à partir du site de téléchargement Microsoft.  Pour obtenir des instructions, consultez [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  Après avoir téléchargé la base de données, copiez le fichier northwnd.mdf dans le dossier c:\\linqtest2.  
  
-   Fichier de code Visual Basic généré à partir de la base de données Northwind.  
  
     Vous pouvez générer ce fichier à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou de l'outil SQLMetal.  Cette procédure pas à pas a été écrite à l'aide de l'outil SQLMetal, avec la ligne de commande suivante :  
  
     **sqlmetal \/code:"c:\\linqtest2\\northwind.vb" \/language:vb "C:\\linqtest2\\northwnd.mdf" \/pluralize**  
  
     Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## Vue d'ensemble  
 Cette procédure pas à pas se compose de six tâches principales :  
  
-   Création de la solution [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   Ajout du fichier de code de base de données au projet.  
  
-   Création d'un objet représentant un client.  
  
-   Modification du nom de contact d'un client.  
  
-   Suppression d'une commande.  
  
-   Soumission de ces modifications à la base de données Northwind.  
  
## Création d'une solution LINQ to SQL  
 Au cours de cette première tâche, vous allez créer une solution [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] qui contient les références nécessaires pour générer et exécuter un projet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
#### Pour créer une solution LINQ to SQL  
  
1.  Dans le menu **Fichier** de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], cliquez sur **Nouveau projet**.  
  
2.  Dans le volet **Types de projets** de la boîte de dialogue **Nouveau projet**, sélectionnez **Visual Basic**.  
  
3.  Dans le volet **Modèles**, cliquez sur **Application console**.  
  
4.  Dans la zone **Nom**, tapez LinqDataManipulationApp.  
  
5.  Cliquez sur **OK**.  
  
## Ajout de références et de directives LINQ  
 Cette procédure pas à pas utilise des assemblys qui ne sont pas nécessairement installés par défaut dans votre projet.  Si `System.Data.Linq` n'est pas répertorié comme une référence dans votre projet \(cliquez sur **Afficher tous les fichiers** dans l'**Explorateur de solutions** et développez le nœud **Références**\), ajoutez\-le comme indiqué dans les étapes suivantes.  
  
#### Pour ajouter System.Data.Linq  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis cliquez sur **Ajouter une référence**.  
  
2.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur **.NET**, sur l'assembly System.Data.Linq, puis sur **OK**.  
  
     L'assembly est ajouté au projet.  
  
3.  Dans l'éditeur de code, ajoutez les directives suivantes au\-dessus de **Module1** :  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## Ajout du fichier de code Northwind au projet  
 Ces étapes supposent que vous avez utilisé l'outil SQLMetal pour générer un fichier de code à partir de l'exemple de base de données Northwind.  Pour plus d'informations, consultez la section Composants requis au début de cette procédure pas à pas.  
  
#### Pour ajouter le fichier de code Northwind au projet  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un élément existant**.  
  
2.  Dans la boîte de dialogue **Ajouter un élément existant**, accédez à c:\\linqtest2\\northwind.vb, puis cliquez sur **Ajouter**.  
  
     Le fichier northwind.vb est ajouté au projet.  
  
## Paramétrage de la connexion de base de données  
 Commencez par tester votre connexion à la base de données.  Notez en particulier que le nom de la base de données \(Northwnd\) ne comporte pas de caractère i.  Si vous générez des erreurs au cours des étapes suivantes, examinez le fichier northwind.vb pour déterminer comment la classe partielle Northwind est orthographiée.  
  
#### Pour paramétrer et tester la connexion de base de données  
  
1.  Tapez ou collez le code suivant dans `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  Appuyez sur F5 pour tester l'application à ce stade.  
  
     Une fenêtre de **console** s'ouvre.  
  
     Pour fermer l'application, appuyez sur Entrée dans la fenêtre de **console** ou cliquez sur **Arrêter le débogage** dans le menu **Déboguer** de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
## Création d'une entité  
 La création d'une entité est une opération simple.  Vous pouvez créer des objets \(`Customer`, par exemple\) à l'aide du mot clé `New`.  
  
 Dans cette section et les suivantes, vous apporterez des modifications uniquement au cache local.  Aucune modification n'est envoyée à la base de données tant que vous n'avez pas appelé <xref:System.Data.Linq.DataContext.SubmitChanges%2A> vers la fin de cette procédure pas à pas.  
  
#### Pour ajouter un nouvel objet d'entité Customer  
  
1.  Créez un `Customer` en ajoutant le code suivant avant `Console.ReadLine` dans `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  Appuyez sur F5 pour déboguer la solution.  
  
     Les résultats suivants s'affichent dans la fenêtre de console :  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Notez que la nouvelle ligne n'apparaît pas dans les résultats.  Les nouvelles données n'ont pas encore été soumises à la base de données.  
  
3.  Appuyez sur Entrée dans la fenêtre de **console** pour arrêter le débogage.  
  
## Mise à jour d'une entité  
 Au cours des étapes suivantes, vous allez récupérer un objet `Customer` et modifier l'une de ses propriétés.  
  
#### Pour modifier le nom d'un client  
  
-   Ajoutez le code suivant au\-dessus de `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## Suppression d'une entité  
 Vous pouvez supprimer la première commande à l'aide du même objet Customer.  
  
 Le code suivant montre comment couper les relations entre les lignes et supprimer une ligne de la base de données.  
  
#### Pour supprimer une ligne  
  
-   Ajoutez le code suivant juste au\-dessus de `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## Soumission des modifications à la base de données  
 La dernière étape requise pour la création, la mise à jour et la suppression d'objets consiste à soumettre les modifications à la base de données.  Sans cette étape, vos modifications restent locales et n'apparaissent pas dans les résultats de requêtes.  
  
#### Pour soumettre les modifications à la base de données  
  
1.  Insérez le code suivant juste au\-dessus de `Console.ReadLine` :  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  Insérez le code suivant \(après `SubmitChanges`\) pour afficher les effets avant\/après de la soumission des modifications :  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  Appuyez sur F5 pour déboguer la solution.  
  
     La fenêtre de console se présente comme suit :  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4.  Appuyez sur Entrée dans la fenêtre de **console** pour arrêter le débogage.  
  
> [!NOTE]
>  Une fois que vous avez soumis les modifications \(ajouté le nouveau client\), vous ne pouvez plus exécuter cette solution telle quelle car vous ne pouvez plus ajouter le même client tel quel.  Pour exécuter à nouveau la solution, modifiez la valeur de l'ID client à ajouter.  
  
## Voir aussi  
 [Apprentissage par les procédures pas à pas](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)