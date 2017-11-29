---
title: "Constructeur de type nommé (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 72a19094beb03982448a102a4c7362a026d9e611
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="named-type-constructor-entity-sql"></a><span data-ttu-id="a070b-102">Constructeur de type nommé (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a070b-102">Named Type Constructor (Entity SQL)</span></span>
<span data-ttu-id="a070b-103">Permet de créer des instances des types nominaux de modèle conceptuel, tels que les types d'entités ou complexes.</span><span class="sxs-lookup"><span data-stu-id="a070b-103">Used to create instances of conceptual model nominal types such as Entity or Complex types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a070b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a070b-104">Syntax</span></span>  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="a070b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a070b-105">Arguments</span></span>  
 `identifier`  
 <span data-ttu-id="a070b-106">Valeur correspondant à un identificateur simple ou entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="a070b-106">Value that is a simple or quoted identifier.</span></span> <span data-ttu-id="a070b-107">Pour plus d’informations, consultez [identificateurs](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span><span class="sxs-lookup"><span data-stu-id="a070b-107">For more information see, [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)</span></span>  
  
 `expression`  
 <span data-ttu-id="a070b-108">Attributs du type supposés se trouver dans le même ordre d'apparition que dans la déclaration du type.</span><span class="sxs-lookup"><span data-stu-id="a070b-108">Attributes of the type that are assumed to be in the same order as they appear in the declaration of the type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a070b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a070b-109">Return Value</span></span>  
 <span data-ttu-id="a070b-110">Instances de types complexes et de types d'entités nommés.</span><span class="sxs-lookup"><span data-stu-id="a070b-110">Instances of named complex types and entity types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a070b-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="a070b-111">Remarks</span></span>  
 <span data-ttu-id="a070b-112">Les exemples suivants montrent comment construire des types nominaux et des types complexes :</span><span class="sxs-lookup"><span data-stu-id="a070b-112">The following examples show how to construct nominal and complex types:</span></span>  
  
 <span data-ttu-id="a070b-113">L'expression ci-dessous crée une instance de type `Person` :</span><span class="sxs-lookup"><span data-stu-id="a070b-113">The expression below creates an instance of a `Person` type:</span></span>  
  
 `Person("abc", 12)`  
  
 <span data-ttu-id="a070b-114">L'expression ci-dessous crée une instance d'un type complexe :</span><span class="sxs-lookup"><span data-stu-id="a070b-114">The expression below creates an instance of a complex type:</span></span>  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 <span data-ttu-id="a070b-115">L'expression ci-dessous crée une instance d'un type complexe imbriqué :</span><span class="sxs-lookup"><span data-stu-id="a070b-115">The expression below creates an instance of a nested complex type:</span></span>  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 <span data-ttu-id="a070b-116">L'expression ci-dessous crée une instance d'une entité avec un type complexe imbriqué :</span><span class="sxs-lookup"><span data-stu-id="a070b-116">The expression below creates an instance of an entity with a nested complex type:</span></span>  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 <span data-ttu-id="a070b-117">L'exemple suivant montre comment initialiser une propriété d'un type complexe en valeur null :`MyModel.ZipCode(‘98118’, null)`</span><span class="sxs-lookup"><span data-stu-id="a070b-117">The following example shows how to initialize a property of a complex type to null:`MyModel.ZipCode(‘98118’, null)`</span></span>  
  
## <a name="example"></a><span data-ttu-id="a070b-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="a070b-118">Example</span></span>  
 <span data-ttu-id="a070b-119">La requête Entity SQL ci-dessous utilise le constructeur de type nommé pour créer une instance d'un type de modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="a070b-119">The following Entity SQL query uses the named type constructor to create an instance of a conceptual model type.</span></span> <span data-ttu-id="a070b-120">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="a070b-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a070b-121">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a070b-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a070b-122">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a070b-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a070b-123">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="a070b-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a><span data-ttu-id="a070b-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a070b-124">See Also</span></span>  
 [<span data-ttu-id="a070b-125">Construction de Types</span><span class="sxs-lookup"><span data-stu-id="a070b-125">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="a070b-126">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a070b-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
