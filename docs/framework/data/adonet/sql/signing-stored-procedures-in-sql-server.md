---
title: "Signature de procédures stockées dans SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3f1ed66ed7caf2272ca27097dc9a838bec7d0ae
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="signing-stored-procedures-in-sql-server"></a>Signature de procédures stockées dans SQL Server
Vous pouvez signer une procédure stockée avec un certificat ou une clé asymétrique. Cela est très utile lorsque des autorisations ne peuvent pas être héritées par le biais du chaînage des propriétés ou lorsque ce dernier est rompu, comme avec SQL dynamique. Vous devez alors créer un utilisateur mappé au certificat en accordant à l'utilisateur du certificat des autorisations sur les objets auxquels la procédure stockée doit accéder.  
  
 Lorsque la procédure stockée est exécutée, SQL Server combine les autorisations de l'utilisateur du certificat à celles de l'appelant. À la différence de la clause EXECUTE AS, il ne modifie pas le contexte d'exécution de la procédure. Les fonctions intégrées qui retournent les noms d'accès et d'utilisateur retournent le non de l'appelant, et non celui de l'utilisateur du certificat.  
  
 Une signature numérique est un résumé des données qui est chiffré avec la clé privée du signataire. La clé privée garantit que la signature numérique est unique à son porteur ou propriétaire. Vous pouvez signer des procédures stockées, des fonctions ou des déclencheurs.  
  
> [!NOTE]
>  Vous pouvez créer un certificat dans la base de données MASTER afin d'accorder des autorisations de niveau serveur.  
  
## <a name="creating-certificates"></a>Création de certificats  
 Lorsque vous signez une procédure stockée avec un certificat, un résumé des données contenant le hachage chiffré du code de la procédure stockée est créé à l'aide de la clé privée. Au moment de l'exécution, le résumé des données est chiffré avec la clé publique et comparée à la valeur de hachage de la procédure stockée. Toute modification de la procédure stockée invalide la valeur de hachage afin que la signature numérique ne corresponde plus. Cela permet d'éviter qu'une personne n'ayant pas accès à la clé privée puisse modifier le code de la procédure stockée. Par conséquent, vous devez signer de nouveau la procédure à chaque fois que vous la modifiez.  
  
 La signature d'un module est réalisée en quatre étapes :  
  
1.  Créez un certificat à l'aide de l'instruction Transact-SQL `CREATE CERTIFICATE [certificateName]`. Cette instruction possède plusieurs options permettant de définir une date de début et de fin, de même qu'un mot de passe. La date d'expiration par défaut est une année.  
  
2.  Créez un utilisateur de base de données associé à ce certificat à l'aide de l'instruction Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Cet utilisateur existe uniquement dans la base de données et n'est pas associé une connexion.  
  
3.  Accordez les autorisations requises sur les objets de la base de données à l'utilisateur du certificat.  
  
> [!NOTE]
>  Un certificat ne permet pas d'accorder des autorisations à un utilisateur dont les autorisations ont été révoquées à l'aide de l'instruction DENY. L'instruction DENY a toujours priorité sur l'instruction GRANT, ce qui empêche l'appelant d'hériter des autorisations accordées à l'utilisateur du certificat.  
  
1.  Signez la procédure avec le certificat en utilisant l'instruction Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.  
  
## <a name="external-resources"></a>Ressources externes  
 Pour plus d'informations, voir les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Signature de module](http://go.microsoft.com/fwlink/?LinkId=98590) dans la documentation en ligne de SQL Server|Décrit la signature de module, en fournissant un exemple de scénario et des liens vers les rubriques pertinentes relatives à Transact-SQL.|  
|[Les procédures stockées avec un certificat de signature](http://msdn.microsoft.com/library/bb283630.aspx) dans la documentation en ligne de SQL Server|Propose un didacticiel de signature d'une procédure stockée à l'aide d'un certificat.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Vue d’ensemble de la sécurité SQL Server](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [Scénarios de sécurité des applications dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Gestion des autorisations avec les procédures stockées dans SQL Server](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [Écriture de code SQL dynamique sécurisé dans SQL Server](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Modification des données avec les procédures stockées](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
