---
title: "Activités d'accès aux bases de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d95eece0a02433a78a400f1cfd9ab06ca716668e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="database-access-activities"></a>Activités d'accès aux bases de données
Les activités d'accès aux bases de données vous permettent d'accéder à une base de données dans un workflow. Ces activités permettent l’accès aux bases de données pour récupérer ou modifier les informations et l’utiliser [ADO.NET](http://go.microsoft.com/fwlink/?LinkId=166081) pour accéder à la base de données.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez-vous sur la page de téléchargement pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`  
  
## <a name="database-activities"></a>Activités de base de données  
 Les sections suivantes détaillent la liste des activités incluses dans cet exemple.  
  
## <a name="dbupdate"></a>DbUpdate  
 Exécute une requête SQL qui produit une modification dans la base de données (insertion, mise à jour, suppression et autres modifications).  
  
 Cette classe effectue son travail de façon asynchrone (elle dérive d'<xref:System.Activities.AsyncCodeActivity> et utilise ses fonctionnalités asynchrones).  
  
 Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.  
  
 La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.  
  
 Une fois `DbUpdate` exécuté, le nombre des enregistrements affectés est retourné dans la propriété `AffectedRecords`.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
|Argument|Description|  
|-|-|  
|ProviderName|Nom invariant du fournisseur ADO.NET. Si cet argument est défini, `ConnectionString` doit également être défini.|  
|ConnectionString|Chaîne de connexion utilisée pour se connecter à la base de données. Si cet argument est défini, `ProviderName` doit également être défini.|  
|ConfigName|Nom de la section du fichier de configuration où les informations de connexion sont stockées. Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.|  
|CommandType|Type du <xref:System.Data.Common.DbCommand> à exécuter.|  
|Sql|Commande SQL à exécuter.|  
|Paramètres|Collection des paramètres de la requête SQL.|  
|AffectedRecords|Nombre d'enregistrements affectés par la dernière opération.|  
  
## <a name="dbqueryscalar"></a>DbQueryScalar  
 Exécute une requête qui récupère une valeur unique à partir de la base de données.  
  
 Cette classe effectue son travail de façon asynchrone (elle dérive d'<xref:System.Activities.AsyncCodeActivity%601> et utilise ses fonctionnalités asynchrones).  
  
 Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.  
  
 La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.  
  
 Après avoir `DbQueryScalar` est exécuté, la valeur scalaire est retourné dans le `Result``out` argument (de type `TResult`, qui est défini dans la classe de base <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Argument|Description|  
|-|-|  
|ProviderName|Nom invariant du fournisseur ADO.NET. Si cet argument est défini, `ConnectionString` doit également être défini.|  
|ConnectionString|Chaîne de connexion utilisée pour se connecter à la base de données. Si cet argument est défini, `ProviderName` doit également être défini.|  
|ConfigName|Nom de la section du fichier de configuration où les informations de connexion sont stockées. Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.|  
|CommandType|Type du <xref:System.Data.Common.DbCommand> à exécuter.|  
|Sql|Commande SQL à exécuter.|  
|Paramètres|Collection des paramètres de la requête SQL.|  
|Résultat|Scalaire obtenu une fois la requête exécutée. Cet argument est de type `TResult`.|  
  
## <a name="dbquery"></a>DbQuery  
 Exécute une requête qui récupère une liste d'objets. Une fois que la requête est exécutée, une fonction de mappage est exécutée (il peut être <xref:System.Func%601> < `DbDataReader`, `TResult`> ou un <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>). Cette fonction de mappage obtient un enregistrement dans un `DbDataReader` et le mappe à l'objet à retourner.  
  
 Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.  
  
 La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.  
  
 Les résultats de la requête SQL sont récupérés à l'aide d'un `DbDataReader`. L'activité itère au sein de `DbDataReader` et mappe les lignes de `DbDataReader` à une instance de `TResult`. L’utilisateur de `DbQuery` doit fournir le code de mappage et cela peuvent être réalisées de deux façons : à l’aide un <xref:System.Func%601> < `DbDataReader`, `TResult`> ou un <xref:System.Activities.ActivityFunc%601> < `DbDataReader`, `TResult`>. Dans le premier cas, le mappage est effectué en une seule impulsion d'exécution. Par conséquent, il est plus rapide, mais ne peut pas être sérialisé en XAML. Dans le dernier cas, le mappage est effectué en plusieurs impulsions. Par conséquent, il peut être plus lent mais peut être sérialisé en XAML et créé de façon déclarative (toute activité existante peut participer au mappage).  
  
```  
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [OverloadGroup("DirectMapping")]  
    [DefaultValue(null)]  
    public Func<DbDataReader, TResult> Mapper { get; set; }  
  
    [OverloadGroup("MultiplePulseMapping")]  
    [DefaultValue(null)]  
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }  
}  
```  
  
|Argument|Description|  
|-|-|  
|ProviderName|Nom invariant du fournisseur ADO.NET. Si cet argument est défini, `ConnectionString` doit également être défini.|  
|ConnectionString|Chaîne de connexion utilisée pour se connecter à la base de données. Si cet argument est défini, `ProviderName` doit également être défini.|  
|ConfigName|Nom de la section du fichier de configuration où les informations de connexion sont stockées. Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.|  
|CommandType|Type du <xref:System.Data.Common.DbCommand> à exécuter.|  
|Sql|Commande SQL à exécuter.|  
|Paramètres|Collection des paramètres de la requête SQL.|  
|Mapper|Fonction de mappage (<xref:System.Func%601><`DbDataReader`, `TResult`>) qui prend un enregistrement dans le `DataReader` obtenu en résultat de l’exécution de la requête et retourne une instance d’un objet de type `TResult` à ajouter à la `Result` collection.<br /><br /> Dans ce cas, le mappage est effectué en seule impulsion d'exécution, mais il ne peut pas être créé de façon déclarative à l'aide du concepteur.|  
|MapperFunc|Fonction de mappage (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) qui prend un enregistrement dans le `DataReader` obtenu en résultat de l’exécution de la requête et retourne une instance d’un objet de type `TResult` à ajouter à la `Result` collection.<br /><br /> Dans ce cas, le mappage est effectué en plusieurs impulsions d'exécution. Cette fonction peut être sérialisée en XAML et créée de façon déclarative (toute activité existante peut participer au mappage).|  
|Résultat|Liste des objets obtenus en résultat de l'exécution de la requête et de l'exécution de la fonction de mappage pour chaque d'enregistrement de `DataReader`.|  
  
## <a name="dbquerydataset"></a>DbQueryDataSet  
 Exécute une requête qui retourne un <xref:System.Data.DataSet>. Cette classe effectue son travail de façon asynchrone. Elle est dérivée de <xref:System.Activities.AsyncCodeActivity> < `TResult`> et utilise ses fonctionnalités asynchrones.  
  
 Les informations de connexion peuvent être configurées en définissant un nom invariant de fournisseur (`ProviderName`) et la chaîne de connexion (`ConnectionString`), ou simplement à l'aide d'un nom de configuration de chaîne de connexion (`ConfigFileSectionName`) provenant du fichier de configuration de l'application.  
  
 La requête à exécuter est configurée dans sa propriété `Sql` et les paramètres sont passés via la collection `Parameters`.  
  
 Après le `DbQueryDataSet` est exécutée la `DataSet` est retourné dans le `Result``out` argument (de type `TResult`, qui est défini dans la classe de base <xref:System.Activities.AsyncCodeActivity%601>).  
  
```  
public class DbQueryDataSet : AsyncCodeActivity<DataSet>  
{  
    // public arguments  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
}  
```  
  
|Argument|Description|  
|-|-|  
|ProviderName|Nom invariant du fournisseur ADO.NET. Si cet argument est défini, `ConnectionString` doit également être défini.|  
|ConnectionString|Chaîne de connexion utilisée pour se connecter à la base de données. Si cet argument est défini, `ProviderName` doit également être défini.|  
|ConfigName|Nom de la section du fichier de configuration où les informations de connexion sont stockées. Lorsque cet argument est défini, `ProviderName` et `ConnectionString` ne sont pas requis.|  
|CommandType|Type du <xref:System.Data.Common.DbCommand> à exécuter.|  
|Sql|Commande SQL à exécuter.|  
|Paramètres|Collection des paramètres de la requête SQL.|  
|Résultat|<xref:System.Data.DataSet> obtenu une fois la requête exécutée.|  
  
## <a name="configuring-connection-information"></a>Configuration des informations de connexion  
 Tous les DbActivities partagent les mêmes paramètres de configuration. Ils peuvent être configurés de deux façons :  
  
-   `ConnectionString + InvariantName` : définit le nom invariant du fournisseur ADO.NET et la chaîne de connexion.  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<DateTime>()  
    {  
        ProviderName = "System.Data.SqlClient",  
        ConnectionString = @"Data Source=.\SQLExpress;  
                             Initial Catalog=DbActivitiesSample;  
                             Integrated Security=True",  
        Sql = "SELECT GetDate()"  
    };  
    ```  
  
-   `ConfigName` : définit le nom de la section de configuration qui contient les informations de connexion.  
  
    ```xml  
    <connectionStrings>      
        <add name="DbActivitiesSample"  
             providerName="System.Data.SqlClient"  
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>  
      </connectionStrings>  
    ```  
  
-   Dans l'activité :  
  
    ```  
    Activity dbSelectCount = new DbQueryScalar<int>()  
    {                  
        ConfigName = "DbActivitiesSample",  
        Sql = "SELECT COUNT(*) FROM Roles"  
    };  
    ```  
  
## <a name="running-this-sample"></a>Exécution de cet exemple  
  
### <a name="setup-instructions"></a>Instructions de configuration  
 Cet exemple utilise une base de données. Un script d'installation et de chargement (Setup.cmd) est fourni avec l'exemple. Vous devez exécuter ce fichier à l'aide de l'invite de commandes.  
  
 Le script Setup.cmd appelle le fichier de script CreateDb.sql, lequel contient des commandes SQL qui effectuent les opérations suivantes :  
  
-   Crée une base de données appelée DbActivitiesSample.  
  
-   Crée la table Roles.  
  
-   Crée la table Employees.  
  
-   Insère trois enregistrements dans la table Roles.  
  
-   Insère douze enregistrements dans la table Employees.  
  
##### <a name="to-run-setupcmd"></a>Pour exécuter Setup.cmd  
  
1.  Ouvrez une invite de commandes.  
  
2.  Accédez au dossier d’exemples DbActivities.  
  
3.  Tapez « setup.cmd » et appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  Setup.cmd tente d'installer l'exemple dans l'instance SqlExpress de votre ordinateur local. Si vous voulez l'installer dans une autre instance SQL Server, modifiez Setup.cmd avec le nom de la nouvelle instance.  
  
##### <a name="to-uninstall-the-sample-database"></a>Pour désinstaller l'exemple de base de données  
  
1.  Exécutez le fichier Cleanup.cmd du dossier d'exemples dans une invite de commandes.  
  
##### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pour compiler la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter l'exemple sans débogage, appuyez sur CTRL+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
