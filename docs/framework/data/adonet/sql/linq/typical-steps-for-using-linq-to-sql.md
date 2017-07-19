---
title: "Proc&#233;dure standard d&#39;utilisation de LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Proc&#233;dure standard d&#39;utilisation de LINQ to SQL
Pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], suivez les étapes décrites ultérieurement dans cette rubrique.  Notez que de nombreuses étapes sont facultatives.  Il est tout à fait possible que votre modèle objet soit utilisable dans son état par défaut.  
  
 Pour un démarrage rapide, créez votre modèle objet à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] et commencez à coder vos requêtes.  
  
## Création du modèle objet  
 La première étape consiste à créer un modèle objet à partir des métadonnées d'une base de données relationnelle existante.  Le modèle objet représente la base de données en fonction du langage de programmation du développeur.  Pour plus d'informations, consultez [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### 1.Sélectionnez un outil pour créer le modèle.  
 Trois outils sont disponibles pour la création du modèle.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  
  
     Ce concepteur fournit une interface utilisateur élaborée pour créer un modèle objet à partir d'une base de données existante.  Cet outil fait partie de l'IDE de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]. C'est le mieux adapté aux bases de données de taille réduite ou moyenne.  
  
-   Outil de génération de code SQLMetal  
  
     Cet utilitaire en ligne de commande propose un ensemble d'options légèrement différent d'[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].  Il est mieux adapté à la modélisation de grandes bases de données.  Pour plus d'informations, consultez [SqlMetal.exe \(outil de génération de code\)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Éditeur de code  
  
     Vous pouvez écrire votre propre code à l'aide de l'éditeur de code [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ou de tout autre éditeur.  Cette approche, qui peut générer des erreurs, n'est pas conseillée lorsque vous disposez d'une base de données existante et que vous pouvez utiliser [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou SQLMetal.  Toutefois, l'éditeur de code peut s'avérer particulièrement utile pour affiner ou modifier du code déjà généré à l'aide d'autres outils.  Pour plus d'informations, consultez [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### 2.Sélectionnez le type de code à générer.  
  
-   Fichier de code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# pour le mappage basé sur les attributs.  
  
     Incluez ensuite ce fichier de code dans votre projet [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]. Pour plus d'informations, consultez [Mappage basé sur les attributs](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Fichier XML pour le mappage externe.  
  
     Cette approche vous permet de maintenir les métadonnées de mappage en dehors de votre code d'application.  Pour plus d'informations, consultez [Mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ne prend pas en charge la génération de fichiers de mappage externes.  Vous devez utiliser l'outil SQLMetal pour implémenter cette fonctionnalité.  
  
-   Un fichier DBML, que vous pouvez modifier avant de générer un fichier de code final.  
  
     Il s'agit d'une fonctionnalité avancée.  
  
### 3.Affinez le fichier de code en fonction des besoins de votre application.  
 Pour cela, vous pouvez utiliser [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou l'éditeur de code.  
  
## Utilisation du modèle objet  
 L'illustration suivante montre la relation entre le développeur et les données dans un scénario à deux niveaux.  Pour d'autres scénarios, consultez [Applications multicouches et distantes avec LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Maintenant que vous disposez du modèle objet, vous pouvez décrire les demandes d'informations et manipuler des données dans ce modèle.  Pensez en termes d'objets et de propriétés dans votre modèle objet et non pas en termes de lignes et de colonnes de la base de données.  Vous ne traitez pas directement avec la base de données.  
  
 Lorsque vous indiquez à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] d'exécuter une requête que vous avez décrite ou d'appeler `SubmitChanges()` sur des données que vous avez manipulées, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communique avec la base de données dans le langage de cette dernière.  
  
 La procédure standard d'utilisation du modèle objet créé est présentée ci\-dessous.  
  
### 1.Créez des requêtes pour récupérer des informations de la base de données.  
 Pour plus d'informations, consultez [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) et [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### 2.Substituez des comportements par défaut pour l'insertion, la mise à jour et la suppression.  
 Cette étape est facultative.  Pour plus d'informations, consultez [Personnalisation des opérations d'insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### 3.Définissez les options appropriées pour détecter et signaler des conflits d'accès concurrentiel.  
 Vous pouvez conserver les valeurs par défaut de votre modèle pour la gestion des conflits d'accès concurrentiel ou les adapter à vos besoins.  Pour plus d'informations, consultez [Procédure : spécifier les membres dont les conflits d'accès concurrentiel doivent être vérifiés](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) et [Procédure : spécifier le moment où des exceptions d'accès concurrentiel sont levées](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### 4.Établissez une hiérarchie d'héritage.  
 Cette étape est facultative.  Pour plus d'informations, consultez [Prise en charge de l'héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### 5.Fournissez une interface utilisateur appropriée.  
 Cette étape est facultative et dépend de l'utilisation ultérieure de votre application.  
  
### 6.Déboguez et testez votre application.  
 Pour plus d'informations, consultez [Prise en charge du débogage](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## Voir aussi  
 [Prise en main](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)   
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)