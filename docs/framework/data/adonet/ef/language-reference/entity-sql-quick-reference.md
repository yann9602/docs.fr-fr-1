---
title: "Aide-mémoire Entity SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19be8e04f8bb0cb11c98d5361deb6deffe797fca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-quick-reference"></a>Aide-mémoire Entity SQL
Cette rubrique fournit un aide-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. Les requêtes de cette rubrique sont basés sur le modèle de vente AdventureWorks Sales Model.  
  
## <a name="literals"></a>Littéraux  
  
### <a name="string"></a>Chaîne  
 Les chaînes de caractères littérales peuvent être au format Unicode ou non-Unicode. Les chaînes Unicode sont précédées de N. Par exemple, `N'hello'`.  
  
 Exemple de littéral de chaîne non-Unicode :  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 Dans les littéraux DateTime, les parties date et heure sont obligatoires. Il n'existe pas de valeur par défaut.  
  
 Exemple :  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|25.12.06 01:01:00|  
  
### <a name="integer"></a>Integer  
 Les littéraux d'entiers peuvent être de type Int32 (123), UInt32 (123U), Int64 (123L) et UInt64 (123UL).  
  
 Exemple :  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Autre  
 Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float/Double, Decimal et la valeur `null`. Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.  
  
## <a name="type-constructors"></a>Constructeurs de type  
  
### <a name="row"></a>ROW  
 [LIGNE](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) construit une valeur (enregistrement) anonyme, structurellement typés, comme dans :`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Exemple :  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Sortie :  
  
|ProductID|Nom|  
|---------------|----------|  
|1|Adjustable Race|  
|879|All-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) construit des collections, telles que :  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Exemple :  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Sortie :  
  
|ProductID|Nom|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Large|PA-T100|…|  
  
### <a name="object"></a>Objet  
 [Nommé le constructeur de Type](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) construit les objets (nommés) définis par l’utilisateur, telles que `person("abc", 12)`.  
  
 Exemple :  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Sortie :  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Références  
  
### <a name="ref"></a>REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) crée une référence à une instance de type d’entité. Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 L'exemple suivant utilise l'opérateur d'extraction de propriété (.) pour accéder à une propriété d'entité. Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.  
  
 Exemple :  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) déréférence une valeur de référence et génère le résultat de ce déréférencement. Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.  
  
 Exemple :  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF et KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) crée une référence en passant une clé. [CLÉ](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrait la partie clé d’une expression avec référence de type.  
  
 Exemple :  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>Fonctions  
  
### <a name="canonical"></a>Canoniques  
 L’espace de noms [fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) est Edm, comme dans `Edm.Length("string")`. Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique. Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.  
  
 Exemple :  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Sortie :  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Spécifiques au fournisseur Microsoft  
 [Fonctions spécifiques au fournisseur de Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) se trouvent dans le `SqlServer` espace de noms.  
  
 Exemple :  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Sortie :  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Espaces de noms  
 [À l’aide de](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) spécifie les espaces de noms utilisés dans une expression de requête.  
  
 Exemple :  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Pagination  
 La pagination peut être exprimée en déclarant un [ignorer](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) et [limite](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sous-clauses pour le [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.  
  
 Exemple :  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Sortie :  
  
|ID|Nom|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Regroupement  
 [REGROUPEMENT par](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) indique les groupes dans les objets retournés par une requête ([sélectionnez](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression doivent être placés.  
  
 Exemple :  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Sortie :  
  
|name|  
|----------|  
|LL Mountain Seat Assembly|  
|ML Mountain Seat Assembly|  
|HL Mountain Seat Assembly|  
|...|  
  
## <a name="navigation"></a>Navigation  
 L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité (terminaison From) et une autre entité (terminaison To). [NAVIGUER](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) prend le type de relation qualifié comme \<espace de noms >.\< nom de type de relation >. Accédez retourne Ref\<T > Si la cardinalité de la terminaison to est 1. Si la cardinalité de la terminaison to est n, la Collection < Ref\<T >> sera retourné.  
  
 Exemple :  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Sortie :  
  
|AddressID|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>SELECT VALUE et SELECT  
  
### <a name="select-value"></a>SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite. Un seul élément peut être spécifié dans une clause SELECT VALUE. Lorsqu’une telle clause est utilisée, aucun wrapper de ligne n’est construit autour des éléments dans la clause SELECT et une collection de la forme souhaitée peut être générée, par exemple : `SELECT VALUE a`.  
  
 Exemple :  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Nom|  
|----------|  
|Adjustable Race|  
|All-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires. SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.  
  
 Exemple :  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Nom|ProductID|  
|----------|---------------|  
|Adjustable Race|1|  
|All-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>Expression CASE  
 Le [cas expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) évalue un ensemble d’expressions booléennes pour déterminer le résultat.  
  
 Exemple :  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Sortie :  
  
|Valeur|  
|-----------|  
|true|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Vue d’ensemble de Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
