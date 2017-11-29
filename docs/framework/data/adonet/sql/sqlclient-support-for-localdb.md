---
title: Prise en charge de SqlClient pour LocalDB
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: abe9487f9c2ebbb93c2e712959237f722ee707b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlclient-support-for-localdb"></a>Prise en charge de SqlClient pour LocalDB
À partir de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nom de code Denali, une version légère de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], appelée LocalDB, sera disponible. Cette rubrique explique comment se connecter à une base de données LocalDB.  
  
## <a name="remarks"></a>Notes  
 Pour plus d'informations sur LocalDB, y compris comment installer LocalDB et configurer votre instance de LocalDB, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] .  
  
 Pour résumer les opérations possibles avec LocalDB :  
  
-   Créez et démarrez les instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.  
  
-   Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance de LocalDB. Par exemple, `sqlcmd -S (localdb)\myinst`.  
  
-   Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance de LocalDB. Lorsque vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database` , la base de données sera supprimée de l'instance de LocalDB lorsque l'application se ferme.  
  
-   Spécifiez une instance de LocalDB dans votre chaîne de connexion. Par exemple, si le nom de l'instance est `myInstance`, la chaîne de connexion est la suivante :  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 Vous ne pouvez pas utiliser`User Instance=True` lors de la connexion à une base de données LocalDB.  
  
 Vous pouvez télécharger LocalDB à partir de [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Si vous devez utiliser sqlcmd.exe pour modifier des données dans votre instance de LocalDB, vous aurez besoin de sqlcmd de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, que vous pouvez également obtenir dans le [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Créer par programme une instance nommée  
 Une application peut créer une instance nommée et spécifier une base de données comme suit :  
  
-   Spécifiez les instances de LocalDB à créer dans le fichier app.config, comme suit.  Le numéro de version de l'instance doit être le même que le numéro de version de votre installation de LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   Spécifiez le nom de l'instance à l'aide du mot clé de chaîne de connexion `server` .  Le nom d’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.  
  
-   Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
