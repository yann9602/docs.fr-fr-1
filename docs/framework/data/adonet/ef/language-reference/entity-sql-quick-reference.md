---
title: "Aide-m&#233;moire sur Entity SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Aide-m&#233;moire sur Entity SQL
Cette rubrique fournit un aide\-mémoire sur les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)].  Les requêtes de cette rubrique sont basées sur le modèle de vente Adventure Works Sales Model.  
  
## Littéraux  
  
### Chaîne  
 Les chaînes de caractères littérales peuvent être au format Unicode ou non\-Unicode.  Les chaînes Unicode sont précédées de N.  Par exemple, `N'hello'`.  
  
 Exemple de littéral de chaîne non\-Unicode :  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|hello|  
  
### DateTime  
 Dans les littéraux DateTime, les parties date et heure sont obligatoires.  Il n'existe pas de valeur par défaut.  
  
 Exemple :  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|25.12.06 01:01:00|  
  
### Integer  
 Les littéraux d'entiers peuvent être de type Int32 \(123\), UInt32 \(123U\), Int64 \(123L\) et UInt64 \(123UL\).  
  
 Exemple :  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|1|  
|2|  
|3|  
  
### Autre  
 Les autres littéraux pris en charge par [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont Guid, Binary, Float\/Double, Decimal et la valeur `null`.  Les littéraux NULL dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont considérés compatibles avec tous les autres types dans le modèle conceptuel.  
  
## Constructeurs de type  
  
### ROW  
 [ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) construit une valeur anonyme, structurellement typée \(enregistrement\) comme dans : `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Exemple :  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Sortie :  
  
|ProductID|Nom|  
|---------------|---------|  
|1|Adjustable Race|  
|879|All\-Purpose Bike Stand|  
|712|AWC Logo Cap|  
|...|...|  
  
### MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) construit des collections, telles que :  
  
 `MULTISET(1,2,2,3)` `--same as`\-`{1,2,2,3}.`  
  
 Exemple :  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Sortie :  
  
|ProductID|Nom|ProductNumber|…|  
|---------------|---------|-------------------|-------|  
|842|Touring\-Panniers, Large|PA\-T100|…|  
  
### Objet  
 [Constructeur de type nommé](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) construit des objets définis par l'utilisateur \(nommés\), tels que `person("abc", 12)`.  
  
 Exemple :  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Sortie :  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911\-403C\-98|1|776|...|  
|2|4911\-403C\-98|3|777|...|  
|...|...|...|...|...|  
  
## Références  
  
### REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) crée une référence à une instance de type entité.  Par exemple, la requête suivante retourne les références à chaque entité Order dans le jeu d'entités Orders :  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|1|  
|2|  
|3|  
|...|  
  
 L'exemple suivant utilise l'opérateur d'extraction de propriété \(.\) pour accéder à une propriété d'entité.  Lors de l'utilisation de l'opérateur d'extraction de propriété, la référence est automatiquement supprimée.  
  
 Exemple :  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) supprime une valeur de référence et génère le résultat de ce déréférencement.  Par exemple, la requête suivante génère les entités Order pour chaque élément Order du jeu d'entités Orders : `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`.  
  
 Exemple :  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### CREATEREF et KEY  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) crée une référence qui passe une clé.  [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extrait la partie clé d'une expression avec la référence de type.  
  
 Exemple :  
  
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
  
## Fonctions  
  
### Canoniques  
 L'espace de noms des [fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) est Edm, comme dans `Edm.Length("string")`.  Vous n'avez pas besoin de spécifier l'espace de noms sauf si un autre espace de noms est importé et qu'il contient une fonction portant le même nom qu'une fonction canonique.  Si deux espaces de noms partagent la même fonction, l'utilisateur doit spécifier le nom complet.  
  
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
  
### Spécifiques au fournisseur Microsoft  
 Les [fonctions spécifiques au fournisseur Microsoft](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) figurent dans l'espace de noms `SqlServer`.  
  
 Exemple :  
  
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
  
## Espaces de noms  
 [USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) spécifie les espaces de noms utilisés dans une expression de requête.  
  
 Exemple :  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|aa|  
  
## Pagination  
 La pagination peut s'effectuer en déclarant des sous\-clauses [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) et [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) de la clause [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
 Exemple :  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Sortie :  
  
|ID|Nom|  
|--------|---------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## Regroupement  
 [GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) spécifie des groupes dans lesquels doivent être placés les objets retournés par une expression de requête \([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)\).  
  
 Exemple :  
  
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
  
## Navigation  
 L'opérateur de navigation de relations vous permet de parcourir la relation entre une entité \(terminaison From\) et une autre entité \(terminaison To\).  [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) accepte le type de relation qualifié comme \<espace de noms\>.\<nom du type de relation\>.  Navigate retourne Ref\<T\> si la cardinalité de la terminaison To est 1.  Si la cardinalité de la terminaison To est n, la valeur retournée est Collection\<Ref\<T\>\>.  
  
 Exemple :  
  
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
  
## SELECT VALUE et SELECT  
  
### SELECT VALUE  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit la clause SELECT VALUE pour ignorer la construction de ligne implicite.  Un seul élément peut être spécifié dans une clause SELECT VALUE.  Lorsqu'une telle clause est utilisée, aucun wrapper de ligne n'est construit autour des éléments de la clause SELECT et une collection de la forme souhaitée peut être générée, par exemple : `SELECT VALUE a`.  
  
 Exemple :  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Sortie :  
  
|Nom|  
|---------|  
|Adjustable Race|  
|All\-Purpose Bike Stand|  
|AWC Logo Cap|  
|...|  
  
### SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] fournit également le constructeur de ligne pour construire des lignes arbitraires.  SELECT extrait un ou plusieurs éléments de la projection et produit un enregistrement de données avec des champs, par exemple : `SELECT a, b, c`.  
  
 Exemple :  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Nom|ProductID|  
|---------|---------------|  
|Adjustable Race|1|  
|All\-Purpose Bike Stand|879|  
|AWC Logo Cap|712|  
|...|...|  
  
## Expression CASE  
 L'[expression CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) évalue un ensemble d'expressions booléennes pour déterminer le résultat.  
  
 Exemple :  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Sortie :  
  
|Valeur|  
|------------|  
|TRUE|  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Vue d'ensemble d'Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)