---
title: "Comment : exécuter une requête polymorphe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4c5ee1a815ed638bc8e775abbb1c0541aa70d746
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="a59e6-102">Comment : exécuter une requête polymorphe</span><span class="sxs-lookup"><span data-stu-id="a59e6-102">How to: Execute a Polymorphic Query</span></span>
<span data-ttu-id="a59e6-103">Cette rubrique montre comment exécuter un polymorphe [!INCLUDE[esql](../../../../../includes/esql-md.md)] de requête à l’aide de la [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) opérateur.</span><span class="sxs-lookup"><span data-stu-id="a59e6-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="a59e6-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="a59e6-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="a59e6-105">Ajouter le [modèle School](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) à votre projet et configurer votre projet pour utiliser Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a59e6-105">Add the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="a59e6-106">Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="a59e6-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="a59e6-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="a59e6-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="a59e6-108">Modifier le modèle conceptuel pour avoir un héritage table par-hierrachy en suivant les étapes dans [procédure pas à pas : mappage de l’héritage - Table par hiérarchie](http://msdn.microsoft.com/en-us/49b685cf-9db8-4d6d-b885-8837ed238f55).</span><span class="sxs-lookup"><span data-stu-id="a59e6-108">Modify the conceptual model to have a table-per-hierrachy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](http://msdn.microsoft.com/en-us/49b685cf-9db8-4d6d-b885-8837ed238f55).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a59e6-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a59e6-109">Example</span></span>  
 <span data-ttu-id="a59e6-110">L'exemple ci-dessous utilise un opérateur OFTYPE pour obtenir et afficher une collection d'`OnsiteCourses` uniquement, à partir d'une collection de `Courses`.</span><span class="sxs-lookup"><span data-stu-id="a59e6-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a><span data-ttu-id="a59e6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a59e6-111">See Also</span></span>  
 [<span data-ttu-id="a59e6-112">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a59e6-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 [<span data-ttu-id="a59e6-113">Langage Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a59e6-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
