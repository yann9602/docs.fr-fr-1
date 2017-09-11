---
title: "Comment : appeler une procédure stockée à l’aide de LINQ (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 40e72ece8399b1ffbe8c5457c63113d563c9f7f8
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a><span data-ttu-id="afb63-102">Comment : appeler une procédure stockée à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb63-102">How to: Call a Stored Procedure by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="afb63-103">Language-Integrated Query (LINQ) permet d’accéder aux informations de base de données, y compris les procédures stockées comme des objets de base de données.</span><span class="sxs-lookup"><span data-stu-id="afb63-103">Language-Integrated Query (LINQ) makes it easy to access database information, including database objects such as stored procedures.</span></span>  
  
 <span data-ttu-id="afb63-104">L’exemple suivant montre comment créer une application qui appelle une procédure stockée dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="afb63-104">The following example shows how to create an application that calls a stored procedure in a SQL Server database.</span></span> <span data-ttu-id="afb63-105">L’exemple montre comment appeler deux procédures stockées différentes dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="afb63-105">The sample shows how to call two different stored procedures in the database.</span></span> <span data-ttu-id="afb63-106">Chaque procédure retourne les résultats d’une requête.</span><span class="sxs-lookup"><span data-stu-id="afb63-106">Each procedure returns the results of a query.</span></span> <span data-ttu-id="afb63-107">Une procédure accepte des paramètres d’entrée, et l’autre procédure ne prend pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="afb63-107">One procedure takes input parameters, and the other procedure does not take parameters.</span></span>  
  
 <span data-ttu-id="afb63-108">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="afb63-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="afb63-109">Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="afb63-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="afb63-110">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="afb63-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="afb63-111">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="afb63-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="afb63-112">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur **Explorateur de serveurs**/**Explorateur de base de données** sur la **affichage** menu.</span><span class="sxs-lookup"><span data-stu-id="afb63-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="afb63-113">Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer** , puis **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="afb63-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="afb63-114">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="afb63-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="afb63-115">Pour ajouter un projet contenant un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="afb63-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="afb63-116">Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="afb63-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="afb63-117">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="afb63-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="afb63-118">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="afb63-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="afb63-119">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="afb63-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="afb63-120">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="afb63-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="afb63-121">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="afb63-121">Click **Add**.</span></span> <span data-ttu-id="afb63-122">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouverte pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="afb63-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a><span data-ttu-id="afb63-123">Pour ajouter des procédures stockées au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="afb63-123">To add stored procedures to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="afb63-124">Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="afb63-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="afb63-125">Développez le **de procédures stockées** dossier.</span><span class="sxs-lookup"><span data-stu-id="afb63-125">Expand the **Stored Procedures** folder.</span></span>  
  
     <span data-ttu-id="afb63-126">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="afb63-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="afb63-127">Cliquez sur le **ventes par année** procédure stockée et faites-le glisser vers le volet de droite du concepteur.</span><span class="sxs-lookup"><span data-stu-id="afb63-127">Click the **Sales by Year** stored procedure and drag it to the right pane of the designer.</span></span> <span data-ttu-id="afb63-128">Cliquez sur le **Ten Most Expensive Products** procédure stockée faites-le glisser vers le volet de droite du concepteur.</span><span class="sxs-lookup"><span data-stu-id="afb63-128">Click the **Ten Most Expensive Products** stored procedure drag it to the right pane of the designer.</span></span>  
  
3.  <span data-ttu-id="afb63-129">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="afb63-129">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="afb63-130">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="afb63-130">Save your project.</span></span>  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a><span data-ttu-id="afb63-131">Pour ajouter du code pour afficher les résultats des procédures stockées</span><span class="sxs-lookup"><span data-stu-id="afb63-131">To add code to display the results of the stored procedures</span></span>  
  
1.  <span data-ttu-id="afb63-132">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="afb63-132">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="afb63-133">Double-cliquez sur Form1 pour ajouter du code à son `Load` événement.</span><span class="sxs-lookup"><span data-stu-id="afb63-133">Double-click Form1 to add code to its `Load` event.</span></span>  
  
3.  <span data-ttu-id="afb63-134">Lorsque vous avez ajouté des procédures stockées au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet pour votre projet.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="afb63-134">When you added stored procedures to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="afb63-135">Cet objet contient le code que vous devez disposer pour accéder à ces procédures.</span><span class="sxs-lookup"><span data-stu-id="afb63-135">This object contains the code that you must have to access those procedures.</span></span> <span data-ttu-id="afb63-136">Le <xref:System.Data.Linq.DataContext>objet pour le projet est nommé d’après le nom du fichier .dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="afb63-136">The <xref:System.Data.Linq.DataContext> object for the project is named based on the name of the .dbml file.</span></span> <span data-ttu-id="afb63-137">Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="afb63-137">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="afb63-138">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>dans votre code et appeler les méthodes de procédures stockées spécifiées par le Concepteur O/R.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="afb63-138">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and call the stored procedure methods specified by the O/R Designer.</span></span> <span data-ttu-id="afb63-139">Pour lier à la <xref:System.Windows.Forms.DataGridView>de l’objet, vous devrez peut-être forcer la requête à exécuter immédiatement en appelant le <xref:System.Linq.Enumerable.ToList%2A>méthode sur les résultats de la procédure stockée.</xref:System.Linq.Enumerable.ToList%2A> </xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="afb63-139">To bind to the <xref:System.Windows.Forms.DataGridView> object, you may have to force the query to execute immediately by calling the <xref:System.Linq.Enumerable.ToList%2A> method on the results of the stored procedure.</span></span>  
  
     <span data-ttu-id="afb63-140">Ajoutez le code suivant à la `Load` événements d’appeler des procédures stockées exposées comme méthodes pour votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="afb63-140">Add the following code to the `Load` event to call either of the stored procedures exposed as methods for your data context.</span></span>  
  
     <span data-ttu-id="afb63-141">[!code-vb[VbLINQtoSQLHowTos n °&1;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="afb63-141">[!code-vb[VbLINQtoSQLHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_1.vb)]</span></span>  
    <span data-ttu-id="afb63-142">[!code-vb[VbLINQtoSQLHowTos n °&2;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="afb63-142">[!code-vb[VbLINQtoSQLHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-call-a-stored-procedure-by-using-linq_2.vb)]</span></span>  
  
4.  <span data-ttu-id="afb63-143">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="afb63-143">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb63-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb63-144">See Also</span></span>  
 <span data-ttu-id="afb63-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="afb63-145">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="afb63-146"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="afb63-146"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="afb63-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="afb63-147"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="afb63-148"> [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span><span class="sxs-lookup"><span data-stu-id="afb63-148"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span></span>  
<span data-ttu-id="afb63-149"> [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span><span class="sxs-lookup"><span data-stu-id="afb63-149"> [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span></span>

