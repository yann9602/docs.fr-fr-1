---
title: "Sécurité dans LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d49787f7-414e-4c71-aa33-80a5895536b1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3b3f23be3be6d0c50f015be95b10938178f198bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-in-linq-to-sql"></a>Sécurité dans LINQ to SQL
Les risques de sécurité sont toujours présents lorsque vous vous connectez à une base de données. Même si LINQ to SQL inclut de nouvelles méthodes d'utilisation des données dans SQL Server, il ne fournit pas de mécanismes de sécurité supplémentaires.  
  
## <a name="access-control-and-authentication"></a>Contrôle d'accès et authentification  
 LINQ to SQL ne dispose pas de modèle utilisateur ou de mécanismes d'authentification qui lui sont propres. SQL Server Security vous permet de contrôler l'accès à la base de données, aux tables de base de données, aux vues et aux procédures stockées qui sont mappées à votre modèle objet. Accordez l'accès requis minimal aux utilisateurs et exigez des mots de passe forts pour l'authentification des utilisateurs.  
  
## <a name="mapping-and-schema-information"></a>Informations de mappage et de schéma  
 Les informations de schéma de base de données et de mappage de type SQL-CLR de votre modèle objet ou fichier de mappage externe sont consultables par tous ceux qui ont accès à ces fichiers via le système de fichiers. Supposons que les informations de schéma sont consultables par tous ceux qui peuvent accéder au modèle objet ou au fichier de mappage externe. Pour éviter un accès plus étendu aux informations de schéma, utilisez des mécanismes de sécurité des fichiers pour sécuriser les fichiers sources et de mappage.  
  
## <a name="connection-strings"></a>Chaînes de connexion  
 Dans la mesure du possible, vous devez éviter d'utiliser des mots de passe dans les chaînes de connexion. Non seulement une chaîne de connexion constitue un risque de sécurité en tant que telle, mais elle peut également être ajoutée en texte clair au modèle objet ou au fichier de mappage externe lors de l'utilisation du Concepteur Objet/Relationnel ou de l'outil de ligne de commande SQLMetal. Toute personne pouvant accéder au modèle objet ou au fichier de mappage externe via le système de fichiers peut visualiser le mot de passe de connexion (s'il est inclus dans la chaîne de connexion).  
  
 Pour réduire de tels risques, utilisez la sécurité intégrée pour effectuer une connexion approuvée avec [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)]. En utilisant cette approche, vous ne devez pas stocker de mot de passe dans la chaîne de connexion. Pour plus d’informations, consultez [sécurité SQL Server](../../../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
 En l'absence de sécurité intégrée, un mot de passe en texte clair est nécessaire dans la chaîne de connexion. La méthode la plus appropriée pour sécuriser votre chaîne de connexion, dans l'ordre croissant de risque, est la suivante :  
  
-   Utilisez la sécurité intégrée.  
  
-   Sécurisez les chaînes de connexion à l'aide de mots de passe et minimisez l'accès à celles-ci.  
  
-   Utilisez une classe <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> au lieu d'une chaîne de connexion car elle limite la durée d'exposition. La classe <xref:System.Data.Linq.DataContext?displayProperty=nameWithType> LINQ to SQL peut être instanciée à l'aide d'un objet <xref:System.Data.SqlClient.SqlConnection>.  
  
-   Minimisez les durées de vie et les points d'accès pour toutes les chaînes de connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Forum Aux Questions](../../../../../../docs/framework/data/adonet/sql/linq/frequently-asked-questions.md)
