---
title: BFILE Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e7b7d438abb5a7e14a55f30447d291d3c8ee286
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-bfiles"></a><span data-ttu-id="da59e-102">BFILE Oracle</span><span class="sxs-lookup"><span data-stu-id="da59e-102">Oracle BFILEs</span></span>
<span data-ttu-id="da59e-103">Le fournisseur de données .NET Framework pour Oracle inclut la classe <xref:System.Data.OracleClient.OracleBFile> qui est utilisée pour opérer avec le type de données <xref:System.Data.OracleClient.OracleType.BFile> Oracle.</span><span class="sxs-lookup"><span data-stu-id="da59e-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle <xref:System.Data.OracleClient.OracleType.BFile> data type.</span></span>  
  
 <span data-ttu-id="da59e-104">Oracle **BFILE** type de données est Oracle **LOB** type de données qui contient une référence à des données binaires d’une taille maximale de 4 giga-octets.</span><span class="sxs-lookup"><span data-stu-id="da59e-104">The Oracle **BFILE** data type is an Oracle **LOB** data type that contains a reference to binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="da59e-105">Oracle **BFILE** Oracle diffère d’autres **LOB** les types de données par ses données stockées dans un fichier physique dans le système d’exploitation au lieu de sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="da59e-105">An Oracle **BFILE** differs from other Oracle **LOB** data types in that its data is stored in a physical file in the operating system instead of on the server.</span></span> <span data-ttu-id="da59e-106">Notez que la **BFILE** type de données fournit un accès en lecture seule aux données.</span><span class="sxs-lookup"><span data-stu-id="da59e-106">Note that the **BFILE** data type provides read-only access to data.</span></span>  
  
 <span data-ttu-id="da59e-107">Autres caractéristiques d’un **BFILE** type de données qui le distinguent un **LOB** type de données :</span><span class="sxs-lookup"><span data-stu-id="da59e-107">Other characteristics of a **BFILE** data type that distinguish it from a **LOB** data type are that it:</span></span>  
  
-   <span data-ttu-id="da59e-108">Il contient des données non structurées.</span><span class="sxs-lookup"><span data-stu-id="da59e-108">Contains unstructured data.</span></span>  
  
-   <span data-ttu-id="da59e-109">Il prend en charge la fragmentation côté serveur.</span><span class="sxs-lookup"><span data-stu-id="da59e-109">Supports server-side chunking.</span></span>  
  
-   <span data-ttu-id="da59e-110">Il utilise une sémantique de copie de référence.</span><span class="sxs-lookup"><span data-stu-id="da59e-110">Uses reference copy semantics.</span></span> <span data-ttu-id="da59e-111">Par exemple, si vous effectuez une opération de copie sur un **BFILE**, seule la **BFILE** (qui est une référence au fichier) est copiée.</span><span class="sxs-lookup"><span data-stu-id="da59e-111">For example, if you perform a copy operation on a **BFILE**, only the **BFILE** locator (which is a reference to the file) is copied.</span></span> <span data-ttu-id="da59e-112">Les données du fichier ne sont pas copiées.</span><span class="sxs-lookup"><span data-stu-id="da59e-112">The data in the file is not copied.</span></span>  
  
 <span data-ttu-id="da59e-113">Le **BFILE** type de données doit être utilisé pour référencer les LOB de grande taille et par conséquent, pas pratique de stocker dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="da59e-113">The **BFILE** data type should be used for referencing LOBs that are large in size, and therefore, not practical to store in the database.</span></span> <span data-ttu-id="da59e-114">Davantage de surcharge client, serveur et de communication intervient lorsque vous utilisez un **BFILE** type de données par rapport à la **LOB** type de données.</span><span class="sxs-lookup"><span data-stu-id="da59e-114">More client, server, and communication overhead is involved when using a **BFILE** data type compared with the **LOB** data type.</span></span> <span data-ttu-id="da59e-115">Il est plus efficace d’accéder à un **BFILE** si vous devez uniquement obtenir une petite quantité de données.</span><span class="sxs-lookup"><span data-stu-id="da59e-115">It is more efficient to access a **BFILE** if you only need to obtain a small amount of data.</span></span> <span data-ttu-id="da59e-116">Il est plus efficace d'accéder à des LOB résidant en mémoire si vous avez besoin d'obtenir l'objet entier.</span><span class="sxs-lookup"><span data-stu-id="da59e-116">It is more efficient to access database-resident LOBs if you need to obtain the entire object.</span></span>  
  
 <span data-ttu-id="da59e-117">Chaque valeur non NULL **OracleBFile** objet est associé à deux entités qui définissent l’emplacement du fichier physique sous-jacent :</span><span class="sxs-lookup"><span data-stu-id="da59e-117">Each non-NULL **OracleBFile** object is associated with two entities that define the location of the underlying physical file:</span></span>  
  
1.  <span data-ttu-id="da59e-118">Un objet DIRECTORY Oracle, qui est un alias de base de données pour un répertoire du système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="da59e-118">An Oracle DIRECTORY object, which is a database alias for a directory in the file system, and</span></span>  
  
2.  <span data-ttu-id="da59e-119">Le nom du fichier physique sous-jacent, qui se trouve dans le répertoire associé à l'objet DIRECTORY.</span><span class="sxs-lookup"><span data-stu-id="da59e-119">The file name of the underlying physical file, which is located in the directory associated with the DIRECTORY object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da59e-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="da59e-120">Example</span></span>  
 <span data-ttu-id="da59e-121">L’exemple c# suivant montre comment vous pouvez créer un **BFILE** dans une table Oracle, puis l’extraire sous la forme d’un **OracleBFile** objet.</span><span class="sxs-lookup"><span data-stu-id="da59e-121">The following C# example demonstrates how you can create a **BFILE** in an Oracle table and then retrieve it in the form of an **OracleBFile** object.</span></span> <span data-ttu-id="da59e-122">L’exemple montre comment utiliser le <xref:System.Data.OracleClient.OracleDataReader> objet et la **OracleBFile** **recherche** et **en lecture** méthodes.</span><span class="sxs-lookup"><span data-stu-id="da59e-122">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleBFile** **Seek** and **Read** methods.</span></span> <span data-ttu-id="da59e-123">Notez que pour utiliser cet exemple, vous devez d’abord créer un répertoire nommé « c:\\\bfiles » et un fichier nommé « MyFile.jpg » sur le serveur Oracle.</span><span class="sxs-lookup"><span data-stu-id="da59e-123">Note that in order to use this sample, you must first create a directory named "c:\\\bfiles" and file named "MyFile.jpg" on the Oracle server.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="da59e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da59e-124">See Also</span></span>  
 [<span data-ttu-id="da59e-125">Oracle et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="da59e-125">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="da59e-126">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="da59e-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
