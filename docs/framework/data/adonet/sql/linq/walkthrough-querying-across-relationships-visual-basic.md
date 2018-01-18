---
title: "Procédure pas à pas : interrogation de relations (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fef9880d5f9fa652eab2eb0d17bbf782dc64773d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="aba70-102">Procédure pas à pas : interrogation de relations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aba70-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="aba70-103">Cette procédure pas à pas illustre l’utilisation de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* pour représenter les relations de clé étrangère dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="aba70-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="aba70-104">Cette procédure pas à pas a été écrite à l'aide des paramètres de développement Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aba70-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="aba70-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="aba70-105">Prerequisites</span></span>  
 <span data-ttu-id="aba70-106">Vous devez avoir terminé [procédure pas à pas : modèle d’objet Simple et de requête (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="aba70-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="aba70-107">Cette procédure pas à pas est basée sur cette dernière, y compris la présence du fichier northwnd.mdf dans c:\linqtest.</span><span class="sxs-lookup"><span data-stu-id="aba70-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="aba70-108">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="aba70-108">Overview</span></span>  
 <span data-ttu-id="aba70-109">Cette procédure pas à pas se compose de trois tâches principales :</span><span class="sxs-lookup"><span data-stu-id="aba70-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="aba70-110">Ajout d'une classe d'entité pour représenter la table Orders dans l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="aba70-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="aba70-111">Ajout d'annotations à la classe `Customer` pour améliorer la relation entre les classes `Customer` et `Order`.</span><span class="sxs-lookup"><span data-stu-id="aba70-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="aba70-112">Création et exécution d'une requête pour essayer d'obtenir des informations `Order` en utilisant la classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="aba70-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="aba70-113">Mappage de relations entre des tables</span><span class="sxs-lookup"><span data-stu-id="aba70-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="aba70-114">Une fois la définition de classe `Customer` terminée, créez la définition de classe d'entité `Order` qui inclut le code suivant indiquant que `Orders.Customer` est une clé étrangère de `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="aba70-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="aba70-115">Pour ajouter la classe d'entité Order</span><span class="sxs-lookup"><span data-stu-id="aba70-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="aba70-116">Tapez ou collez le code suivant après la classe `Customer` :</span><span class="sxs-lookup"><span data-stu-id="aba70-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="aba70-117">Annotation de la classe Customer</span><span class="sxs-lookup"><span data-stu-id="aba70-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="aba70-118">Dans cette étape, annotez la classe `Customer` pour indiquer sa relation avec la classe `Order`.</span><span class="sxs-lookup"><span data-stu-id="aba70-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="aba70-119">Cet ajout n'est pas strictement nécessaire étant donné que la définition de la relation dans chacune des directions est suffisante pour créer le lien.</span><span class="sxs-lookup"><span data-stu-id="aba70-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="aba70-120">Cependant, l'ajout de cette annotation vous permet de naviguer facilement parmi les objets dans chacune des directions.</span><span class="sxs-lookup"><span data-stu-id="aba70-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="aba70-121">Pour annoter la classe Customer</span><span class="sxs-lookup"><span data-stu-id="aba70-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="aba70-122">Tapez ou collez le code suivant dans la classe `Customer` :</span><span class="sxs-lookup"><span data-stu-id="aba70-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="aba70-123">Création et exécution d'une requête dans la relation entre les classes Order et Customer</span><span class="sxs-lookup"><span data-stu-id="aba70-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="aba70-124">Vous pouvez désormais accéder aux objets `Order` directement à partir des objets `Customer` ou inversement.</span><span class="sxs-lookup"><span data-stu-id="aba70-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="aba70-125">Vous n’avez pas besoin explicite *jointure* entre customers et orders.</span><span class="sxs-lookup"><span data-stu-id="aba70-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="aba70-126">Pour accéder aux objets Order à l'aide d'objets Customer</span><span class="sxs-lookup"><span data-stu-id="aba70-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="aba70-127">Modifiez la méthode `Sub Main` en tapant ou en collant le code suivant dans la méthode :</span><span class="sxs-lookup"><span data-stu-id="aba70-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="aba70-128">Appuyez sur F5 pour déboguer l'application.</span><span class="sxs-lookup"><span data-stu-id="aba70-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="aba70-129">Deux noms apparaissent dans le message et la fenêtre de console affiche le code SQL généré.</span><span class="sxs-lookup"><span data-stu-id="aba70-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="aba70-130">Fermez le message pour arrêter le débogage.</span><span class="sxs-lookup"><span data-stu-id="aba70-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="aba70-131">Création d'une vue fortement typée de votre base de données</span><span class="sxs-lookup"><span data-stu-id="aba70-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="aba70-132">Il est beaucoup plus facile de démarrer avec une vue fortement typée de votre base de données.</span><span class="sxs-lookup"><span data-stu-id="aba70-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="aba70-133">En effectuant un typage fort de l'objet <xref:System.Data.Linq.DataContext>, vous n'avez pas besoin d'effectuer des appels à <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="aba70-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="aba70-134">Vous pouvez utiliser des tables fortement typées dans toutes vos requêtes lorsque vous utilisez l'objet <xref:System.Data.Linq.DataContext> fortement typé.</span><span class="sxs-lookup"><span data-stu-id="aba70-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="aba70-135">Dans les étapes suivantes, vous créerez `Customers` comme table fortement typée qui mappe à la table Customers dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="aba70-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="aba70-136">Pour effectuer un typage fort de l'objet DataContext</span><span class="sxs-lookup"><span data-stu-id="aba70-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="aba70-137">Ajoutez le code suivant au-dessus de la déclaration de classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="aba70-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="aba70-138">Modifiez `Sub Main` pour utiliser le <xref:System.Data.Linq.DataContext> fortement typé comme suit :</span><span class="sxs-lookup"><span data-stu-id="aba70-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="aba70-139">Appuyez sur F5 pour déboguer l'application.</span><span class="sxs-lookup"><span data-stu-id="aba70-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="aba70-140">La sortie de la fenêtre de console est :</span><span class="sxs-lookup"><span data-stu-id="aba70-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="aba70-141">Appuyez sur Entrée dans la fenêtre de console pour fermer l'application.</span><span class="sxs-lookup"><span data-stu-id="aba70-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="aba70-142">Sur le **fichier** menu, cliquez sur **Enregistrer tout** si vous souhaitez enregistrer cette application.</span><span class="sxs-lookup"><span data-stu-id="aba70-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="aba70-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aba70-143">Next Steps</span></span>  
 <span data-ttu-id="aba70-144">La procédure pas à pas suivante ([procédure pas à pas : manipulation de données (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) montre comment manipuler les données.</span><span class="sxs-lookup"><span data-stu-id="aba70-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="aba70-145">Cette procédure pas à pas ne requiert pas d'enregistrer les deux procédures pas à pas de cette série que vous avez déjà terminées.</span><span class="sxs-lookup"><span data-stu-id="aba70-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba70-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aba70-146">See Also</span></span>  
 [<span data-ttu-id="aba70-147">Apprentissage par les procédures pas à pas</span><span class="sxs-lookup"><span data-stu-id="aba70-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
