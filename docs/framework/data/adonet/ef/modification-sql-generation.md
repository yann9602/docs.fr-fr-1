---
title: "Génération SQL de modification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6696d80246d61cc2eac47266837d79661141b9b0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="modification-sql-generation"></a><span data-ttu-id="c005e-102">Génération SQL de modification</span><span class="sxs-lookup"><span data-stu-id="c005e-102">Modification SQL Generation</span></span>
<span data-ttu-id="c005e-103">Cette section décrit la manière de développer un module de génération SQL de modification pour votre fournisseur (base de données conforme SQL:1999).</span><span class="sxs-lookup"><span data-stu-id="c005e-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="c005e-104">Ce module doit traduire une arborescence de commandes de modification en instructions SQL INSERT, UPDATE ou DELETE appropriées.</span><span class="sxs-lookup"><span data-stu-id="c005e-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>  
  
 <span data-ttu-id="c005e-105">Pour plus d’informations sur la génération SQL pour les instructions select, consultez [génération SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span><span class="sxs-lookup"><span data-stu-id="c005e-105">For information about SQL generation for select statements, see [SQL Generation](../../../../../docs/framework/data/adonet/ef/sql-generation.md).</span></span>  
  
## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="c005e-106">Vue d’ensemble des arborescences de commandes de modification</span><span class="sxs-lookup"><span data-stu-id="c005e-106">Overview of Modification Command Trees</span></span>  
 <span data-ttu-id="c005e-107">Le module de génération SQL de modification génère des instructions SQL de modification spécifiques à la base de données selon un DbModificationCommandTree d'entrée donné.</span><span class="sxs-lookup"><span data-stu-id="c005e-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="c005e-108">Un DbModificationCommandTree est une représentation du modèle objet d'une opération DML de modification (opération INSERT, UPDATE ou DELETE), en héritant de DbCommandTree.</span><span class="sxs-lookup"><span data-stu-id="c005e-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="c005e-109">Il existe trois implémentations de DbModificationCommandTree :</span><span class="sxs-lookup"><span data-stu-id="c005e-109">There are three implementations of DbModificationCommandTree:</span></span>  
  
-   <span data-ttu-id="c005e-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-110">DbInsertCommandTree</span></span>  
  
-   <span data-ttu-id="c005e-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-111">DbUpdateCommandTree</span></span>  
  
-   <span data-ttu-id="c005e-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-112">DbDeleteCommandTree</span></span>  
  
 <span data-ttu-id="c005e-113">DbModificationCommandTree et ses implémentations produites par le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] représentent toujours une opération de ligne unique.</span><span class="sxs-lookup"><span data-stu-id="c005e-113">DbModificationCommandTree and its implementations that are produced by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] always represent a single row operation.</span></span> <span data-ttu-id="c005e-114">Cette section décrit ces types avec leurs contraintes dans .NET Framework version 3.5.</span><span class="sxs-lookup"><span data-stu-id="c005e-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>  
  
 <span data-ttu-id="c005e-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="c005e-115">![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>  
  
 <span data-ttu-id="c005e-116">DbModificationCommandTree a une propriété Target qui représente le jeu de cibles pour l'opération de modification.</span><span class="sxs-lookup"><span data-stu-id="c005e-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="c005e-117">La propriété d'expression de la cible, qui définit le jeu de données d'entrée, est toujours DbScanExpression.</span><span class="sxs-lookup"><span data-stu-id="c005e-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="c005e-118">Un DbScanExpression peut représenter une table ou une vue ou un jeu de données définies avec une requête si la propriété de métadonnées « Defining Query » de la cible est non null.</span><span class="sxs-lookup"><span data-stu-id="c005e-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>  
  
 <span data-ttu-id="c005e-119">Un DbScanExpression qui représente une requête peut atteindre un fournisseur en tant que cible de modification uniquement si le jeu a été défini à l'aide d'une requête de définition dans le modèle mais qu'aucune fonction n'a été fournie pour l'opération de modification correspondante.</span><span class="sxs-lookup"><span data-stu-id="c005e-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="c005e-120">Il est possible que les fournisseurs ne puissent pas prendre en charge un tel scénario (par exemple, c'est le cas de SqlClient).</span><span class="sxs-lookup"><span data-stu-id="c005e-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>  
  
 <span data-ttu-id="c005e-121">DbInsertCommandTree représente une opération d'insertion d'une seule ligne exprimée sous la forme d'une arborescence de commandes.</span><span class="sxs-lookup"><span data-stu-id="c005e-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 <span data-ttu-id="c005e-122">DbUpdateCommandTree représente une opération de mise à jour d'une seule ligne exprimée sous la forme d'une arborescence de commandes.</span><span class="sxs-lookup"><span data-stu-id="c005e-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>  
  
 <span data-ttu-id="c005e-123">DbDeleteCommandTree représente une opération de suppression d'une seule ligne exprimée sous la forme d'une arborescence de commandes.</span><span class="sxs-lookup"><span data-stu-id="c005e-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>  
  
### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="c005e-124">Restrictions sur les propriétés de l'arborescence de commandes de modification</span><span class="sxs-lookup"><span data-stu-id="c005e-124">Restrictions on Modification Command Tree Properties</span></span>  
 <span data-ttu-id="c005e-125">Les informations et restrictions suivantes s'appliquent aux propriétés de l'arborescence de commandes de modification.</span><span class="sxs-lookup"><span data-stu-id="c005e-125">The following information and restrictions apply to the modification command tree properties.</span></span>  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="c005e-126">Renvoi dans DbInsertCommandTree et DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="c005e-127">Lorsque la valeur n'est pas null, le renvoi indique que la commande retourne un lecteur.</span><span class="sxs-lookup"><span data-stu-id="c005e-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="c005e-128">Dans le cas contraire, la commande doit retourner une valeur scalaire qui indique le nombre de lignes affectées (insérées ou mises à jour).</span><span class="sxs-lookup"><span data-stu-id="c005e-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>  
  
 <span data-ttu-id="c005e-129">La valeur du renvoi spécifie une projection de résultats à retourner selon la ligne insérée ou mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c005e-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="c005e-130">Une ligne ne peut être représentée que par le type DbNewInstanceExpression, avec chacun de ses arguments DbPropertyExpression sur un DbVariableReferenceExpression qui représente une référence à la cible du DbModificationCommandTree correspondant.</span><span class="sxs-lookup"><span data-stu-id="c005e-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="c005e-131">Les propriétés représentées par les DbPropertyExpressions utilisés dans le renvoi de propriété sont toujours des valeurs générées ou calculées par la banque.</span><span class="sxs-lookup"><span data-stu-id="c005e-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="c005e-132">Dans DbInsertCommandTree, le renvoi n'a pas la valeur null lorsque au moins une propriété de la table dans laquelle la ligne est insérée est spécifiée comme générée ou calculée par la banque (marquée comme StoreGeneratedPattern.Identity ou StoreGeneratedPattern.Computed dans le ssdl).</span><span class="sxs-lookup"><span data-stu-id="c005e-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="c005e-133">Dans DbUpdateCommandTrees, le renvoi n'a pas la valeur null lorsque au moins une propriété de la table dans laquelle la ligne est mise à jour est spécifiée comme calculée par la banque (marqué comme StoreGeneratedPattern.Computed dans le ssdl).</span><span class="sxs-lookup"><span data-stu-id="c005e-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="c005e-134">SetClauses dans DbInsertCommandTree et DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>  
 <span data-ttu-id="c005e-135">SetClauses spécifie la liste des clauses set d'insertion ou de mise à jour qui définissent l'opération d'insertion ou de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c005e-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 <span data-ttu-id="c005e-136">Property spécifie la propriété à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="c005e-136">Property specifies the property that should be updated.</span></span> <span data-ttu-id="c005e-137">Il s'agit toujours d'un DbPropertyExpression sur un DbVariableReferenceExpression, qui représente une référence à la cible du DbModificationCommandTree correspondant.</span><span class="sxs-lookup"><span data-stu-id="c005e-137">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
 <span data-ttu-id="c005e-138">Value spécifie la nouvelle valeur avec laquelle mettre à jour la propriété.</span><span class="sxs-lookup"><span data-stu-id="c005e-138">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="c005e-139">Elle est de type DbConstantExpression ou DbNullExpression.</span><span class="sxs-lookup"><span data-stu-id="c005e-139">It is either of type DbConstantExpression or DbNullExpression.</span></span>  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="c005e-140">Predicate dans DbUpdateCommandTree et DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="c005e-140">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>  
 <span data-ttu-id="c005e-141">Predicate spécifie le prédicat utilisé pour identifier dans la collection cible les membres à mettre à jour ou à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c005e-141">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="c005e-142">Il s'agit d'une arborescence de l'expression construite sur le sous-ensemble de DbExpressions suivant :</span><span class="sxs-lookup"><span data-stu-id="c005e-142">It is an expression tree built of the following subset of DbExpressions:</span></span>  
  
-   <span data-ttu-id="c005e-143">DbComparisonExpression de type Equals, avec l'enfant droit qui est un DbPropertyExression comme délimité ci-dessous et l'enfant gauche qui est un DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="c005e-143">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExression as restricted below and the left child a DbConstantExpression.</span></span>  
  
-   <span data-ttu-id="c005e-144">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-144">DbConstantExpression</span></span>  
  
-   <span data-ttu-id="c005e-145">DbIsNullExpression sur un DbPropertyExpression comme délimité ci-dessous</span><span class="sxs-lookup"><span data-stu-id="c005e-145">DbIsNullExpression over a DbPropertyExpresison as restricted below</span></span>  
  
-   <span data-ttu-id="c005e-146">DbPropertyExpression sur un DbVariableReferenceExpression qui représente une référence à la cible du DbModificationCommandTree correspondant.</span><span class="sxs-lookup"><span data-stu-id="c005e-146">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>  
  
-   <span data-ttu-id="c005e-147">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-147">DbAndExpression</span></span>  
  
-   <span data-ttu-id="c005e-148">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-148">DbNotExpression</span></span>  
  
-   <span data-ttu-id="c005e-149">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-149">DbOrExpression</span></span>  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="c005e-150">Génération SQL de modification dans le fournisseur d'exemples</span><span class="sxs-lookup"><span data-stu-id="c005e-150">Modification SQL Generation in the Sample Provider</span></span>  
 <span data-ttu-id="c005e-151">Le [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) présente les composants de fournisseurs de données ADO.NET qui prennent en charge la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c005e-151">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="c005e-152">Il cible une base de données SQL Server 2005 et est implémenté comme un wrapper sur le fournisseur de données ADO.NET 2.0 System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="c005e-152">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="c005e-153">Le module de génération SQL de modification du fournisseur d'exemples (situé dans le fichier SQL Generation\DmlSqlGenerator.cs) prend un DbModificationCommandTree d'entrée et produit une instruction SQL de modification unique pouvant être suivie par une instruction SELECT pour retourner un lecteur, si spécifié par le DbModificationCommandTree.</span><span class="sxs-lookup"><span data-stu-id="c005e-153">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="c005e-154">Notez que la forme des commandes générées est affectée par la base de données SQL Server cible.</span><span class="sxs-lookup"><span data-stu-id="c005e-154">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>  
  
### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="c005e-155">Classes d'assistance : ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="c005e-155">Helper Classes: ExpressionTranslator</span></span>  
 <span data-ttu-id="c005e-156">ExpressionTranslator fait office de traducteur commun léger pour toutes les propriétés de l'arborescence de commandes de modification de type DbExpression.</span><span class="sxs-lookup"><span data-stu-id="c005e-156">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="c005e-157">Il prend uniquement en charge la traduction des types de l'expression auxquels les propriétés de l'arborescence de commandes de modification sont contraintes et est construit en fonction de ces contraintes particulières.</span><span class="sxs-lookup"><span data-stu-id="c005e-157">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>  
  
 <span data-ttu-id="c005e-158">Les informations suivantes décrivent la visite de types de l'expression spécifiques (les nœuds avec des traductions simples sont omis).</span><span class="sxs-lookup"><span data-stu-id="c005e-158">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>  
  
### <a name="dbcomparisonexpression"></a><span data-ttu-id="c005e-159">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-159">DbComparisonExpression</span></span>  
 <span data-ttu-id="c005e-160">Lorsque l'ExpressionTranslator est construit avec preserveMemberValues = true et lorsque la constante de droite est un DbConstantExpression (au lieu de DbNullExpression), il associe l'opérande de gauche (DbPropertyExpressions) à ce DbConstantExpression.</span><span class="sxs-lookup"><span data-stu-id="c005e-160">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="c005e-161">Cela est utilisé si une instruction SELECT de renvoi doit être générée pour identifier la ligne affectée.</span><span class="sxs-lookup"><span data-stu-id="c005e-161">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>  
  
### <a name="dbconstantexpression"></a><span data-ttu-id="c005e-162">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-162">DbConstantExpression</span></span>  
 <span data-ttu-id="c005e-163">Pour chaque constante visitée un paramètre est créé.</span><span class="sxs-lookup"><span data-stu-id="c005e-163">For each visited constant a parameter is created.</span></span>  
  
### <a name="dbpropertyexpression"></a><span data-ttu-id="c005e-164">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="c005e-164">DbPropertyExpression</span></span>  
 <span data-ttu-id="c005e-165">Étant donné que l'instance de DbPropertyExpression représente toujours la table d'entrée, sauf si la génération a créé un alias (ce qui se produit seulement pour les scénarios de mise à jour lorsqu'une variable de table est utilisée), aucun alias ne doit être spécifié pour l'entrée, la traduction par défaut est le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c005e-165">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>  
  
## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="c005e-166">Génération d'une commande SQL d'insertion</span><span class="sxs-lookup"><span data-stu-id="c005e-166">Generating an Insert SQL Command</span></span>  
 <span data-ttu-id="c005e-167">Pour un DbInsertCommandTree donné dans le fournisseur d'exemples, la commande d'insertion générée suit l'un des deux modèles d'insertion ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c005e-167">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>  
  
 <span data-ttu-id="c005e-168">Le premier modèle possède une commande pour effectuer l'insertion selon les valeurs de la liste de SetClauses et une instruction SELECT pour retourner les propriétés spécifiées dans la propriété Returning pour la ligne insérée, si la propriété Returning n'a pas la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c005e-168">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="c005e-169">L’élément de prédicat « @@ROWCOUNT > 0 » a la valeur true si une ligne a été insérée.</span><span class="sxs-lookup"><span data-stu-id="c005e-169">The predicate element "@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="c005e-170">L’élément de prédicat « keyMemberI = keyValueI &#124; SCOPE_IDENTITY() » prend la forme « keyMemberI = scope_identity() » uniquement si Keymemberi est une clé générée par le magasin, parce que scope_identity() retourne la dernière valeur identity insérée dans une colonne d’identité (générée par le magasin).</span><span class="sxs-lookup"><span data-stu-id="c005e-170">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemeberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="c005e-171">Le deuxième modèle est nécessaire si l'insertion spécifie une insertion de ligne à l'endroit où la clé primaire est générée par la banque mais n'est pas de type entier et par conséquent ne peut pas être utilisée avec scope_identity()).</span><span class="sxs-lookup"><span data-stu-id="c005e-171">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="c005e-172">Il est également utilisé s'il s'agit d'une clé composée générée par la banque.</span><span class="sxs-lookup"><span data-stu-id="c005e-172">It is also used if there is a compound store-generated key.</span></span>  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 <span data-ttu-id="c005e-173">Voici un exemple qui utilise le modèle inclus avec le fournisseur d'exemples.</span><span class="sxs-lookup"><span data-stu-id="c005e-173">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="c005e-174">Il génère une commande d'insertion d'un DbInsertCommandTree.</span><span class="sxs-lookup"><span data-stu-id="c005e-174">It generates an insert command from a DbInsertCommandTree.</span></span>  
  
 <span data-ttu-id="c005e-175">Le code suivant insère une catégorie :</span><span class="sxs-lookup"><span data-stu-id="c005e-175">The following code inserts a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="c005e-176">Ce code produit l'arborescence de commandes suivante, passée au fournisseur :</span><span class="sxs-lookup"><span data-stu-id="c005e-176">This code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 <span data-ttu-id="c005e-177">La commande de stockage que le fournisseur d'exemples produit est l'instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="c005e-177">The store command that the sample provider produces is the following SQL statement:</span></span>  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a><span data-ttu-id="c005e-178">Génération d'une commande SQL de mise à jour</span><span class="sxs-lookup"><span data-stu-id="c005e-178">Generating an Update SQL Command</span></span>  
 <span data-ttu-id="c005e-179">Pour un DbUpdateCommandTree donné, la commande de mise à jour générée est basée sur le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="c005e-179">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 <span data-ttu-id="c005e-180">La clause set est fausse («@i = 0 ») uniquement si aucune clause set n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c005e-180">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="c005e-181">Ceci permet de vérifier que toutes les colonnes calculées par la banque sont recalculées.</span><span class="sxs-lookup"><span data-stu-id="c005e-181">This is to ensure that any store-computed columns are recomputed.</span></span>  
  
 <span data-ttu-id="c005e-182">Uniquement si la propriété Returning n'a pas la valeur null, une instruction SELECT est générée pour retourner les propriétés spécifiées dans la propriété Returning.</span><span class="sxs-lookup"><span data-stu-id="c005e-182">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>  
  
 <span data-ttu-id="c005e-183">L'exemple suivant utilise le modèle inclus avec le fournisseur d'exemples pour générer une commande de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="c005e-183">The following example uses the model that is included with the sample provider to generate an update command.</span></span>  
  
 <span data-ttu-id="c005e-184">Le code utilisateur suivant met à jour une catégorie :</span><span class="sxs-lookup"><span data-stu-id="c005e-184">The following user code updates a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="c005e-185">Ce code utilisateur produit l'arborescence de commandes suivante, passée au fournisseur :</span><span class="sxs-lookup"><span data-stu-id="c005e-185">This user code produces the following command tree, which is passed to the provider:</span></span>  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 <span data-ttu-id="c005e-186">Le fournisseur d'exemples produit la commande de stockage suivante :</span><span class="sxs-lookup"><span data-stu-id="c005e-186">The sample provider produces the following store command:</span></span>  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="c005e-187">Génération d'une commande SQL de suppression</span><span class="sxs-lookup"><span data-stu-id="c005e-187">Generating a Delete SQL Command</span></span>  
 <span data-ttu-id="c005e-188">Pour un DbDeleteCommandTree donné, la commande DELETE générée est basée sur le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="c005e-188">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 <span data-ttu-id="c005e-189">L'exemple suivant utilise le modèle inclus avec le fournisseur d'exemples pour générer une commande de suppression.</span><span class="sxs-lookup"><span data-stu-id="c005e-189">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>  
  
 <span data-ttu-id="c005e-190">Le code utilisateur suivant supprime une catégorie :</span><span class="sxs-lookup"><span data-stu-id="c005e-190">The following user code deletes a Category:</span></span>  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 <span data-ttu-id="c005e-191">Ce code utilisateur produit l'arborescence de commandes suivante, passée au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="c005e-191">This user code produces the following command tree, which is passed to the provider.</span></span>  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 <span data-ttu-id="c005e-192">La commande de stockage suivante est produite par le fournisseur d'exemples :</span><span class="sxs-lookup"><span data-stu-id="c005e-192">The following store command is produced by the sample provider:</span></span>  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a><span data-ttu-id="c005e-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c005e-193">See Also</span></span>  
 [<span data-ttu-id="c005e-194">Écriture d’un fournisseur de données Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c005e-194">Writing an Entity Framework Data Provider</span></span>](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
