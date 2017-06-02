---
title: "Authentification dans SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
caps.latest.revision: 9
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 9
---
# Authentification dans SQL Server
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prend en charge deux modes d'authentification, le mode d'authentification Windows et le mode mixte.  
  
-   L'authentification Windows correspond au mode par défaut et il est souvent qualifié de sécurité intégrée car ce modèle de sécurité [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] est étroitement intégré à Windows.  Des comptes d'utilisateurs et de groupes Windows spécifiques sont approuvés pour se connecter à SQL Server.  Les utilisateurs Windows qui ont déjà été authentifiés n'ont pas besoin de présenter d'informations d'identification supplémentaires.  
  
-   Le mode mixte prend en charge l'authentification par Windows et par [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  Les paires nom d'utilisateur–mot de passe sont conservées dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]
>  Il est recommandé d'utiliser l'authentification Windows chaque fois que possible.  L'authentification Windows utilise une série de messages chiffrés pour authentifier les utilisateurs dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  Lorsque des connexions [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] sont utilisées, les noms de connexion [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] et les mots de passe sont transmis sur le réseau, ce qui les rend moins sûrs.  
  
 Avec l'authentification Windows, les utilisateurs ont déjà ouvert une session Windows et n'ont pas besoin d'ouvrir une session [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] distincte.  Le `SqlConnection.ConnectionString` suivant spécifie l'authentification Windows sans nécessiter de nom d'utilisateur ni de mot de passe.  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
>  Les connexions sont différentes des utilisateurs de base de données.  Vous devez mapper les connexions ou les groupes Windows sur les utilisateurs de base de données ou les rôles dans une opération distincte.  Vous accordez ensuite des autorisations aux utilisateurs ou aux rôles pour accéder aux objets de base de données.  
  
## Scénarios d'authentification  
 L'authentification Windows représente généralement le meilleur choix dans les situations suivantes :  
  
-   Il existe un contrôleur de domaine.  
  
-   L'application et la base de données se trouvent sur le même ordinateur.  
  
-   Vous utilisez une instance de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Express ou LocalDB.  
  
 Les connexions SQL Server sont souvent utilisées dans les situations suivantes :  
  
-   si vous avez un groupe de travail ;  
  
-   les utilisateurs se connectent à partir de domaines différents, non approuvés ;  
  
-   les applications Internet, comme [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
  
> [!NOTE]
>  La spécification de l'authentification Windows ne désactive pas les connexions [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  Utilisez l'instruction [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] ALTER LOGIN DISABLE pour désactiver des connexions [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] dotées de privilèges élevés.  
  
## Types de connexions  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prend en charge trois types de connexions :  
  
-   Compte d'utilisateur Windows local ou compte de domaine approuvé.  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] s'appuie sur Windows pour authentifier les comptes d'utilisateurs Windows.  
  
-   Groupe Windows.  Accorder l'accès à un groupe Windows permet d'accorder l'accès à toutes les connexions utilisateur Windows membres du groupe.  
  
-   Connexion [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] stocke le nom d'utilisateur et un hachage du mot de passe dans la base de données MASTER, en utilisant des méthodes d'authentification internes pour vérifier les tentatives de connexion.  
  
> [!NOTE]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] fournit les connexions créées à partir de certificats ou de clés asymétriques qui sont utilisées seulement pour la signature de code.  Elles ne peuvent pas être utilisées pour se connecter à [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].  
  
## Authentification en mode mixte  
 Si vous devez utiliser l'authentification en mode mixte, vous devez créer des connexions [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] qui sont stockées dans SQL Server.  Vous devez ensuite fournir le nom d'utilisateur et le mot de passe [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] au moment de l'exécution.  
  
> [!IMPORTANT]
>  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] est installé avec une connexion [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nommée `sa` \(abréviation de « system administrator »\).  Attribuez un mot de passe fort à la connexion `sa` et n'utilisez pas la connexion `sa` dans votre application.  La connexion `sa` correspond au rôle serveur fixe `sysadmin`, qui possède des informations d'identification d'administration irrévocables sur le serveur entier.  Si un attaquant bénéficie de l'accès en tant qu'administrateur système, les dommages potentiels sont sans limite.  Tous les membres du groupe `BUILTIN\Administrators` Windows \(groupe des administrateurs locaux\) sont membres du rôle `sysadmin` par défaut, mais peuvent être supprimés de ce rôle.  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] fournit des mécanismes de stratégie de mot de passe Windows pour les connexions [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] lorsque le logiciel s'exécute sous [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] ou des versions ultérieures.  Les stratégies de complexité des mots de passe sont conçues pour prévenir les attaques en force brute en augmentant le nombre de mots de passe possibles.  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] peut appliquer aux mots de passe [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] les mêmes stratégies de complexité et d'expiration que celles utilisées dans [!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)].  
  
> [!IMPORTANT]
>  La concaténation des chaînes de connexion à partir des entrées utilisateur peut vous rendre vulnérable à une attaque par injection de chaîne de connexion.  Utilisez le <xref:System.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion valides du point de vue de la syntaxe au moment de l'exécution.  Pour plus d'informations, consultez [Générateurs de chaînes de connexion](../../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## Ressources externes  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Principaux](http://msdn.microsoft.com/library/bb543165.aspx) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]|Décrit les connexions et autres entités de sécurité dans [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].|  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [Scénarios de sécurité des applications dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)   
 [Connexion à une source de données](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [Chaînes de connexion](../../../../../docs/framework/data/adonet/connection-strings.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)