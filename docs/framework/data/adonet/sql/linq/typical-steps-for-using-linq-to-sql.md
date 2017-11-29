---
title: "Procédure standard d'utilisation de LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5115fce1d5060d258ae5feeefd99aaaf5123a123
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="typical-steps-for-using-linq-to-sql"></a>Procédure standard d'utilisation de LINQ to SQL
Pour implémenter une application [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], suivez les étapes décrites ultérieurement dans cette rubrique. Notez que de nombreuses étapes sont facultatives. Il est tout à fait possible que votre modèle objet soit utilisable dans son état par défaut.  
  
 Pour un démarrage rapide, créez votre modèle objet à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] et commencez à coder vos requêtes.  
  
## <a name="creating-the-object-model"></a>Création du modèle objet  
 La première étape consiste à créer un modèle objet à partir des métadonnées d'une base de données relationnelle existante. Le modèle objet représente la base de données en fonction du langage de programmation du développeur. Pour plus d’informations, consultez [le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
### <a name="1-select-a-tool-to-create-the-model"></a>1. Sélectionnez un outil pour créer le modèle.  
 Trois outils sont disponibles pour la création du modèle.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  
  
     Ce concepteur fournit une interface utilisateur élaborée pour créer un modèle objet à partir d'une base de données existante. Cet outil fait partie de l'IDE de [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]. C'est le mieux adapté aux bases de données de taille réduite ou moyenne.  
  
-   Outil de génération de code SQLMetal  
  
     Cet utilitaire en ligne de commande propose un ensemble d'options légèrement différent d'[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Il est mieux adapté à la modélisation de grandes bases de données. Pour plus d’informations, consultez [SqlMetal.exe (outil de génération de code)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
-   Éditeur de code  
  
     Vous pouvez écrire votre propre code à l'aide de l'éditeur de code [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] ou de tout autre éditeur. Cette approche, qui peut générer des erreurs, n'est pas conseillée lorsque vous disposez d'une base de données existante et que vous pouvez utiliser [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou SQLMetal. Toutefois, l'éditeur de code peut s'avérer particulièrement utile pour affiner ou modifier du code déjà généré à l'aide d'autres outils. Pour plus d’informations, consultez [Comment : personnaliser les Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md).  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a>2. Sélectionnez le type de code à générer.  
  
-   Fichier de code source [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C# pour le mappage basé sur les attributs.  
  
     Incluez ensuite ce fichier de code dans votre projet [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]. Pour plus d’informations, consultez [mappage basé sur l’attribut](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Fichier XML pour le mappage externe.  
  
     Cette approche vous permet de maintenir les métadonnées de mappage en dehors de votre code d'application. Pour plus d’informations, consultez [mappage externe](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ne prend pas en charge la génération de fichiers de mappage externes. Vous devez utiliser l'outil SQLMetal pour implémenter cette fonctionnalité.  
  
-   Un fichier DBML, que vous pouvez modifier avant de générer un fichier de code final.  
  
     Il s'agit d'une fonctionnalité avancée.  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a>3. Affinez le fichier de code en fonction des besoins de votre application.  
 Pour cela, vous pouvez utiliser [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] ou l'éditeur de code.  
  
## <a name="using-the-object-model"></a>Utilisation du modèle objet  
 L'illustration suivante montre la relation entre le développeur et les données dans un scénario à deux niveaux. Pour d’autres scénarios, consultez [multicouches et des Applications distantes avec LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md).  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 Maintenant que vous disposez du modèle objet, vous pouvez décrire les demandes d'informations et manipuler des données dans ce modèle. Pensez en termes d'objets et de propriétés dans votre modèle objet et non pas en termes de lignes et de colonnes de la base de données. Vous ne traitez pas directement avec la base de données.  
  
 Lorsque vous indiquez à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] d’exécuter une requête que vous avez décrite ou un appel `SubmitChanges()` sur les données que vous avez manipulées, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communique avec la base de données dans la langue de la base de données.  
  
 La procédure standard d'utilisation du modèle objet créé est présentée ci-dessous.  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a>1. Créez des requêtes pour récupérer des informations de la base de données.  
 Pour plus d’informations, consultez [concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md) et [exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md).  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a>2. Substituez des comportements par défaut pour l'insertion, la mise à jour et la suppression.  
 Cette étape est facultative. Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a>3. Définissez les options appropriées pour détecter et signaler des conflits d'accès concurrentiel.  
 Vous pouvez conserver les valeurs par défaut de votre modèle pour la gestion des conflits d'accès concurrentiel ou les adapter à vos besoins. Pour plus d’informations, consultez [Comment : spécifier lequel les membres sont testées pour les conflits d’accès concurrentiel](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) et [Comment : spécifier lors de la concurrence Exceptions sont levées](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
### <a name="4-establish-an-inheritance-hierarchy"></a>4. Établissez une hiérarchie d'héritage.  
 Cette étape est facultative. Pour plus d’informations, consultez [prise en charge l’héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md).  
  
### <a name="5-provide-an-appropriate-user-interface"></a>5. Fournissez une interface utilisateur appropriée.  
 Cette étape est facultative et dépend de l'utilisation ultérieure de votre application.  
  
### <a name="6-debug-and-test-your-application"></a>6. Déboguez et testez votre application.  
 Pour plus d’informations, consultez [prise en charge de débogage](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
