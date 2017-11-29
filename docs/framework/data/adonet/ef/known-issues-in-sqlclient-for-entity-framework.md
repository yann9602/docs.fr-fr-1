---
title: "Problèmes connus dans SqlClient pour l’Entity Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 67d4c4f08661bbf2febefead64e62c8a84045f47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Problèmes connus dans SqlClient pour l’Entity Framework
Cette section décrit les problèmes connus liés au fournisseur de données .NET Framework pour SQL Server (SqlClient).  
  
## <a name="trailing-spaces-in-string-functions"></a>Espaces de fin dans les fonctions de chaîne  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ignore les espaces de fin dans les valeurs de chaîne. Par conséquent, le passage d'espaces de fin dans la chaîne peut provoquer des résultats imprévisibles, voire des défaillances.  
  
 Si votre chaîne doit contenir des espaces de fin, envisagez d'ajouter un espace blanc à la fin, pour éviter que [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] ne les supprime. Si les espaces de fin ne sont pas indispensables, ils doivent être supprimés avant le passage au pipeline de la requête.  
  
## <a name="right-function"></a>Fonction RIGHT  
 Si une valeur non `null` est passée comme premier argument et que 0 est passé comme deuxième argument à `RIGHT(nvarchar(max)`, 0`)` ou `RIGHT(varchar(max)`, 0`)`, c'est une valeur `NULL` qui sera retournée, et non une chaîne `empty`.  
  
## <a name="cross-and-outer-apply-operators"></a>Opérateurs CROSS et OUTER APPLY  
 Les opérateurs CROSS et OUTER APPLY ont été introduits dans [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)]. Dans certains cas, le pipeline de requête peut produire une instruction Transact-SQL qui contient des opérateurs CROSS APPLY et/ou OUTER APPLY. Dans la mesure où certains fournisseurs principaux, notamment dans les versions de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], ne prennent pas en charge ces opérateurs, de telles requêtes ne peuvent pas être exécutées sur ces fournisseurs.  
  
 Vous trouverez ci-dessous quelques scénarios classiques susceptibles d'aboutir à la présence d'opérateurs CROSS APPLY et/ou OUTER APPLY dans la requête de sortie :  
  
-   sous-requête corrélée avec pagination ;  
  
-   `AnyElement` sur une sous-requête corrélée ou sur une collection produite par navigation ;  
  
-   requêtes LINQ qui utilisent des méthodes de regroupement acceptant un sélecteur d'élément ;  
  
-   requête dans laquelle un CROSS APPLY ou un OUTER APPLY est explicitement spécifié ;  
  
-   requête dotée d'une construction DEREF sur une construction REF.  
  
## <a name="skip-operator"></a>Opérateur SKIP  
 Si vous utilisez [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)], l’utilisation de SKIP avec ORDER BY sur des colonnes non-clés peut retourner des résultats incorrects. Le nombre de lignes ignorées peut être supérieur au nombre de lignes spécifié si la colonne non-clé contient des données en double. Cela est dû à la manière dont la sous-clause SKIP est traduite pour [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)]. Par exemple, dans la requête suivante, plus de cinq lignes peuvent être ignorées si `E.NonKeyColumn` a des valeurs en double :  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>Ciblage de la version appropriée de SQL Server  
 Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] cibles le [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] requête basée sur la version de SQL Server qui est spécifiée dans le `ProviderManifestToken` attribut de l’élément de schéma dans le fichier de modèle (.ssdl) de stockage. Cette version de SQL Server peut ne pas correspondre à celle à laquelle vous êtes connecté. Par exemple, si vous utilisez SQL Server 2005, mais que votre attribut `ProviderManifestToken` a la valeur 2008, la requête [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] générée ne peut pas s'exécuter sur le serveur. Par exemple, une requête qui utilise les nouveaux types date/heure introduits dans SQL Server 2008 ne s'exécutera pas sur les versions antérieures de SQL Server. Si vous utilisez SQL Server 2005, mais votre `ProviderManifestToken` attribut a la valeur 2000, généré [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] requête risque d’être moins optimisée, ou vous pouvez obtenir une exception indiquant que la requête n’est pas pris en charge. Pour plus d'informations, voir la section Opérateurs CROSS et OUTER APPLY, plus haut dans cette rubrique.  
  
 Certains comportements de base de données dépendent du niveau de compatibilité défini pour la base de données. Si votre attribut `ProviderManifestToken` a la valeur 2005 et que votre version de SQL Server est 2005, mais que le niveau de compatibilité d'une base de données est 80 (SQL Server 2000), le [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] généré ciblera bien SQL Server 2005, mais il est possible qu'il ne s'exécute pas comme prévu en raison du paramètre de niveau de compatibilité. Par exemple, vous pouvez perdre des informations de classement si un nom de colonne dans la liste ORDER BY correspond à un nom de colonne dans le sélecteur.  
  
## <a name="nested-queries-in-projection"></a>Requêtes imbriquées dans la projection  
 Les requêtes imbriquées d'une clause de projection peuvent être traduites en requêtes de produit cartésien sur le serveur. Sur certains serveurs principaux dont SQL Server, cela peut avoir pour conséquences l'augmentation de volume de la table TempDB et une diminution des performances du serveur.  
  
 Vous trouverez ci-dessous un exemple de requête imbriquée dans une clause de projection :  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>Valeurs d'identité GUID générées par le serveur  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge les valeurs d'identité de type GUID générées par le serveur, mais le fournisseur doit prendre en charge le retour de la valeur d'identité générée par le serveur après l'insertion d'une ligne. En commençant par [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2005, vous pouvez retourner le type de GUID généré par le serveur dans un [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] de la base de données via le [clause OUTPUT](http://go.microsoft.com/fwlink/?LinkId=169400) .  
  
## <a name="see-also"></a>Voir aussi  
 [SqlClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)  
 [Problèmes connus et des considérations dans LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
