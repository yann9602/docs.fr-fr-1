---
title: "Différences entre Entity SQL et Transact-SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c9ee36d-f294-4c8b-a196-f0114c94f559
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 90c3b7d639ea6fafd570b44ee40c0567e264ea91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-entity-sql-differs-from-transact-sql"></a><span data-ttu-id="cf7c4-102">Différences entre Entity SQL et Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="cf7c4-102">How Entity SQL Differs from Transact-SQL</span></span>
<span data-ttu-id="cf7c4-103">Cette rubrique décrit les différences entre [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf7c4-103">This topic describes the differences between [!INCLUDE[esql](../../../../../../includes/esql-md.md)] and [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span>  
  
## <a name="inheritance-and-relationships-support"></a><span data-ttu-id="cf7c4-104">Héritage et prise en charge des relations</span><span class="sxs-lookup"><span data-stu-id="cf7c4-104">Inheritance and Relationships Support</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-105">fonctionne directement avec les schémas d’entité conceptuels et prend en charge des fonctionnalités telles que l’héritage et les relations de modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-105"> works directly with conceptual entity schemas and supports conceptual model features such as inheritance and relationships.</span></span>  
  
 <span data-ttu-id="cf7c4-106">Lors de l’utilisation de l’héritage, il est souvent utile de sélectionner des instances d’un sous-type à partir d’une collection d’instances de supertype.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-106">When working with inheritance, it is often useful to select instances of a subtype from a collection of supertype instances.</span></span> <span data-ttu-id="cf7c4-107">Le [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) opérateur dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (semblable à `oftype` dans les séquences c#) fournit cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-107">The [oftype](../../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (similar to `oftype` in C# Sequences) provides this capability.</span></span>  
  
## <a name="support-for-collections"></a><span data-ttu-id="cf7c4-108">Prise en charge des collections</span><span class="sxs-lookup"><span data-stu-id="cf7c4-108">Support for Collections</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-109">traite les collections en tant qu’entités de première classe.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-109"> treats collections as first-class entities.</span></span> <span data-ttu-id="cf7c4-110">Exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-110">For example:</span></span>  
  
-   <span data-ttu-id="cf7c4-111">Les expressions de collection sont valides dans une clause `from`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-111">Collection expressions are valid in a `from` clause.</span></span>  
  
-   <span data-ttu-id="cf7c4-112">Les sous-requêtes `in` et `exists` ont été généralisées pour autoriser toute collection.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-112">`in` and `exists` subqueries have been generalized to allow any collections.</span></span>  
  
     <span data-ttu-id="cf7c4-113">Une sous-requête est un type de collection.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-113">A subquery is one kind of collection.</span></span> <span data-ttu-id="cf7c4-114">`e1 in e2` et `exists(e)` sont les constructions [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui permettent d'effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-114">`e1 in e2` and `exists(e)` are the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs to perform these operations.</span></span>  
  
-   <span data-ttu-id="cf7c4-115">Les opérations de définition, telles que `union`, `intersect` et `except`, s'appliquent à présent aux collections.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-115">Set operations, such as `union`, `intersect`, and `except`, now operate on collections.</span></span>  
  
-   <span data-ttu-id="cf7c4-116">Les jointures s'appliquent aux collections.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-116">Joins operate on collections.</span></span>  
  
## <a name="support-for-expressions"></a><span data-ttu-id="cf7c4-117">Prise en charge des expressions</span><span class="sxs-lookup"><span data-stu-id="cf7c4-117">Support for Expressions</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="cf7c4-118">a des sous-requêtes (tables) et des expressions (lignes et colonnes).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-118"> has subqueries (tables) and expressions (rows and columns).</span></span>  
  
 <span data-ttu-id="cf7c4-119">Pour prendre en charge les collections et les collections imbriquées, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforme tout en expression.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-119">To support collections and nested collections, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] makes everything an expression.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-120"> est plus composable que [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] – chaque expression peut être utilisée n'importe où.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-120"> is more composable than [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]—every expression can be used anywhere.</span></span> <span data-ttu-id="cf7c4-121">Les expressions de requête génèrent toujours des collections des types projetés et peuvent être utilisées partout où une expression de collection est autorisée.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-121">Query expressions always result in collections of the projected types and can be used anywhere a collection expression is allowed.</span></span> <span data-ttu-id="cf7c4-122">Pour plus d’informations sur [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions qui ne sont pas pris en charge dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], consultez [non pris en charge les Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-122">For information about [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], see [Unsupported Expressions](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="cf7c4-123">Les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivantes sont toutes valides :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-123">The following are all valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries:</span></span>  
  
```  
1+2 *3  
"abc"  
row(1 as a, 2 as b)  
{ 1, 3, 5}   
e1 union all e2  
set(e1)  
```  
  
## <a name="uniform-treatment-of-subqueries"></a><span data-ttu-id="cf7c4-124">Traitement uniforme des sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="cf7c4-124">Uniform Treatment of Subqueries</span></span>  
 <span data-ttu-id="cf7c4-125">Vu l’accent porté sur les tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] effectue une interprétation contextuelle des sous-requêtes.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-125">Given its emphasis on tables, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] performs contextual interpretation of subqueries.</span></span> <span data-ttu-id="cf7c4-126">Par exemple, une sous-requête dans la `from` clause est considérée comme un multiset (table).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-126">For example, a subquery in the `from` clause is considered to be a multiset (table).</span></span> <span data-ttu-id="cf7c4-127">En revanche, la même sous-requête utilisée dans la clause `select` est considérée comme une sous-requête scalaire.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-127">But the same subquery used in the `select` clause is considered to be a scalar subquery.</span></span> <span data-ttu-id="cf7c4-128">De même, une sous-requête utilisée sur le côté gauche d’une `in` opérateur est considéré comme une sous-requête scalaire, tandis que le côté droit est supposé être une sous-requête de type multiset.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-128">Similarly, a subquery used on the left side of an `in` operator is considered to be a scalar subquery, while the right side is expected to be a multiset subquery.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-129"> élimine ces différences.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-129"> eliminates these differences.</span></span> <span data-ttu-id="cf7c4-130">Une expression a une interprétation uniforme qui ne dépend pas du contexte dans lequel elle est utilisée.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-130">An expression has a uniform interpretation that does not depend on the context in which it is used.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-131">considère que toutes les sous-requêtes comme des sous-requêtes de type multiset.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-131"> considers all subqueries to be multiset subqueries.</span></span> <span data-ttu-id="cf7c4-132">Si une valeur scalaire est souhaitée à partir de la sous-requête, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit le `anyelement` opérateur qui opère sur une collection (dans ce cas, la sous-requête) et extrait une valeur singleton de la collection.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-132">If a scalar value is desired from the subquery, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides the `anyelement` operator that operates on a collection (in this case, the subquery), and extracts a singleton value from the collection.</span></span>  
  
### <a name="avoiding-implicit-coercions-for-subqueries"></a><span data-ttu-id="cf7c4-133">Éviter des contraintes implicites pour les sous-requêtes</span><span class="sxs-lookup"><span data-stu-id="cf7c4-133">Avoiding Implicit Coercions for Subqueries</span></span>  
 <span data-ttu-id="cf7c4-134">Un effet secondaire connexe du traitement uniforme des sous-requêtes est la conversion implicite des sous-requêtes en valeurs scalaires.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-134">A related side effect of uniform treatment of subqueries is implicit conversion of subqueries to scalar values.</span></span> <span data-ttu-id="cf7c4-135">En particulier, dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], un multiset de lignes (avec un champ unique) est converti implicitement en une valeur scalaire dont le type de données est celui du champ.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-135">Specifically, in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], a multiset of rows (with a single field) is implicitly converted into a scalar value whose data type is that of the field.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-136"> ne prend pas en charge cette contrainte implicite.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-136"> does not support this implicit coercion.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-137"> fournit l'opérateur ANYELEMENT pour extraire une valeur singleton d'une collection et une clause `select value` pour éviter de créer un wrapper de ligne pendant une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-137"> provides the ANYELEMENT operator to extract a singleton value from a collection, and a `select value` clause to avoid creating a row-wrapper during a query expression.</span></span>  
  
## <a name="select-value-avoiding-the-implicit-row-wrapper"></a><span data-ttu-id="cf7c4-138">Select Value : éviter le wrapper de ligne implicite</span><span class="sxs-lookup"><span data-stu-id="cf7c4-138">Select Value: Avoiding the Implicit Row Wrapper</span></span>  
 <span data-ttu-id="cf7c4-139">La clause select dans une [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] sous-requête crée implicitement un wrapper de ligne autour des éléments dans la clause.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-139">The select clause in a [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] subquery implicitly creates a row wrapper around the items in the clause.</span></span> <span data-ttu-id="cf7c4-140">Cela implique que nous ne pouvons pas créer de collections de scalaires ou d’objets.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-140">This implies that we cannot create collections of scalars or objects.</span></span> [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="cf7c4-141">autorise une contrainte implicite entre un rowtype avec un champ et une valeur singleton du même type de données.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-141"> allows an implicit coercion between a rowtype with one field, and a singleton value of the same data type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-142"> fournit la clause `select value` pour ignorer la construction de ligne implicite.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-142"> provides the `select value` clause to skip the implicit row construction.</span></span> <span data-ttu-id="cf7c4-143">Un seul élément peut être spécifié dans une clause `select value`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-143">Only one item may be specified in a `select value` clause.</span></span> <span data-ttu-id="cf7c4-144">Lorsqu'une telle clause est utilisée, aucun wrapper de ligne n'est construit autour des éléments de la clause `select` et une collection de la forme souhaitée peut être générée, par exemple : `select value a`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-144">When such a clause is used, no row wrapper is constructed around the items in the `select` clause, and a collection of the desired shape may be produced, for example: `select value a`.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-145"> fournit également le constructeur de ligne pour construire des lignes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-145"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="cf7c4-146">`select` accepte un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, comme suit :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-146">`select` takes one or more elements in the projection and results in a data record with fields, as follows:</span></span>  
  
 `select a, b, c`  
  
## <a name="left-correlation-and-aliasing"></a><span data-ttu-id="cf7c4-147">Corrélation gauche et utilisation d'alias</span><span class="sxs-lookup"><span data-stu-id="cf7c4-147">Left Correlation and Aliasing</span></span>  
 <span data-ttu-id="cf7c4-148">Dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], les expressions comprises dans une étendue donnée (une clause unique comme `select` ou `from`) ne peuvent pas référencer des expressions définies précédemment dans la même étendue.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-148">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], expressions in a given scope (a single clause like `select` or `from`) cannot reference expressions defined earlier in the same scope.</span></span> <span data-ttu-id="cf7c4-149">Certains dialectes SQL (y compris [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) prennent en charge des formes limitées de ces éléments dans la clause `from`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-149">Some dialects of SQL (including [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]) do support limited forms of these in the `from` clause.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-150">généralise les corrélations gauches dans la `from` clause et les traite uniformément.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-150"> generalizes left correlations in the `from` clause, and treats them uniformly.</span></span> <span data-ttu-id="cf7c4-151">Les expressions dans la clause `from` peuvent référencer des définitions antérieures (définitions à gauche) dans la même clause sans nécessiter une syntaxe supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-151">Expressions in the `from` clause can reference earlier definitions (definitions to the left) in the same clause without the need for additional syntax.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-152"> impose également des restrictions supplémentaires sur les requêtes qui impliquent des clauses `group by`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-152"> also imposes additional restrictions on queries involving `group by` clauses.</span></span> <span data-ttu-id="cf7c4-153">Expressions dans les `select` clause et `having` clause de telles requêtes peut-être faire référence uniquement à la `group by` clés via leurs alias.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-153">Expressions in the `select` clause and `having` clause of such queries may only refer to the `group by` keys via their aliases.</span></span> <span data-ttu-id="cf7c4-154">La construction suivante est valide dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] mais ne sont pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="cf7c4-154">The following construct is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but are not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select t.x + t.y from T as t group by t.x + t.y  
```  
  
 <span data-ttu-id="cf7c4-155">Pour effectuer cette opération dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-155">To do this in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]:</span></span>  
  
```  
select k from T as t group by (t.x + t.y) as k  
```  
  
## <a name="referencing-columns-properties-of-tables-collections"></a><span data-ttu-id="cf7c4-156">Référencement de colonnes (propriétés) de tables (collections)</span><span class="sxs-lookup"><span data-stu-id="cf7c4-156">Referencing Columns (Properties) of Tables (Collections)</span></span>  
 <span data-ttu-id="cf7c4-157">Toutes les références de colonne dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] doivent être qualifiées avec l'alias de la table.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-157">All column references in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] must be qualified with the table alias.</span></span> <span data-ttu-id="cf7c4-158">La construction suivante (en supposant que `a` est une colonne valide de la table `T`) est valide dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] , mais pas dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf7c4-158">The following construct (assuming that `a` is a valid column of table `T`) is valid in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] but not in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
```  
select a from T  
```  
  
 <span data-ttu-id="cf7c4-159">La forme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-159">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] form is</span></span>  
  
```  
select t.a as A from T as t  
```  
  
 <span data-ttu-id="cf7c4-160">Les alias de la table sont facultatifs dans la clause `from`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-160">The table aliases are optional in the `from` clause.</span></span> <span data-ttu-id="cf7c4-161">Le nom de la table est utilisé comme alias implicite.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-161">The name of the table is used as the implicit alias.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-162"> autorise également la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-162"> allows the following form as well:</span></span>  
  
```  
select Tab.a from Tab  
```  
  
## <a name="navigation-through-objects"></a><span data-ttu-id="cf7c4-163">Navigation dans les objets</span><span class="sxs-lookup"><span data-stu-id="cf7c4-163">Navigation Through Objects</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="cf7c4-164"> utilise la notation "." pour référencer les colonnes d'(une ligne d')une table.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-164"> uses the "." notation for referencing columns of (a row of) a table.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-165"> étend cette notation (empruntée des langages de programmation) pour prendre en charge la navigation dans les propriétés d'un objet.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-165"> extends this notation (borrowed from programming languages) to support navigation through properties of an object.</span></span>  
  
 <span data-ttu-id="cf7c4-166">Par exemple, si `p` est une expression de type Person, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous référence la ville de l'adresse de cette personne.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-166">For example, if `p` is an expression of type Person, the following is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax for referencing the city of the address of this person.</span></span>  
  
```  
p.Address.City   
```  
  
## <a name="no-support-for-"></a><span data-ttu-id="cf7c4-167">Aucune prise en charge pour *</span><span class="sxs-lookup"><span data-stu-id="cf7c4-167">No Support for *</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="cf7c4-168">prend en charge la non qualifiée * syntaxe comme alias pour la ligne entière et le texte complet \* syntaxe (t.\*) comme raccourci pour les champs de la table.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-168"> supports the unqualified * syntax as an alias for the entire row, and the qualified \* syntax (t.\*) as a shortcut for the fields of that table.</span></span> <span data-ttu-id="cf7c4-169">En outre, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] permettant à un compte spécial (\*) agrégat, qui inclut les valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-169">In addition, [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] allows for a special count(\*) aggregate, which includes nulls.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-170"> ne prend pas en charge la construction *.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-170"> does not support the * construct.</span></span> <span data-ttu-id="cf7c4-171">Les requêtes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] de la forme `select * from T` et `select T1.* from T1, T2...` peuvent être exprimées dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sous la forme `select value t from T as t` et `select value t1 from T1 as t1, T2 as t2...`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-171">[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] queries of the form `select * from T` and `select T1.* from T1, T2...` can be expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as `select value t from T as t` and `select value t1 from T1 as t1, T2 as t2...`, respectively.</span></span> <span data-ttu-id="cf7c4-172">En outre, ces constructions gèrent l'héritage (capacité des valeurs à être substituées), tandis que les variantes `select *` sont restreintes aux propriétés de niveau supérieur du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-172">Additionally, these constructs handle inheritance (value substitutability), while the `select *` variants are restricted to top-level properties of the declared type.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-173"> ne prend pas en charge l'agrégat `count(*)`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-173"> does not support the `count(*)` aggregate.</span></span> <span data-ttu-id="cf7c4-174">Utilisez plutôt `count(0)`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-174">Use `count(0)` instead.</span></span>  
  
## <a name="changes-to-group-by"></a><span data-ttu-id="cf7c4-175">Modifications apportées à Group By</span><span class="sxs-lookup"><span data-stu-id="cf7c4-175">Changes to Group By</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-176"> prend en charge les alias des clés `group by`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-176"> supports aliasing of `group by` keys.</span></span> <span data-ttu-id="cf7c4-177">Les expressions dans la clause `select` et la clause `having` doivent faire référence aux clés `group by` par le biais de ces alias.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-177">Expressions in the `select` clause and `having` clause must refer to the `group by` keys via these aliases.</span></span> <span data-ttu-id="cf7c4-178">Par exemple, la syntaxe [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-178">For example, this [!INCLUDE[esql](../../../../../../includes/esql-md.md)] syntax:</span></span>  
  
```  
select k1, count(t.a), sum(t.a)  
from T as t  
group by t.b + t.c as k1  
```  
  
 <span data-ttu-id="cf7c4-179">...est équivalente à la syntaxe [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] suivante :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-179">...is equivalent to the following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]:</span></span>  
  
```  
select b + c, count(*), sum(a)   
from T  
group by b + c  
```  
  
## <a name="collection-based-aggregates"></a><span data-ttu-id="cf7c4-180">Agrégats basés sur des collections</span><span class="sxs-lookup"><span data-stu-id="cf7c4-180">Collection-Based Aggregates</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-181"> prend en charge deux types d'agrégats.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-181"> supports two kinds of aggregates.</span></span>  
  
 <span data-ttu-id="cf7c4-182">Les agrégats basés sur des collections opèrent sur des collections et produisent le résultat agrégé.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-182">Collection-based aggregates operate on collections and produce the aggregated result.</span></span> <span data-ttu-id="cf7c4-183">Ils peuvent apparaître n'importe où dans la requête et ne requièrent pas de clause `group by`.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-183">These can appear anywhere in the query, and do not require a `group by` clause.</span></span> <span data-ttu-id="cf7c4-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-184">For example:</span></span>  
  
```  
select t.a as a, count({1,2,3}) as b from T as t     
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-185"> prend également en charge les agrégats de style SQL.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-185"> also supports SQL-style aggregates.</span></span> <span data-ttu-id="cf7c4-186">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-186">For example:</span></span>  
  
```  
select a, sum(t.b) from T as t group by t.a as a  
```  
  
## <a name="order-by-clause-usage"></a><span data-ttu-id="cf7c4-187">Utilisation des clauses ORDER BY</span><span class="sxs-lookup"><span data-stu-id="cf7c4-187">ORDER BY Clause Usage</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="cf7c4-188"> permet de spécifier des clauses ORDER BY uniquement dans le bloc SELECT ..</span><span class="sxs-lookup"><span data-stu-id="cf7c4-188"> allows ORDER BY clauses to be specified only in the topmost SELECT ..</span></span> <span data-ttu-id="cf7c4-189">FROM .</span><span class="sxs-lookup"><span data-stu-id="cf7c4-189">FROM ..</span></span> <span data-ttu-id="cf7c4-190">WHERE le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-190">WHERE block.</span></span> <span data-ttu-id="cf7c4-191">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], vous pouvez utiliser une expression ORDER BY imbriquée et elle peut être placée n'importe où dans la requête, mais le classement dans une requête imbriquée n'est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-191">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)] you can use a nested ORDER BY expression and it can be placed anywhere in the query, but ordering in a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="identifiers"></a><span data-ttu-id="cf7c4-192">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="cf7c4-192">Identifiers</span></span>  
 <span data-ttu-id="cf7c4-193">Dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], la comparaison d'identificateurs est basée sur le classement de la base de données actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-193">In [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], identifier comparison is based on the collation of the current database.</span></span> <span data-ttu-id="cf7c4-194">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les identificateurs respectent toujours la casse et les accents (autrement dit, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distingue les caractères accentués et non accentués ; par exemple, « a » n'est pas égal à « à »).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-194">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], identifiers are always case insensitive and accent sensitive (that is, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] distinguishes between accented and unaccented characters; for example, 'a' is not equal to 'ấ').</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-195"> traite les versions des lettres qui apparaissent identiques mais qui proviennent de pages de codes différentes comme des caractères différents.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-195"> treats versions of letters that appear the same but are from different code pages as different characters.</span></span> <span data-ttu-id="cf7c4-196">Pour plus d’informations, consultez [du jeu de caractères entrée](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-196">For more information, see [Input Character Set](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md).</span></span>  
  
## <a name="transact-sql-functionality-not-available-in-entity-sql"></a><span data-ttu-id="cf7c4-197">Fonctionnalités Transact-SQL non disponibles dans Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cf7c4-197">Transact-SQL Functionality Not Available in Entity SQL</span></span>  
 <span data-ttu-id="cf7c4-198">Les fonctionnalités [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ci-dessous ne sont pas disponibles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf7c4-198">The following [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] functionality is not available in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
 <span data-ttu-id="cf7c4-199">DML</span><span class="sxs-lookup"><span data-stu-id="cf7c4-199">DML</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-200">ne fournit actuellement aucune prise en charge pour les instructions DML (insert, update, supprimer).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-200"> currently provides no support for DML statements (insert, update, delete).</span></span>  
  
 <span data-ttu-id="cf7c4-201">DDL</span><span class="sxs-lookup"><span data-stu-id="cf7c4-201">DDL</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-202"> ne fournit aucune prise en charge pour DDL dans la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-202"> provides no support for DDL in the current version.</span></span>  
  
 <span data-ttu-id="cf7c4-203">Programmation impérative</span><span class="sxs-lookup"><span data-stu-id="cf7c4-203">Imperative Programming</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-204"> ne fournit aucune prise en charge pour la programmation impérative, contrairement à [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf7c4-204"> provides no support for imperative programming, unlike [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cf7c4-205">Utilisez un langage de programmation à la place.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-205">Use a programming language instead.</span></span>  
  
 <span data-ttu-id="cf7c4-206">Fonctions de regroupement</span><span class="sxs-lookup"><span data-stu-id="cf7c4-206">Grouping Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-207"> ne fournit pas encore de prise en charge pour les fonctions de regroupement (par exemple, CUBE, ROLLUP et GROUPING_SET).</span><span class="sxs-lookup"><span data-stu-id="cf7c4-207"> does not yet provide support for grouping functions (for example, CUBE, ROLLUP, and GROUPING_SET).</span></span>  
  
 <span data-ttu-id="cf7c4-208">Fonctions analytiques</span><span class="sxs-lookup"><span data-stu-id="cf7c4-208">Analytic Functions</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-209"> ne fournit pas (encore) de prise en charge pour les fonctions analytiques.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-209"> does not (yet) provide support for analytic functions.</span></span>  
  
 <span data-ttu-id="cf7c4-210">Fonctions et opérateurs intégrés</span><span class="sxs-lookup"><span data-stu-id="cf7c4-210">Built-in Functions, Operators</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-211">prend en charge un sous-ensemble de [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]intégrés dans les fonctions et opérateurs.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-211"> supports a subset of [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]'s built in functions and operators.</span></span> <span data-ttu-id="cf7c4-212">Ces opérateurs et ces fonctions seront vraisemblablement pris en charge par les principaux fournisseurs de stockage.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-212">These operators and functions are likely to be supported by the major store providers.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-213">utilise les fonctions spécifiques aux magasins déclarées dans le manifeste du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-213"> uses the store-specific functions declared in a provider manifest.</span></span> <span data-ttu-id="cf7c4-214">En outre, le [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] vous permet de déclarer intégrées et définies par l’utilisateur existante fonctions de magasin [!INCLUDE[esql](../../../../../../includes/esql-md.md)] à utiliser.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-214">Additionally, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] allows you to declare built-in and user-defined existing store functions, for [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to use.</span></span>  
  
 <span data-ttu-id="cf7c4-215">Indicateurs</span><span class="sxs-lookup"><span data-stu-id="cf7c4-215">Hints</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-216"> ne fournit pas de mécanismes pour les indicateurs de requête.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-216"> does not provide mechanisms for query hints.</span></span>  
  
 <span data-ttu-id="cf7c4-217">Résultats d'une requête de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="cf7c4-217">Batching Query Results</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-218"> ne prend pas en charge les résultats d'une requête de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-218"> does not support batching query results.</span></span> <span data-ttu-id="cf7c4-219">Par exemple, ce qui suit est valide [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (envoi en tant que lot) :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-219">For example, the following is valid [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] (sending as a batch):</span></span>  
  
```  
select * from products;  
select * from catagories;  
```  
  
 <span data-ttu-id="cf7c4-220">Toutefois, l'équivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n'est pas pris en charge :</span><span class="sxs-lookup"><span data-stu-id="cf7c4-220">However, the equivalent [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not supported:</span></span>  
  
```  
Select value p from Products as p;  
Select value c from Categories as c;  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cf7c4-221"> prend uniquement en charge une seule instruction de requête générant un résultat par commande.</span><span class="sxs-lookup"><span data-stu-id="cf7c4-221"> only supports one result-producing query statement per command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7c4-222">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf7c4-222">See Also</span></span>  
 [<span data-ttu-id="cf7c4-223">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cf7c4-223">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="cf7c4-224">Expressions non prises en charge</span><span class="sxs-lookup"><span data-stu-id="cf7c4-224">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)
