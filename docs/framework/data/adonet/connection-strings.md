---
title: "Cha&#238;nes de connexion dans ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Cha&#238;nes de connexion dans ADO.NET
Le .NET Framework 2.0 a introduit de nouvelles fonctionnalités permettant d'utiliser des chaînes de connexion, y compris l'intégration de nouveaux mots clés aux classes de générateur de chaînes de connexion, qui facilitent la création de chaînes de connexion valides au moment de l'exécution.  
  
 Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.  La syntaxe dépend du fournisseur de données et la chaîne de connexion est analysée lors de la tentative d'ouverture d'une connexion.  Des erreurs de syntaxe génèrent une exception runtime mais d'autres erreurs ne se produisent qu'après que la source de données a reçu des informations de connexion.  Une fois validée, la source de données applique les options spécifiées dans la chaîne de connexion et ouvre la connexion.  
  
 Le format d'une chaîne de connexion est une liste délimitée par des points\-virgules de paires de paramètres clé\/valeur :  
  
 `keyword1=value; keyword2=value;`  
  
 Les mots clés ne respectent pas la casse et les espaces entre les paires clé\/valeur sont ignorés.  Toutefois, des valeurs peuvent respecter la casse, en fonction de la source de données.  Toute valeur contenant un point\-virgule ou des guillemets simples ou doubles doit être placée entre des guillemets doubles.  
  
 La syntaxe de chaîne de connexion valide dépend du fournisseur et a évolué au fil des ans, par rapport aux premières API, telles qu'ODBC.  Le fournisseur de données .NET Framework pour SQL Server \(SqlClient\) incorpore de nombreux éléments d'une syntaxe plus ancienne et se montre généralement plus souple avec une syntaxe de chaîne de connexion ordinaire.  Des synonymes tout aussi valides d'éléments de syntaxe de chaîne de connexion se rencontrent fréquemment, mais certaines erreurs de syntaxe et d'orthographe peuvent poser des problèmes.  Par exemple, "`Integrated Security=true`" est valide, tandis que "`IntegratedSecurity=true`" provoque une erreur.  Par ailleurs, les chaînes de connexion générées au moment de l'exécution à partir d'une entrée utilisateur non validée peuvent entraîner des attaques par injection de chaîne, ce qui compromet la sécurité au niveau de la source de données.  
  
 Pour résoudre ces problèmes, ADO.NET 2.0 a introduit de nouveaux générateurs de chaînes de connexion pour chaque fournisseur de données .NET Framework.  Les mots clés son exposés en tant que propriétés, ce qui permet de valider la syntaxe de chaîne de connexion avant de la soumettre à la source de données.  
  
## Dans cette section  
 [Générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.  
  
 [Chaînes de connexion et fichiers de configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.  
  
 [Syntaxe de chaîne de connexion](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.  
  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.  
  
## Voir aussi  
 [Connexion à une source de données](../../../../ocs/framework/data/adonet/connecting-to-a-data-source.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)