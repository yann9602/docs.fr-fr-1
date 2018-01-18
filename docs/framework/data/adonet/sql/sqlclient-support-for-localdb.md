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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a3d643ac386aebf51673f937b3f47e73c749b78f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="5dd62-102">Prise en charge de SqlClient pour LocalDB</span><span class="sxs-lookup"><span data-stu-id="5dd62-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="5dd62-103">À partir de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] nom de code Denali, une version légère de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], appelée LocalDB, sera disponible.</span><span class="sxs-lookup"><span data-stu-id="5dd62-103">Beginning in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] code name Denali, a lightweight version of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)], called LocalDB, will be available.</span></span> <span data-ttu-id="5dd62-104">Cette rubrique explique comment se connecter à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5dd62-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd62-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5dd62-105">Remarks</span></span>  
 <span data-ttu-id="5dd62-106">Pour plus d'informations sur LocalDB, y compris comment installer LocalDB et configurer votre instance de LocalDB, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5dd62-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="5dd62-107">Pour résumer les opérations possibles avec LocalDB :</span><span class="sxs-lookup"><span data-stu-id="5dd62-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="5dd62-108">Créez et démarrez les instances de LocalDB avec sqllocaldb.exe ou votre fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="5dd62-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="5dd62-109">Utilisez sqlcmd.exe pour ajouter et modifier des bases de données dans une instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5dd62-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="5dd62-110">Par exemple, `sqlcmd -S (localdb)\myinst`.</span><span class="sxs-lookup"><span data-stu-id="5dd62-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="5dd62-111">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour ajouter une base de données à votre instance de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5dd62-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="5dd62-112">Lorsque vous utilisez `AttachDBFilename`, si vous ne spécifiez pas le nom de la base de données avec le mot clé de chaîne de connexion `Database` , la base de données sera supprimée de l'instance de LocalDB lorsque l'application se ferme.</span><span class="sxs-lookup"><span data-stu-id="5dd62-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="5dd62-113">Spécifiez une instance de LocalDB dans votre chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="5dd62-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="5dd62-114">Par exemple, si le nom de l'instance est `myInstance`, la chaîne de connexion est la suivante :</span><span class="sxs-lookup"><span data-stu-id="5dd62-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="5dd62-115">Vous ne pouvez pas utiliser`User Instance=True` lors de la connexion à une base de données LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5dd62-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="5dd62-116">Vous pouvez télécharger LocalDB à partir de [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span><span class="sxs-lookup"><span data-stu-id="5dd62-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="5dd62-117">Si vous devez utiliser sqlcmd.exe pour modifier des données dans votre instance de LocalDB, vous aurez besoin de sqlcmd de [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, que vous pouvez également obtenir dans le [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.</span><span class="sxs-lookup"><span data-stu-id="5dd62-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012, which you can also get from the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="5dd62-118">Créer par programme une instance nommée</span><span class="sxs-lookup"><span data-stu-id="5dd62-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="5dd62-119">Une application peut créer une instance nommée et spécifier une base de données comme suit :</span><span class="sxs-lookup"><span data-stu-id="5dd62-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="5dd62-120">Spécifiez les instances de LocalDB à créer dans le fichier app.config, comme suit.</span><span class="sxs-lookup"><span data-stu-id="5dd62-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="5dd62-121">Le numéro de version de l'instance doit être le même que le numéro de version de votre installation de LocalDB.</span><span class="sxs-lookup"><span data-stu-id="5dd62-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
-   <span data-ttu-id="5dd62-122">Spécifiez le nom de l'instance à l'aide du mot clé de chaîne de connexion `server` .</span><span class="sxs-lookup"><span data-stu-id="5dd62-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="5dd62-123">Le nom d’instance spécifié dans le mot clé de chaîne de connexion `server` doit correspondre au nom spécifié dans le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="5dd62-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="5dd62-124">Utilisez le mot clé de chaîne de connexion `AttachDBFilename` pour spécifier le fichier .MDF.</span><span class="sxs-lookup"><span data-stu-id="5dd62-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd62-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dd62-125">See Also</span></span>  
 [<span data-ttu-id="5dd62-126">Fonctionnalités SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5dd62-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="5dd62-127">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="5dd62-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
