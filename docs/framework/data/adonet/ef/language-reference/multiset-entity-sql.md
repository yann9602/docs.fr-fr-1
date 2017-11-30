---
title: MULTISET (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e72605225d214ccd2283aaae3f0c2071ceb92d91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="9f874-102">MULTISET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9f874-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="9f874-103">Crée une instance d'un multiensemble à partir d'une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9f874-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="9f874-104">Toutes les valeurs du constructeur MULTISET doivent être d'un type `T`compatible.</span><span class="sxs-lookup"><span data-stu-id="9f874-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="9f874-105">Les constructeurs de multiensemble vides ne sont pas autorisés.</span><span class="sxs-lookup"><span data-stu-id="9f874-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f874-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f874-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f874-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f874-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9f874-108">Toute liste de valeurs valide.</span><span class="sxs-lookup"><span data-stu-id="9f874-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f874-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9f874-109">Return Value</span></span>  
 <span data-ttu-id="9f874-110">Une collection de type MULTISET\<T >.</span><span class="sxs-lookup"><span data-stu-id="9f874-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f874-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f874-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="9f874-112"> propose trois types de constructeurs : constructeurs de ligne, constructeurs d'objets et constructeurs de multiensemble (ou de collection).</span><span class="sxs-lookup"><span data-stu-id="9f874-112"> provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="9f874-113">Pour plus d’informations, consultez [construction de Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9f874-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="9f874-114">Le constructeur de multiensemble crée une instance d'un multiensemble à partir d'une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9f874-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="9f874-115">Toutes les valeurs du constructeur doivent être d'un type compatible.</span><span class="sxs-lookup"><span data-stu-id="9f874-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="9f874-116">Par exemple, l'expression suivante crée un multiensemble d'entiers.</span><span class="sxs-lookup"><span data-stu-id="9f874-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="9f874-117">Les littéraux de multiensemble imbriqués ne sont pris en charge que lorsqu'un multiensemble d'encapsulation a un seul élément de multiensemble ; par exemple, `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="9f874-117">Nested multiset literals are only supported when a wrapping mutiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="9f874-118">Lorsqu'un multiensemble d'encapsulation a plusieurs éléments de multiensemble (par exemple, `{{1, 2}, {3, 4}}`), ils ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9f874-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f874-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9f874-119">Example</span></span>  
 <span data-ttu-id="9f874-120">La requête Entity SQL suivante utilise l'opérateur MULTISET pour créer une instance d'un multiensemble à partir d'une liste de valeurs.</span><span class="sxs-lookup"><span data-stu-id="9f874-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="9f874-121">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="9f874-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9f874-122">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9f874-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9f874-123">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="9f874-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="9f874-124">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="9f874-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="9f874-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f874-125">See Also</span></span>  
 [<span data-ttu-id="9f874-126">Construction de Types</span><span class="sxs-lookup"><span data-stu-id="9f874-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="9f874-127">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9f874-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
